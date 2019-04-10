---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 52c22660e56d63121181bdcb618e0bed598ca585
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345011"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="75afd-102">Validátor hesel pro uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="75afd-102">User Name Password Validator</span></span>
<span data-ttu-id="75afd-103">Tento příklad ukazuje, jak implementovat vlastní UserNamePassword validátor.</span><span class="sxs-lookup"><span data-stu-id="75afd-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="75afd-104">To je užitečné v případech, kdy se žádná z předdefinovaných režimy ověřování UserNamePassword je vhodné pro požadavky na aplikaci. například když páry uživatelského jména a hesla ukládají v některé externí úložiště, například do databáze.</span><span class="sxs-lookup"><span data-stu-id="75afd-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="75afd-105">Tento příklad ukazuje služba, která má vlastní validátor, který kontroluje dvě dvojice konkrétního uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="75afd-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="75afd-106">Klient používá k ověření ve službě dvojici uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="75afd-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="75afd-107">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="75afd-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="75afd-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="75afd-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75afd-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="75afd-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75afd-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="75afd-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="75afd-111">Vzhledem k tomu, že kdokoli může vytvořit uživatelské jméno pověření, která používá následující páry uživatelského jména a hesla, které přijímá vlastní validátor, tato služba je méně bezpečné než výchozí chování poskytuje standardní UserNamePassword validátoru.</span><span class="sxs-lookup"><span data-stu-id="75afd-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="75afd-112">Validátor standardní UserNamePassword pokusí mapovat pár zadané uživatelské jméno a heslo k účtu Windows a ověřování se nezdaří, pokud tato mapování se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="75afd-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="75afd-113">Vlastní UserNamePassword validátor v této ukázce musí není se dá použít v produkčním kódu, je jen jako ukázka.</span><span class="sxs-lookup"><span data-stu-id="75afd-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="75afd-114">V souhrnu Tato ukázka předvádí, jak:</span><span class="sxs-lookup"><span data-stu-id="75afd-114">In summary this sample demonstrates how:</span></span>

-   <span data-ttu-id="75afd-115">Klient lze ověřit pomocí tokenu uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="75afd-115">The client can be authenticated using a Username Token.</span></span>

-   <span data-ttu-id="75afd-116">Server ověří klienta přihlašovacích údajů, kteří vlastní objekt UserNamePasswordValidator a tom, jak rozšířit vlastní chyby z logiku ověřování uživatelského jména a hesla ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="75afd-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

-   <span data-ttu-id="75afd-117">Server byl ověřovaný pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="75afd-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="75afd-118">Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="75afd-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="75afd-119">Je vazba konfigurována se standardní `wsHttpBinding` , která ve výchozím nastavení používá ověřování uživatelským jménem WS Securityand.</span><span class="sxs-lookup"><span data-stu-id="75afd-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="75afd-120">Určuje chování služby `Custom` režimu pro ověřování klienta páry uživatelského jména a hesla společně s typem třídy program pro ověření.</span><span class="sxs-lookup"><span data-stu-id="75afd-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="75afd-121">Také určuje chování serveru pomocí certifikátu `serviceCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="75afd-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="75afd-122">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="75afd-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="75afd-123">Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="75afd-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="75afd-124">Klient vazby je nakonfigurován příslušný režim, zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="75afd-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="75afd-125">Implementace klienta se zobrazí výzva k zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="75afd-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="75afd-126">Tato ukázka používá vlastní objekt UserNamePasswordValidator k ověření uživatelského jména a hesla dvojice.</span><span class="sxs-lookup"><span data-stu-id="75afd-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="75afd-127">Implementuje vzorek `CustomUserNamePasswordValidator`odvozenou z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="75afd-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="75afd-128">Najdete v dokumentaci k <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace.</span><span class="sxs-lookup"><span data-stu-id="75afd-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="75afd-129">Tato ukázka konkrétní vlastní validátor implementuje `Validate` metodu tak, aby přijímal dvě dvojice konkrétního uživatelského jména a hesla, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="75afd-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="75afd-130">Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="75afd-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="75afd-131">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="75afd-131">This is done using the following code.</span></span>

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="75afd-132">Nebo můžete provést totéž v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="75afd-132">Or you can do the same thing in configuration as follows.</span></span>

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

 <span data-ttu-id="75afd-133">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="75afd-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="75afd-134">Klient úspěšně by měly volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="75afd-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="75afd-135">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="75afd-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="75afd-136">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="75afd-136">Setup Batch File</span></span>
 <span data-ttu-id="75afd-137">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="75afd-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="75afd-138">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě bez vlastního hostitele.</span><span class="sxs-lookup"><span data-stu-id="75afd-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="75afd-139">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="75afd-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="75afd-140">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="75afd-140">Creating the server certificate:</span></span>

     <span data-ttu-id="75afd-141">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="75afd-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="75afd-142">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="75afd-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="75afd-143">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="75afd-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="75afd-144">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="75afd-144">The default value is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="75afd-145">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="75afd-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="75afd-146">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="75afd-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="75afd-147">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="75afd-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="75afd-148">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="75afd-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="75afd-149">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="75afd-149">To set up and build the sample</span></span>

1. <span data-ttu-id="75afd-150">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75afd-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="75afd-151">Ke spuštění ukázky v konfiguraci s jedním nebo více počítačů, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="75afd-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="75afd-152">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="75afd-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="75afd-153">Spusťte Setup.bat ve složce instalace ukázkové uvnitř příkazový řádek sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="75afd-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="75afd-154">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="75afd-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="75afd-155">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="75afd-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="75afd-156">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="75afd-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="75afd-157">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="75afd-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="75afd-158">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="75afd-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="75afd-159">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="75afd-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="75afd-160">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75afd-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="75afd-161">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="75afd-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="75afd-162">Vytvoření adresáře v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="75afd-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="75afd-163">Kopírování souborů program služby adresáře služby v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="75afd-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="75afd-164">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="75afd-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="75afd-165">Budete potřebovat certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="75afd-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="75afd-166">Konfigurační soubor serveru musí být aktualizovány tak, aby odrážely tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="75afd-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="75afd-167">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="75afd-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="75afd-168">Budete muset provést pouze v případě, že certifikát serveru není vystavený důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="75afd-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="75afd-169">V souboru App.config v počítači služby změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="75afd-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="75afd-170">Na počítači služby spusťte Service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="75afd-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="75afd-171">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="75afd-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="75afd-172">V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="75afd-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="75afd-173">Na klientském počítači a spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="75afd-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="75afd-174">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75afd-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="75afd-175">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="75afd-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="75afd-176">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="75afd-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="75afd-177">Tím certifikát serveru z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="75afd-177">This removes the server certificate from the certificate store.</span></span>  
