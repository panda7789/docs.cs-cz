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
# <a name="user-name-password-validator"></a><span data-ttu-id="57a2a-102">Validátor hesel pro uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="57a2a-102">User Name Password Validator</span></span>
<span data-ttu-id="57a2a-103">Tento příklad ukazuje, jak implementovat vlastní UserNamePassword validátor.</span><span class="sxs-lookup"><span data-stu-id="57a2a-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="57a2a-104">To je užitečné v případech, kdy žádný z předdefinovaných režimy ověřování UserNamePassword je vhodné pro požadavky na aplikace; Pokud jsou například páry uživatelského jména a hesla uloženy v některé externí úložiště, jako je databáze.</span><span class="sxs-lookup"><span data-stu-id="57a2a-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="57a2a-105">Tento příklad ukazuje služba, která má vlastní validátor, která vyhledává dvě dvojice konkrétní uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="57a2a-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="57a2a-106">Klient používá dvojici uživatelské jméno a heslo k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="57a2a-106">The client uses such a username/password pair to authenticate to the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57a2a-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="57a2a-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="57a2a-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="57a2a-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="57a2a-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="57a2a-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57a2a-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="57a2a-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="57a2a-111">Protože každý, kdo může provést pověření uživatelské jméno, které používá páry uživatelského jména a hesla, které přijímá vlastní validátor, služba je méně bezpečné než výchozí chování poskytuje standardní UserNamePassword validátoru.</span><span class="sxs-lookup"><span data-stu-id="57a2a-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="57a2a-112">Validátor standardní UserNamePassword se pokouší mapovat pár zadané uživatelské jméno a heslo pro účet systému Windows a ověřování se nezdaří, pokud tato mapování se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="57a2a-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="57a2a-113">Vlastní UserNamePassword validátor v této ukázce není musí použít v produkčním kódu, je obrázek pouze pro účely.</span><span class="sxs-lookup"><span data-stu-id="57a2a-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>  
  
 <span data-ttu-id="57a2a-114">V souhrnu tento příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="57a2a-114">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="57a2a-115">Klienta můžete ověřit pomocí tokenu uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="57a2a-115">The client can be authenticated using a Username Token.</span></span>  
  
-   <span data-ttu-id="57a2a-116">Server ověřuje pověření klienta proti vlastní objekt UserNamePasswordValidator a postup rozšíření vlastních chyb z logiku ověření uživatelského jména a hesla do klienta.</span><span class="sxs-lookup"><span data-stu-id="57a2a-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>  
  
-   <span data-ttu-id="57a2a-117">Server byl ověřovaný pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="57a2a-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="57a2a-118">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="57a2a-119">Vazba je nakonfigurována s standardní `wsHttpBinding` který ve výchozím nastavení používá ověřování uživatelským jménem WS-Securityand.</span><span class="sxs-lookup"><span data-stu-id="57a2a-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="57a2a-120">Určuje chování služby `Custom` režimu pro ověřování klienta páry uživatelského jména a hesla společně s typ validátoru třídu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="57a2a-121">Chování také Určuje certifikát serveru pomocí `serviceCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="57a2a-122">Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="57a2a-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="57a2a-123">Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="57a2a-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="57a2a-124">Klient vazba je konfigurován s odpovídající režim a zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="57a2a-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="57a2a-125">Implementace klienta zobrazí výzvu k zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="57a2a-125">The client implementation prompts the user to enter a username and password.</span></span>  
  
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
  
 <span data-ttu-id="57a2a-126">Tato ukázka používá vlastní objekt UserNamePasswordValidator k ověření uživatelského jména a hesla páry.</span><span class="sxs-lookup"><span data-stu-id="57a2a-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="57a2a-127">Ukázka implementuje `CustomUserNamePasswordValidator`, odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="57a2a-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="57a2a-128">Najdete v dokumentaci k <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace.</span><span class="sxs-lookup"><span data-stu-id="57a2a-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="57a2a-129">Tato ukázka konkrétní vlastní validátor implementuje `Validate` metoda tak, aby přijímal dvě dvojice konkrétního uživatelského jména a hesla, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="57a2a-130">Po validátor je implementovaná v kódu služby, hostitele služby musí být informováni o instanci program pro ověření používat.</span><span class="sxs-lookup"><span data-stu-id="57a2a-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="57a2a-131">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-131">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 <span data-ttu-id="57a2a-132">Nebo můžete provést totéž v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="57a2a-132">Or you can do the same thing in configuration as follows.</span></span>  
  
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
  
 <span data-ttu-id="57a2a-133">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="57a2a-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="57a2a-134">Klient úspěšně by měly volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="57a2a-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="57a2a-135">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="57a2a-135">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="57a2a-136">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="57a2a-136">Setup Batch File</span></span>  
 <span data-ttu-id="57a2a-137">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="57a2a-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="57a2a-138">Tento dávkový soubor je nutné upravit v počítačích nebo pracovat v případě bez samoobslužné hostitele.</span><span class="sxs-lookup"><span data-stu-id="57a2a-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>  
  
 <span data-ttu-id="57a2a-139">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="57a2a-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="57a2a-140">Vytvoření certifikátu serveru:</span><span class="sxs-lookup"><span data-stu-id="57a2a-140">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="57a2a-141">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="57a2a-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="57a2a-142">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="57a2a-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="57a2a-143">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="57a2a-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="57a2a-144">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="57a2a-144">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="57a2a-145">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="57a2a-145">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="57a2a-146">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="57a2a-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="57a2a-147">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="57a2a-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="57a2a-148">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="57a2a-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="57a2a-149">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="57a2a-149">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="57a2a-150">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57a2a-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="57a2a-151">Spustit ukázku v konfiguraci s jedním nebo mezi počítače, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="57a2a-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="57a2a-152">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="57a2a-152">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="57a2a-153">Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57a2a-153">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt.</span></span> <span data-ttu-id="57a2a-154">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="57a2a-154">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57a2a-155">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57a2a-155">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="57a2a-156">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="57a2a-156">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="57a2a-157">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="57a2a-157">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="57a2a-158">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="57a2a-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="57a2a-159">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="57a2a-159">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="57a2a-160">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="57a2a-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="57a2a-161">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="57a2a-161">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="57a2a-162">Vytvoření adresáře na počítač služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="57a2a-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="57a2a-163">Zkopírujte soubory programu služby adresář služby v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="57a2a-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="57a2a-164">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="57a2a-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="57a2a-165">Budete potřebovat certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="57a2a-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="57a2a-166">Konfigurační soubor serveru musí aktualizovat tak, aby odrážela tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="57a2a-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4.  <span data-ttu-id="57a2a-167">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="57a2a-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="57a2a-168">Je třeba provést pouze v případě, že certifikát serveru není vystavený důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="57a2a-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="57a2a-169">V souboru App.config v počítači služby změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="57a2a-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="57a2a-170">Na počítači služby spusťte Service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57a2a-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7.  <span data-ttu-id="57a2a-171">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="57a2a-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8.  <span data-ttu-id="57a2a-172">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="57a2a-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="57a2a-173">V klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57a2a-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="57a2a-174">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="57a2a-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="57a2a-175">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="57a2a-175">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="57a2a-176">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="57a2a-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="57a2a-177">Odebere certifikát serveru z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="57a2a-177">This removes the server certificate from the certificate store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a2a-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="57a2a-178">See Also</span></span>
