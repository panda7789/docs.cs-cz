---
title: Zprostředkovatel tokenu
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d513ddd41d87da7274f961969d261724b49aab65
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807811"
---
# <a name="token-provider"></a>Zprostředkovatel tokenu
Tento příklad znázorňuje způsob implementace vlastního zprostředkovatele tokenu. Zprostředkovatel tokenu ve Windows Communication Foundation (WCF) se používá pro zadávání přihlašovacích údajů k zabezpečení infrastruktury. Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy. WCF se dodává s výchozí zprostředkovatel tokenu správce přihlašovacích údajů. Dodává se také s WCF [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu. Vlastní poskytovatele tokenů jsou užitečné v následujících případech:  
  
-   Pokud máte úložiště přihlašovacích údajů, která tyto poskytovatele tokenů nemůže pracovat s.  
  
-   Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel poskytuje podrobnosti pro případ použití rozhraní klienta WCF přihlašovací údaje.  
  
-   Pokud vytváříte vlastní token.  
  
 Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatele tokenů, který transformuje vstup od uživatele do jiného formátu.  
  
 Tento příklad znázorňuje to Shrneme, následující:  
  
-   Jak klienta můžete ověřit pomocí pár uživatelského jména a hesla.  
  
-   Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.  
  
-   Jak server můžete ověřit pomocí vlastní heslo pověření klienta <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , ověří, zda se shodují uživatelské jméno a heslo.  
  
-   Jak server ověření klienta pomocí certifikátu X.509 serveru.  
  
 Tento příklad také ukazuje, jak identitu volajícího je dostupné po dokončení procesu vlastních tokenů ověřování.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standardní `wsHttpBinding`, který používá zabezpečení zpráv ve výchozím nastavení. Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů. Služba nakonfiguruje taky certifikát služby pomocí – serviceCredentials chování. Chování – serviceCredentials umožňuje nakonfigurovat certifikát služby. Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy. Následující konfigurace odkazuje localhost certifikát nainstalovat během instalace ukázka, jak je popsáno v následujících pokynů pro instalaci.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>  
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
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient vazba je konfigurován s odpovídající `Mode` a zpráva `clientCredentialType`.  
  
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
  
 Následující kroky ukazují, jak vyvíjet vlastní zprostředkovatele tokenu a integrovat do rozhraní zabezpečení WCF:  
  
1.  Napište vlastního zprostředkovatele tokenu.  
  
     Ukázka implementuje vlastního zprostředkovatele tokenu, který získá uživatelské jméno a heslo. Heslo se musí shodovat toto uživatelské jméno. Tento vlastní zprostředkovatel tokenu je pouze pro demonstrační účely a nedoporučuje se používat pro reálné nasazení.  
  
     K provedení této úlohy, poběží vlastní zprostředkovatel tokenu odvozuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda. Tato metoda vytvoří a vrátí novou `UserNameSecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
        // obtain username and password from the user using console window  
        string username = GetUserName();  
        string password = GetPassword();  
        Console.WriteLine("username: {0}", username);  
  
        // return new UserNameSecurityToken containing information obtained from user  
        return new UserNameSecurityToken(username, password);  
    }  
    ```  
  
2.  Zápis tokenu správce vlastní zabezpečení.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda. Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátor, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` metoda vrátí zprostředkovatele tokenu vlastní uživatelské jméno v případě předaný tokenu požadavky znamenat tohoto zprostředkovatele uživatelské jméno je požadovaná.  
  
    ```  
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        MyUserNameClientCredentials myUserNameClientCredentials;  
  
        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)  
            : base(myUserNameClientCredentials)  
        {  
            this.myUserNameClientCredentials = myUserNameClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // if token requirement matches username token return custom username token provider  
            // otherwise use base implementation  
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)  
            {  
                return new MyUserNameTokenProvider();  
            }  
            else  
            {  
                return base.CreateSecurityTokenProvider(tokenRequirement);  
            }  
        }  
    }  
    ```  
  
3.  Zápis vlastních klientských pověření.  
  
     Třída pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy server klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátoru tokenů zabezpečení.  
  
    ```  
    public class MyUserNameClientCredentials : ClientCredentials  
    {  
        public MyUserNameClientCredentials()  
            : base()  
        {  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new MyUserNameClientCredentials();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            // return custom security token manager  
            return new MyUserNameSecurityTokenManager(this);  
        }  
    }  
    ```  
  
4.  Konfigurace klienta pro použití vlastního klienta přihlašovací údaje.  
  
     Aby klientovi použít přihlašovací údaje vlastního klienta vzorek odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta.  
  
    ```  
    static void Main()  
    {  
        // ...  
           // Create a client with given client endpoint configuration  
          CalculatorClient client = new CalculatorClient();  
  
          // set new credentials  
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());  
       // ...  
    }  
    ```  
  
 Na službu, použijte pro zobrazení informací volajícího, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím příkladu kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícího.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat součástí této ukázky můžete nakonfigurovat server se příslušný certifikát spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci:  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota v tomto souboru batch je localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  Dávkový soubor Setup.bat slouží ke spuštění z Windows příkazový řádek SDK. Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Na řádku uživatelské jméno zadejte uživatelské jméno.  
  
5.  Heslo řádku použijte stejný řetězec, který byl zadán pro výzvu uživatelské jméno.  
  
6.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou pro binární soubory služby.  
  
2.  Zkopírujte soubory programu služby do adresáře služby na počítači se službou. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor Service.exe.config musí být aktualizovány tak, aby odrážela tento nový název certifikátu. Certifikát serveru můžete vytvořit úpravou Setup.bat dávkového souboru. Všimněte si, že soubor setup.bat musí spouštět z příkazového řádku Visual Studia, otevřít s oprávněními správce. Je nutné nastavit `%SERVER_NAME%` proměnnou hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Není nutné k tomu, pokud je certifikát serveru vydána klienta důvěryhodného vystavitele.  
  
5.  V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.  
  
6.  Na počítači se službou spusťte z příkazového řádku service.exe.  
  
7.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.  
  
10. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
## <a name="see-also"></a>Viz také
