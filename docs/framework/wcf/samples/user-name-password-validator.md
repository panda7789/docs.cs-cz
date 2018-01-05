---
title: "Validátor hesel pro uživatelská jména"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51f5c91ae63f7c483aab08affe53d6d4b6ceaa01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="user-name-password-validator"></a>Validátor hesel pro uživatelská jména
Tento příklad ukazuje, jak implementovat vlastní UserNamePassword validátor. To je užitečné v případech, kdy žádný z předdefinovaných režimy ověřování UserNamePassword je vhodné pro požadavky na aplikace; Pokud jsou například páry uživatelského jména a hesla uloženy v některé externí úložiště, jako je databáze. Tento příklad ukazuje služba, která má vlastní validátor, která vyhledává dvě dvojice konkrétní uživatelské jméno a heslo. Klient používá dvojici uživatelské jméno a heslo k ověření služby.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  Protože každý, kdo může provést pověření uživatelské jméno, které používá páry uživatelského jména a hesla, které přijímá vlastní validátor, služba je méně bezpečné než výchozí chování poskytuje standardní UserNamePassword validátoru. Validátor standardní UserNamePassword se pokouší mapovat pár zadané uživatelské jméno a heslo pro účet systému Windows a ověřování se nezdaří, pokud tato mapování se nezdaří. Vlastní UserNamePassword validátor v této ukázce není musí použít v produkčním kódu, je obrázek pouze pro účely.  
  
 V souhrnu tento příklad ukazuje, jak:  
  
-   Klienta můžete ověřit pomocí tokenu uživatelské jméno.  
  
-   Server ověřuje pověření klienta proti vlastní objekt UserNamePasswordValidator a postup rozšíření vlastních chyb z logiku ověření uživatelského jména a hesla do klienta.  
  
-   Server byl ověřovaný pomocí certifikátu X.509 serveru.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standardní `wsHttpBinding` který ve výchozím nastavení používá ověřování uživatelským jménem WS-Securityand. Určuje chování služby `Custom` režimu pro ověřování klienta páry uživatelského jména a hesla společně s typ validátoru třídu. Chování také Určuje certifikát serveru pomocí `serviceCertificate` elementu. Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <!-- use host/baseAddresses to configure base address provided by host -->  
      <host>  
        <baseAddresses>  
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />  
        </baseAddresses>  
      </host>  
      <!-- use base address specified above, provide one endpoint -->  
      <endpoint address="username"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- username binding -->  
      <binding name="Binding">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceDebug includeExceptionDetailInFaults ="true"/>  
        <serviceCredentials>  
          <!--   
          The serviceCredentials behavior allows one to   
          specify a custom validator for username/password  
          combinations.  
          -->  
          <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
```  
  
 Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient vazba je konfigurován s odpovídající režim a zpráva `clientCredentialType`.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- Username based endpoint -->  
      <endpoint name="Username"  
address="http://localhost:8001/servicemodelsamples/service/username"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- Username binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Implementace klienta zobrazí výzvu k zadání uživatelského jména a hesla.  
  
```  
// Get the username and password  
Console.WriteLine("Username authentication required.");  
Console.WriteLine("Provide a username.");  
Console.WriteLine("   Enter username: (test1)");  
string username = Console.ReadLine();  
Console.WriteLine("   Enter password:");  
string password = "";  
ConsoleKeyInfo info = Console.ReadKey(true);  
while (info.Key != ConsoleKey.Enter)  
{  
    if (info.Key != ConsoleKey.Backspace)  
    {  
        if (info.KeyChar != '\0')  
        {  
            password += info.KeyChar;  
        }  
        info = Console.ReadKey(true);  
    }  
    else if (info.Key == ConsoleKey.Backspace)  
    {  
        if (password != "")  
        {  
            password = password.Substring(0, password.Length - 1);  
        }  
        info = Console.ReadKey(true);  
    }  
}  
for (int i = 0; i < password.Length; i++)  
{  
    Console.Write("*");  
}  
Console.WriteLine();  
// Create a proxy with Certificate endpoint configuration  
CalculatorProxy proxy = new CalculatorProxy("Username")  
try  
{  
  proxy.ClientCredentials.Username.Username = username;  
  proxy.ClientCredentials.Username.Password = password;  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = proxy.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  }  
  catch (Exception e)  
  {  
      Console.WriteLine("Call failed:");  
      while (e != null)  
      {  
          Console.WriteLine("\t{0}", e.Message);  
          e = e.InnerException;  
      }  
      proxy.Abort();  
  }  
}  
```  
  
 Tato ukázka používá vlastní objekt UserNamePasswordValidator k ověření uživatelského jména a hesla páry. Ukázka implementuje `CustomUserNamePasswordValidator`, odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Najdete v dokumentaci k <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace. Tato ukázka konkrétní vlastní validátor implementuje `Validate` metoda tak, aby přijímal dvě dvojice konkrétního uživatelského jména a hesla, jak je znázorněno v následujícím kódu.  
  
```  
public class CustomUserNameValidator : UserNamePasswordValidator  
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
   throw new FaultException("Unknown Username or Incorrect Password");  
   }  
  }  
 }  
```  
  
 Po validátor je implementovaná v kódu služby, hostitele služby musí být informováni o instanci program pro ověření používat. To se provádí pomocí následujícího kódu.  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 Nebo můžete provést totéž v konfiguraci následujícím způsobem.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="CalculatorServiceBehavior">  
  ...  
   <serviceCredentials>  
    <!--   
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.  
    -->  
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně by měly volat všechny metody. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor je nutné upravit v počítačích nebo pracovat v případě bez samoobslužné hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.  
  
-   Vytvoření certifikátu serveru:  
  
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
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v konfiguraci s jedním nebo mezi počítače, použijte následující pokyny.  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvoření adresáře na počítač služby pro binární soubory služby.  
  
2.  Zkopírujte soubory programu služby adresář služby v počítači služby. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Budete potřebovat certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Konfigurační soubor serveru musí aktualizovat tak, aby odrážela tento nový název certifikátu.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Je třeba provést pouze v případě, že certifikát serveru není vystavený důvěryhodných vystavitelů.  
  
5.  V souboru App.config v počítači služby změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.  
  
6.  Na počítači služby spusťte Service.exe z okna příkazového řádku.  
  
7.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. V klientském počítači spusťte Client.exe z okna příkazového řádku.  
  
10. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky. Odebere certifikát serveru z úložiště certifikátů.  
  
## <a name="see-also"></a>Viz také
