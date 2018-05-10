---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 3744afb20c06e1ca85b91dadde6549d87ac89337
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="authorization-policy"></a>Zásada autorizace
Tato ukázka ukazuje, jak implementovat zásady autorizace vlastních deklarací identity a přidružená služba vlastního Správce autorizací. To je užitečné, když služba díky přístupu na základě deklarace identity ověří k operacím služby a před kontroly přístupu, uděluje volající určitá práva. Tento příklad ukazuje, jak proces přidávání deklarací identity, jakož i proces pro provádění kontroly přístupu proti dokončené sadu deklarací identity. Všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat. Ve výchozím nastavení se `wsHttpBinding` vazby, uživatelské jméno a heslo, které poskytl klient, se používají k přihlašování na platný účet systému Windows NT. Tento příklad ukazuje, jak využívat vlastní <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` k ověření klienta. Kromě toho tento příklad ukazuje ověřování do služby pomocí certifikátu X.509. certifikát klienta. Tento příklad ukazuje implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a <xref:System.ServiceModel.ServiceAuthorizationManager>, které mezi sebou udělit přístup k konkrétních metod služby pro konkrétní uživatele. Tato ukázka je založena na [zpráva zabezpečení uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale ukazuje, jak provést transformace deklarací identity před <xref:System.ServiceModel.ServiceAuthorizationManager> volána.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V souhrnu, tento příklad ukazuje, jak:  
  
-   Klienta můžete ověřit pomocí uživatelského jména a hesla.  
  
-   Klienta můžete ověřit pomocí certifikátu X.509.  
  
-   Server ověřuje pověření klienta proti vlastní `UsernamePassword` validátoru.  
  
-   Server byl ověřovaný pomocí certifikátu X.509 serveru.  
  
-   Server můžete použít <xref:System.ServiceModel.ServiceAuthorizationManager> pro řízení přístupu k některé metody v rámci služby.  
  
-   Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
 Službu zpřístupní dva koncové body pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontraktu. Jednu vazbu nastavena standardní `wsHttpBinding` vazby, která používá ověřování uživatelského jména WS-zabezpečení a klienta. Druhé vazby nastavena standardní `wsHttpBinding` vazby, který se používá ověření certifikátu služby WS-zabezpečení a klienta. [ \<Chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Určuje, že má být použit pro ověřování služby jsou přihlašovací údaje uživatele. Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` vlastnost jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <!-- configure base address provided by host -->  
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>  
        </baseAddresses>  
      </host>  
      <!-- use base address provided by host, provide two endpoints -->  
      <endpoint address="username"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      <endpoint address="certificate"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding2"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Username binding -->  
      <binding name="Binding1">  
        <security mode="Message">  
    <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
      <!-- X509 certificate binding -->  
      <binding name="Binding2">  
        <security mode="Message">  
          <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior" >  
        <serviceDebug includeExceptionDetailInFaults ="true" />  
        <serviceCredentials>  
          <!--   
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.    
          -->  
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />  
          <!--   
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.  
          -->  
          <clientCertificate>  
            <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </clientCertificate>  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
          <!--   
          The serviceAuthorization behavior allows one to specify custom authorization policies.  
          -->  
          <authorizationPolicies>  
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
```  
  
 Každý koncový bod konfigurace klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt. Vazba je klient nakonfigurován s režimem příslušná bezpečnostní uvedeného v tomto případě v [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a `clientCredentialType` uvedené v [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- Username based endpoint -->  
      <endpoint name="Username"  
            address="http://localhost:8001/servicemodelsamples/service/username"   
    binding="wsHttpBinding"   
    bindingConfiguration="Binding1"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator" >  
      </endpoint>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
                        address="http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
            bindingConfiguration="Binding2"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- Username binding -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding2">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
    </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <behavior name="ClientCertificateBehavior">  
        <clientCredentials>  
          <serviceCertificate>  
            <!--   
            Setting the certificateValidationMode to PeerOrChainTrust  
            means that if the certificate   
            is in the user's Trusted People store, then it will be   
            trusted without performing a  
            validation of the certificate's issuer chain. This setting   
            is used here for convenience so that the   
            sample can be run without having to have certificates   
            issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust.   
            The security implications of this   
            setting should be carefully considered before using   
            PeerOrChainTrust in production code.   
            -->  
            <authentication certificateValidationMode = "PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Implementace klienta pro uživatele na základě názvu koncového bodu, nastaví uživatelské jméno a heslo.  
  
```  
// Create a client with Username endpoint configuration  
CalculatorClient client1 = new CalculatorClient("Username");  
  
