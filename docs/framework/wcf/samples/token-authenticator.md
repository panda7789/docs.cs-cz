---
title: "Ověřovací data tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76f3913f5cf6166793cb6f95ef3658c24e2453b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="token-authenticator"></a>Ověřovací data tokenu
Tento příklad ukazuje, jak implementovat vlastní ověřovací data tokenu. Ověřovací data tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k ověřování použít se zprávou, že je konzistentní a ověřování identity přidružené k tokenu ověření tokenu.  
  
 Vlastní ověřovací data tokenu, jako jsou užitečné v mnoha případech:  
  
-   Pokud chcete přepsat výchozí mechanismus ověřování přidružené k tokenu.  
  
-   Když vytváříte vlastní token.  
  
 Tento příklad znázorňuje následující:  
  
-   Jak klienta můžete ověřit pomocí pár uživatelského jména a hesla.  
  
-   Jak server můžete ověřit pomocí vlastního ověřovacího modulu tokenu pověření klienta.  
  
-   Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kódu služby sváže pomocí vlastního ověřovacího modulu tokenu.  
  
-   Jak server lze ověřit pomocí certifikátu X.509 serveru.  
  
 Tento příklad také ukazuje, jak je přístupná ze identitu volajícího [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] po dokončení procesu vlastních tokenů ověřování.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standard `wsHttpBinding`, s režimem zabezpečení nastavena na zprávy - výchozí režim `wsHttpBinding`. Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů. Služba nakonfiguruje taky certifikát služby pomocí `serviceCredentials` chování. `securityCredentials` Chování umožňuje určit certifikát služby. Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy. Následující konfigurace odkazuje localhost certifikát nainstalovat během instalace ukázka, jak je popsáno v následujících pokynů pro instalaci.  
  
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
  
 Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient vazba je konfigurován s odpovídající `Mode` a `clientCredentialType`.  
  
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
  
 Implementace klienta nastaví uživatelské jméno a heslo.  
  
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
  
1.  Zápis vlastního ověřovacího modulu tokenu.  
  
     Ukázka implementuje vlastní ověřovací token, která ověřuje, že je uživatelské jméno ve formátu platné e-mailu. Je odvozen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Je nejdůležitější metoda v této třídě <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. Tato metoda ověří ověřovacích formát uživatelského jména a také, že název hostitele není z podvodného domény. Pokud jsou splněny obě podmínky, pak vrátí kolekci jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které se pak použije k poskytovat deklarace identity, které představují informace uložené uvnitř tokenu uživatelské jméno.  
  
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
  
2.  Zadejte zásad autorizace, který je vrácen vlastní ověřovací data tokenu.  
  
     Tato ukázka poskytuje svou vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> názvem `UnconditionalPolicy` , který vrací sadu deklarací identity a identity, které bylo předáno v jeho konstruktoru.  
  
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
  
3.  Zápis tokenu správce vlastní zabezpečení.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou do ní předán v `CreateSecurityTokenAuthenticator` metoda. Správce tokenu zabezpečení se také používá k vytvoření poskytovatele tokenů a serializátorů tokenu, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenAuthenticator` metoda vrátí ověřovací data tokenu vlastní uživatelské jméno v případě předaný tokenu požadavky znamenat, že ověřovací uživatelské jméno je požadovaná.  
  
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
  
4.  Přihlašovací údaje vlastní služby zápisu.  
  
     Třída přihlašovací údaje služby se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro službu a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátorů tokenu zabezpečení.  
  
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
  
5.  Nakonfigurujte službu, která používá přihlašovací údaje vlastní služby.  
  
     V pořadí pro službu, která používá přihlašovací údaje vlastní služby jsme odstranit výchozí třídu přihlašovacích údajů služby po zaznamenání službu certifikát, který je už předem nakonfigurované výchozí pověření služby a konfiguraci nových přihlašovacích údajů služby instance použít certifikáty předem nakonfigurované služby a přidejte tuto novou instanci služby přihlašovacích údajů do chování služby.  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 Chcete-li zobrazit informace volajícího, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícího.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje server zabezpečení na základě certifikátů. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci.  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tento dávkový soubor výchozí hodnota je localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Instalační program dávkový soubor slouží ke spuštění z Windows příkazový řádek SDK. Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte service.exe z service\bin.  
  
3.  Spusťte client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou pro binární soubory služby.  
  
2.  Zkopírujte soubory programu služby do adresáře služby na počítači se službou. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor App.config služby musí být aktualizovány tak, aby odrážela tento nový název certifikátu. Můžete ji vytvořit pomocí Setup.bat, pokud jste nastavili `%SERVER_NAME%` proměnnou hostitele plně kvalifikovaný název počítače, na kterém je spuštěna služba. Všimněte si, že soubor setup.bat musí spouštět z příkazového řádku Visual Studia, otevřít s oprávněními správce.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Není nutné k tomu kromě při vydání klienta důvěryhodného vystavitele certifikátu serveru.  
  
5.  V souboru App.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.  
  
6.  Na počítači se službou spusťte z příkazového řádku service.exe.  
  
7.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. Na klientském počítači spusťte z příkazového řádku Client.exe.  
  
10. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
## <a name="see-also"></a>Viz také
