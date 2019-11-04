---
title: Ověřovací data tokenu
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 835a158ba668a3aef749602c73fd9157e8d83a40
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425035"
---
# <a name="token-authenticator"></a>Ověřovací data tokenu
Tato ukázka předvádí, jak implementovat vlastní ověřovací data tokenu. Ověřovací data tokenu v Windows Communication Foundation (WCF) se používají k ověření tokenu, který se používá ve zprávě, ověření, že je samostatný, a ověření identity přidružené k tokenu.

 Vlastní ověřovatele tokenů jsou užitečné v nejrůznějších případech, například:

- Pokud chcete přepsat výchozí mechanismus ověřování, který je přidružený k tokenu.

- Při vytváření vlastního tokenu.

 Tato ukázka demonstruje následující:

- Jak se může klient ověřit pomocí dvojice uživatelského jména a hesla.

- Jak může server ověřit přihlašovací údaje klienta pomocí vlastního ověřovatele tokenu.

- Způsob, jakým se kód služby WCF přiřazuje k vlastnímu ověřovateli tokenu.

- Jak se dá server ověřit pomocí certifikátu X. 509 serveru.

 Tato ukázka také ukazuje, jak je identita volajícího přístupná z WCF po procesu ověřování pomocí vlastního tokenu.

 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována se standardním `wsHttpBinding`, s režimem zabezpečení nastaveným na Message – výchozí režim `wsHttpBinding`. Tato ukázka nastaví standardní `wsHttpBinding` pro použití ověřování uživatelského jména klienta. Služba také nakonfiguruje certifikát služby pomocí chování `serviceCredentials`. Chování `securityCredentials` umožňuje zadat certifikát služby. Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv. Následující konfigurace odkazuje na certifikát localhost nainstalovaný během ukázkové instalace, jak je popsáno v následujících pokynech k instalaci.

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

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurovaná s příslušnými `Mode` a `clientCredentialType`.

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

 Implementace klienta nastaví uživatelské jméno a heslo, které se má použít.

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a>Vlastní ověřovací data tokenu
 Pomocí následujících kroků můžete vytvořit vlastní ověřovací data tokenu:

1. Zapište vlastní ověřovací data tokenu.

     Ukázka implementuje vlastní ověřovací data tokenu, které ověřuje, že uživatelské jméno má platný formát e-mailu. Odvozuje <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Nejdůležitější metoda v této třídě je <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. V této metodě ověřovatel ověří formát uživatelského jména a také, že název hostitele není z neoprávněné domény. Pokud jsou splněny obě podmínky, vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí jen pro čtení, která se pak použije k poskytnutí deklarací, které představují informace uložené v tokenu uživatelského jména.

    ```csharp
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

2. Zadejte zásady autorizace, které vrací vlastní ověřovatel tokenu.

     Tato ukázka poskytuje vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> s názvem `UnconditionalPolicy`, která vrací sadu deklarací identity a identit, které byly předány do svého konstruktoru.

    ```csharp
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

3. Napište vlastního správce tokenů zabezpečení.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou předány do této metody `CreateSecurityTokenAuthenticator`. Správce tokenů zabezpečení se používá také k vytváření zprostředkovatelů tokenů a serializátorů tokenů, ale u těch se tato ukázka nezabývá. V této ukázce správce vlastního tokenu zabezpečení dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepíše metodu `CreateSecurityTokenAuthenticator`, aby vracela vlastní ověřovací data tokenu uživatelského jména, když požadavky na předané tokeny označují, že se požaduje ověřovací data uživatelského jména.

    ```csharp
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

4. Napište vlastní přihlašovací údaje služby.

     Třída pověření služby se používá k reprezentaci přihlašovacích údajů nakonfigurovaných pro službu a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátorů tokenů.

    ```csharp
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

5. Nakonfigurujte službu tak, aby používala vlastní přihlašovací údaje služby.

     Aby služba používala vlastní přihlašovací údaje služby, odstraníme po zachycení certifikátu služby, který je už předem nakonfigurovaný v přihlašovacích údajích služby, výchozí třídu přihlašovacích údajů služby a nakonfigurujete nové přihlašovací údaje služby. instance pro použití předkonfigurovaných certifikátů služby a přidání této nové instance pověření služby k chování služby.

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 Chcete-li zobrazit informace o volajícím, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, jak je znázorněno v následujícím kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> obsahuje informace o deklaracích aktuálního volajícího.

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.

- Vytváří se certifikát serveru.

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná `%SERVER_NAME%` Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota v tomto dávkovém souboru je localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Instalační dávkový soubor je navržený tak, aby se spouštěl z příkazového řádku Windows SDK. Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována. Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 otevřené s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.  
  
2. Spustit Service. exe z service\bin.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář v počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na počítači služby. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor App. config aplikace služby musí být aktualizován, aby odrážel tento nový název certifikátu. Můžete ji vytvořit pomocí souboru Setup. bat, pokud nastavíte `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, na kterém bude služba spuštěna. Všimněte si, že soubor Setup. bat musí být spuštěný z Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta. Nemusíte to dělat, s výjimkou případů, kdy je certifikát serveru vydán důvěryhodným vystavitelem klienta.  
  
5. V souboru App. config na počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.  
  
6. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
7. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. V klientském počítači spusťte z příkazového řádku soubor Client. exe.  
  
10. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