client1.ClientCredentials.UserName.UserName = "test1";  
client1.ClientCredentials.UserName.Password = "1tset";  
  
try  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client1.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
    ...  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
}  
  
client1.Close();  
```  
  
 Implementace klienta pro koncový bod založené na certifikátech, nastaví certifikát klienta, který chcete použít.  
  
```  
// Create a client with Certificate endpoint configuration  
CalculatorClient client2 = new CalculatorClient("Certificate");  
  
client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
try  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client2.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
    ...  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
}  
  
client2.Close();  
```  
  
 Tato ukázka používá vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> k ověření uživatelského jména a hesla. Ukázka implementuje `MyCustomUserNamePasswordValidator`, odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Najdete v dokumentaci <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace. Pro účely ukázka integrace s <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, tato ukázka vlastní validátor implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda tak, aby přijímal párů jméno a heslo uživatele, kde uživatelské jméno odpovídá heslu, jak je znázorněno v následujícím kódu.  
  
```  
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator  
{  
  // This method validates users. It allows in two users,   
  // test1 and test2 with passwords 1tset and 2tset respectively.  
  // This code is for illustration purposes only and   
  // MUST NOT be used in a production environment because it   
  // is NOT secure.      
  public override void Validate(string userName, string password)  
  {  
    if (null == userName || null == password)  
    {  
      throw new ArgumentNullException();  
    }  
  
    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))  
    {  
      throw new SecurityTokenException("Unknown Username or Password");  
    }  
  }  
}  
```  
  
 Po validátor je implementovaná v kódu služby, hostitele služby musí být informováni o instanci program pro ověření používat. To se provádí pomocí následujícího kódu.  
  
```  
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();  
```  
  
 Nebo můžete provést totéž v konfiguraci.  
  
```xml  
<behavior ...>  
    <serviceCredentials>  
      <!--   
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.    
      -->  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />  
    ...  
    </serviceCredentials>  
</behavior>  
```  
  
 Windows Communication Foundation (WCF) poskytuje model bohaté založené na deklaracích pro provádění kontroly přístupu. <xref:System.ServiceModel.ServiceAuthorizationManager> Objekt se používá k provedení kontroly přístupu a určit, jestli deklarace identity přidružené ke klientovi splňují požadavky potřebné pro přístup k metodě služby.  
  
 Pro demonstrační účely, tento příklad ukazuje implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> , která implementuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda pro povolení přístupu uživatele k metody na základě deklarací typu http://example.com/claims/allowedoperation jehož hodnota je identifikátor URI akce operace, která se mohou být volána.  
  
```  
public class MyServiceAuthorizationManager : ServiceAuthorizationManager  
{  
  protected override bool CheckAccessCore(OperationContext operationContext)  
  {                  
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;  
    Console.WriteLine("action: {0}", action);  
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)  
    {  
      if ( cs.Issuer == ClaimSet.System )  
      {  
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))  
        {  
          Console.WriteLine("resource: {0}", c.Resource.ToString());  
          if (action == c.Resource.ToString())  
            return true;  
        }  
      }  
    }  
    return false;                   
  }  
}  
```  
  
 Jednou vlastní <xref:System.ServiceModel.ServiceAuthorizationManager> je implementována, hostitele služby musí být informováni o <xref:System.ServiceModel.ServiceAuthorizationManager> používat. Důvodem je, jak je znázorněno v následujícím kódu.  
  
```xml  
<behavior ...>  
    ...  
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
        ...  
    </serviceAuthorization>  
</behavior>  
```  
  
 Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> je metoda implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda.  
  
```  
public class MyAuthorizationPolicy : IAuthorizationPolicy  
{  
    string id;  
  
    public MyAuthorizationPolicy()  
    {  
    id =  Guid.NewGuid().ToString();  
    }  
  
