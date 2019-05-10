---
title: Ověřovací data tokenu
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: fecb9197409f2e486288d40b80ce1abbbbb78fe2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593488"
---
# <a name="token-authenticator"></a>Ověřovací data tokenu
Tento příklad ukazuje, jak implementovat vlastní ověřovací data tokenu. Ve Windows Communication Foundation (WCF) ověřovací data tokenu se používá k ověření tokenu používaného se zprávou, ověření, že je konzistentní a ověření identity přidružené k tokenu.

 Vlastní ověřovací data tokenu jsou užitečné v mnoha případech, jako je například:

- Pokud chcete přepsat výchozí mechanismus ověřování přidružené k tokenu.

- Pokud vytváříte vlastní token.

 Tato ukázka demonstruje následující:

- Jak klient může ověřit pomocí dvojice uživatelského jména a hesla.

- Jak na serveru můžete ověřit přihlašovací údaje klienta pomocí vlastní ověřovací data tokenu.

- Jak kód služby WCF spojují se pomocí vlastní ověřovací data tokenu.

- Jak na serveru je možné ověřit pomocí certifikátu X.509 serveru.

 Tento příklad také ukazuje, jak identitu volajícího, jež je přístupný z WCF po dokončení procesu vlastních tokenů ověřování.

 Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní `wsHttpBinding`, s režimem zabezpečení nastavit ke zprávě – výchozí režim `wsHttpBinding`. Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů. Služba také nakonfiguruje pomocí certifikátu služby `serviceCredentials` chování. `securityCredentials` Chování umožňuje určit certifikát služby. Certifikát služby se používá pro klienta k ověření služby a zajistit ochranu zprávy. Následující konfigurace odkazuje nainstalovat během instalace ukázka, jak je popsáno v následující pokyny k instalaci certifikátu localhost.

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt. Klient vazby je nakonfigurovaný s příslušnou `Mode` a `clientCredentialType`.

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 Implementace klienta nastaví uživatelské jméno a heslo pro použití.

```
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a>Vlastní ověřovací data tokenu
 Použijte následující postup k vytvoření vlastního ověřovacího modulu tokenu:

1. Napište vlastní ověřovací data tokenu.

     Ukázka implementuje vlastní ověřovací data tokenu, který ověřuje, že uživatelské jméno je ve formátu platné e-mailu. Se odvozuje <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Metoda nejdůležitější v této třídě <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. V této metodě ověřovacích ověří formát uživatelského jména a také, že název hostitele není kompatibilní se z podvodného domény. Pokud jsou splněny obě podmínky a pak vrátí kolekci jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které se pak použije k poskytovat deklarace identity, které představují informací uložených uvnitř tokenu uživatelské jméno.

    ```
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. Zadejte zásadu autorizace, který je vrácen vlastní ověřovací data tokenu.

     Tato ukázka poskytuje vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> volá `UnconditionalPolicy` , která vrací sadu deklarací identity a identity, které bylo předáno 've svém konstruktoru.

    ```
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. Správce tokenů zabezpečení vlastního zápisu.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou do ní předán v `CreateSecurityTokenAuthenticator` metody. Správce tokenů zabezpečení se také používá k vytvoření poskytovatele tokenů a serializátorů tokenu, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenAuthenticator` požadovaná metoda vrátí uživatelské jméno vlastní ověřovací data tokenu při úspěšné požadavky tokenu označení authenticator tohoto uživatelského jména.

    ```
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. Zápis přihlašovacích údajů pro vlastní služby.

     Třída přihlašovací údaje služby se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro službu a vytvoří Správce tokenů, který se používá k získání ověřovací data tokenu, poskytovatele tokenů a serializátorů tokenu zabezpečení.

    ```
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. Nakonfigurujte službu, aby pomocí přihlašovacích údajů pro vlastní služby.

     V pořadí pro službu, aby používala vlastní službu přihlašovacích údajů jsme odstranit výchozí třídu přihlašovacích údajů služby po zachycení, který už je předem nakonfigurovaný v přihlašovacích údajích služby výchozí certifikát služby a konfiguraci nových přihlašovacích údajů služby instance používat certifikáty předem nakonfigurované služby a přidejte tato nová pověření instance služby do chování služby.

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 Chcete-li zobrazit informace volajícího, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícím.

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje server zabezpečení na základě certifikátů. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.

 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.

- Vytváří se certifikát serveru.

     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnné Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tomto souboru batch výchozí hodnota je localhost.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.

     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Instalační dávkový soubor je navržena pro spouštění na příkazovém řádku sady SDK Windows. To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.

#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku

1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1. Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio 2012 otevřeného s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.  
  
2. Spusťte service.exe z service\bin.  
  
3. Spusťte client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1. Vytvoření adresáře na počítači se službou pro binární soubory služby.  
  
2. Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor App.config služby musí být aktualizovány tak, aby odrážely tento nový název certifikátu. Můžete vytvořit pomocí Setup.bat, pokud jste nastavili `%SERVER_NAME%` proměnných hostitele plně kvalifikovaný název počítače, na kterém je spuštěna služba. Všimněte si, že se soubor setup.bat musí spustit na příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Nemusíte to dělat s výjimkou případů, kdy certifikátu serveru vydanému klienta důvěryhodného vystavitele.  
  
5. V souboru App.config na počítači se službou změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný, místo localhost.  
  
6. Na počítači se službou spusťte z příkazového řádku service.exe.  
  
7. Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. Na klientském počítači spusťte Client.exe z příkazového řádku.  
  
10. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1. Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
