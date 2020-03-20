---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 202c7bfc7f60afbad8220950e46c08c0a71eb001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183251"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="02e3d-102">Validátor hesel pro uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="02e3d-102">User Name Password Validator</span></span>
<span data-ttu-id="02e3d-103">Tato ukázka ukazuje, jak implementovat vlastní UserNamePassword Validator.</span><span class="sxs-lookup"><span data-stu-id="02e3d-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="02e3d-104">To je užitečné v případech, kdy žádný z předdefinovaných režimů ověření usernamepassword je vhodný pro požadavky aplikace; například když jsou dvojice uživatelského jména a hesla uloženy v některém externím úložišti, například v databázi.</span><span class="sxs-lookup"><span data-stu-id="02e3d-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="02e3d-105">Tato ukázka ukazuje službu, která má vlastní validátor, který kontroluje dva konkrétní dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="02e3d-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="02e3d-106">Klient používá takový pár uživatelského jména a hesla k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="02e3d-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02e3d-107">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="02e3d-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="02e3d-108">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="02e3d-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="02e3d-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="02e3d-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02e3d-110">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="02e3d-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="02e3d-111">Vzhledem k tomu, že kdokoli může vytvořit pověření uživatelského jména, které používá dvojice uživatelského jména a hesla, které přijímá vlastní validátor, je služba méně zabezpečená než výchozí chování poskytované standardním validátorem UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="02e3d-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="02e3d-112">Standardní uživatelPasswordPassword Validator se pokusí namapovat zadaný pár uživatelského jména a hesla na účet systému Windows a pokud se toto mapování nezdaří, ověření se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="02e3d-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="02e3d-113">Vlastní UživatelPasswordPassword Validator v této ukázce nesmí být použit v produkčním kódu, je pouze pro ilustrační účely.</span><span class="sxs-lookup"><span data-stu-id="02e3d-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="02e3d-114">V souhrnu tento vzorek ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="02e3d-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="02e3d-115">Klient může být ověřen pomocí tokenu uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="02e3d-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="02e3d-116">Server ověří pověření klienta proti vlastní UserNamePasswordValidator a jak šířit vlastní chyby z uživatelského jména a logiky ověření hesla do klienta.</span><span class="sxs-lookup"><span data-stu-id="02e3d-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="02e3d-117">Server je ověřen pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="02e3d-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="02e3d-118">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="02e3d-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="02e3d-119">Vazba je konfigurována `wsHttpBinding` se standardem, který je výchozí pro použití ws-security a ověřování uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="02e3d-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="02e3d-120">Chování služby určuje `Custom` režim pro ověřování párů uživatelského jména a hesla klienta spolu s typem třídy validátoru.</span><span class="sxs-lookup"><span data-stu-id="02e3d-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="02e3d-121">Chování také určuje certifikát serveru `serviceCertificate` pomocí prvku.</span><span class="sxs-lookup"><span data-stu-id="02e3d-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="02e3d-122">Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu `findValue` jako v [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="02e3d-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="02e3d-123">Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy pro koncový bod služby, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="02e3d-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="02e3d-124">Vazby klienta je konfigurována `clientCredentialType`s příslušným režimem a zprávou .</span><span class="sxs-lookup"><span data-stu-id="02e3d-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="02e3d-125">Implementace klienta vyzve uživatele k zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="02e3d-125">The client implementation prompts the user to enter a username and password.</span></span>

```csharp
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

 <span data-ttu-id="02e3d-126">Tato ukázka používá vlastní UserNamePasswordValidator k ověření dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="02e3d-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="02e3d-127">Ukázka implementuje `CustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>odvozené z .</span><span class="sxs-lookup"><span data-stu-id="02e3d-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="02e3d-128">Další informace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="02e3d-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="02e3d-129">Tento konkrétní vlastní validátor ukázka implementuje metodu `Validate` přijmout dvě konkrétní uživatelské jméno a heslo dvojice, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="02e3d-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

```csharp
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

 <span data-ttu-id="02e3d-130">Jakmile je validátor implementován v kódu služby, musí být hostitel služby informován o instanci validátoru, která má být používána.</span><span class="sxs-lookup"><span data-stu-id="02e3d-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="02e3d-131">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="02e3d-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="02e3d-132">Nebo můžete udělat totéž v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="02e3d-132">Or you can do the same thing in configuration as follows.</span></span>

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

 <span data-ttu-id="02e3d-133">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="02e3d-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="02e3d-134">Klient by měl úspěšně volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="02e3d-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="02e3d-135">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="02e3d-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="02e3d-136">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="02e3d-136">Setup Batch File</span></span>
 <span data-ttu-id="02e3d-137">Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru.</span><span class="sxs-lookup"><span data-stu-id="02e3d-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="02e3d-138">Tento dávkový soubor musí být upraven tak, aby fungoval napříč počítači nebo aby fungoval v případě, který není hostovaný sám.</span><span class="sxs-lookup"><span data-stu-id="02e3d-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="02e3d-139">Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="02e3d-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="02e3d-140">Vytvoření certifikátu serveru:</span><span class="sxs-lookup"><span data-stu-id="02e3d-140">Creating the server certificate:</span></span>

     <span data-ttu-id="02e3d-141">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="02e3d-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="02e3d-142">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="02e3d-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="02e3d-143">Změňte tuto proměnnou a zadejte vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="02e3d-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="02e3d-144">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="02e3d-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="02e3d-145">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="02e3d-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="02e3d-146">Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="02e3d-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="02e3d-147">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="02e3d-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="02e3d-148">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="02e3d-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="02e3d-149">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="02e3d-149">To set up and build the sample</span></span>

1. <span data-ttu-id="02e3d-150">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02e3d-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="02e3d-151">Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="02e3d-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="02e3d-152">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="02e3d-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="02e3d-153">Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="02e3d-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="02e3d-154">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="02e3d-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02e3d-155">Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="02e3d-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="02e3d-156">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory vyžadované skriptem Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="02e3d-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="02e3d-157">Spusťte soubor Service.exe ze služby\přihrádka.</span><span class="sxs-lookup"><span data-stu-id="02e3d-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="02e3d-158">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="02e3d-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="02e3d-159">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="02e3d-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="02e3d-160">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02e3d-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="02e3d-161">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="02e3d-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="02e3d-162">Vytvořte adresář na servisním počítači pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="02e3d-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="02e3d-163">Zkopírujte soubory servisních programů do adresáře služby v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="02e3d-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="02e3d-164">Zkopírujte také soubory Setup.bat a Cleanup.bat do servisního stroje.</span><span class="sxs-lookup"><span data-stu-id="02e3d-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="02e3d-165">Potřebujete certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="02e3d-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="02e3d-166">Konfigurační soubor serveru musí být aktualizován tak, aby odrážel tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="02e3d-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="02e3d-167">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="02e3d-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="02e3d-168">To je třeba provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="02e3d-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="02e3d-169">V souboru App.config v servisním počítači změňte hodnotu základní adresy a zadejte plně kvalifikovaný název počítače namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="02e3d-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="02e3d-170">Na servisním počítači spusťte service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="02e3d-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="02e3d-171">Zkopírujte soubory klientských programů ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="02e3d-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="02e3d-172">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="02e3d-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="02e3d-173">V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="02e3d-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="02e3d-174">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02e3d-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="02e3d-175">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="02e3d-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="02e3d-176">Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="02e3d-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="02e3d-177">Tím odeberete certifikát serveru z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="02e3d-177">This removes the server certificate from the certificate store.</span></span>  