    public bool Evaluate(EvaluationContext evaluationContext,   
                                            ref object state)  
    {  
        bool bRet = false;  
        CustomAuthState customstate = null;  
  
        if (state == null)  
        {  
            customstate = new CustomAuthState();  
            state = customstate;  
        }  
        else  
            customstate = (CustomAuthState)state;  
        Console.WriteLine("In Evaluate");  
        if (!customstate.ClaimsAdded)  
        {  
           IList<Claim> claims = new List<Claim>();  
  
           foreach (ClaimSet cs in evaluationContext.ClaimSets)  
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,   
                                         Rights.PossessProperty))  
                  foreach (string s in   
                        GetAllowedOpList(c.Resource.ToString()))  
                  {  
                       claims.Add(new  
               Claim("http://example.com/claims/allowedoperation",   
                                    s, Rights.PossessProperty));  
                            Console.WriteLine("Claim added {0}", s);  
                      }  
                   evaluationContext.AddClaimSet(this,   
                           new DefaultClaimSet(this.Issuer,claims));  
                   customstate.ClaimsAdded = true;  
                   bRet = true;  
                }  
         else  
         {  
              bRet = true;  
         }  
         return bRet;  
     }  
...  
}  
```  
  
 Předchozí kód ukazuje jak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda ověří, že byly přidány nové deklarace identity, vliv na zpracování a přidá deklarace identity specifické. Deklarace identity, které jsou povoleny jsou získávány z `GetAllowedOpList` metody, které je implementované vrátit na konkrétní seznam operací, které má uživatel k provedení. Zásady autorizace přidá deklarace identity pro přístup ke konkrétní operaci. Používá se později pomocí <xref:System.ServiceModel.ServiceAuthorizationManager> k provedení rozhodnutí kontroly přístupu.  
  
 Jednou vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementace hostitele služby musí být informováni o zásady autorizace používat.  
  
```xml  
<serviceAuthorization ...>  
       <authorizationPolicies>   
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />  
       </authorizationPolicies>   
</serviceAuthorization>  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně volá přidat, Subtract a několik metod a získá zprávu "Přístup byl odepřen" při volání metody dělení. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci:  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. Proměnná % název_serveru % Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota je localhost.  
  
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
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty, které jsou generovány nástrojem Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Vytvoření certifikátu klienta.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit klientský certifikát, který se má použít. Proměnná % uživatelské_jméno % Určuje název serveru. Tato hodnota nastavena na "test1", protože je to název `IAuthorizationPolicy` hledá. Pokud změníte hodnotu % uživatelské_jméno % musíte změnit s odpovídající hodnotou v `IAuthorizationPolicy.Evaluate` metoda.  
  
     Certifikát je uložen v tomto úložišti (osobních) v umístění úložiště CurrentUser.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru.  
  
     Následující řádky v dávkovém souboru, Setup.bat zkopírujte certifikát klienta do úložiště důvěryhodných osob. Tento krok je povinný, protože certifikáty, které jsou generovány nástrojem Makecert.exe nejsou důvěryhodný implicitně systému serveru. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů serveru pomocí certifikátu klienta se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, použijte následující pokyny.  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno příkazového řádku s oprávněními správce a spusťte Setup.bat ve složce instalace ukázkové. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spustit Setup.bat v sadě Visual Studio s oprávněními správce z ukázky otevřít příkazový řádek instalační složku. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
3.  Spusťte Service.exe z service\bin.  
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
5.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou.  
  
2.  Zkopírujte soubory programu služby z \service\bin do adresáře na počítači se službou. Taky zkopírujte soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.  
  
3.  Vytvoření adresáře na klienta počítačeDalší binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s názvem plně kvalifikované domény computerand Exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit Service.exe.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače. Také změnit vlastnosti computername v \<služby > /\<baseAddresses > element z místního hostitele na plně kvalifikovaný název služby počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na klientovi, spusťte `setup.bat client` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem test1 a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. To nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce otevřít. Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
13. Na počítači serveru spusťte Service.exe z okna příkazového řádku.  
  
14. Na klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky. Tím se odebere z úložiště certifikátů serveru a klientské certifikáty.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili Ukázky WCF, které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople uložit. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
