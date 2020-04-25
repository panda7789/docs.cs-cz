---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: e66188cfe1874c4d4097f3f842fd19cfdd4c79f1
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141277"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="20568-102">Validátor hesel pro uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="20568-102">User Name Password Validator</span></span>
<span data-ttu-id="20568-103">Tato ukázka předvádí, jak implementovat vlastní validátor UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="20568-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="20568-104">To je užitečné v případech, kdy žádný z vestavěných režimů ověřování UserNamePassword není vhodný pro požadavky aplikace. například když jsou páry uživatelského jména a hesla uložené v některém externím úložišti, jako je třeba databáze.</span><span class="sxs-lookup"><span data-stu-id="20568-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="20568-105">Tato ukázka obsahuje službu, která má vlastní validátor, který kontroluje dvě konkrétní páry uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="20568-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="20568-106">Klient používá k ověření ve službě takové párování uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="20568-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20568-107">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="20568-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20568-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="20568-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="20568-109">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="20568-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20568-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20568-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="20568-111">Vzhledem k tomu, že kdokoli může vytvořit přihlašovací údaje pro uživatelské jméno, které používají páry uživatelské jméno a heslo, které vlastní validátor akceptuje, je tato služba méně bezpečná, než je výchozí chování, které poskytuje standardní validátor UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="20568-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="20568-112">Standardní validátor UserNamePassword se pokusí mapovat zadané párování uživatelského jména a hesla k účtu systému Windows a ověřování se nepovede, pokud toto mapování neproběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="20568-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="20568-113">Vlastní validátor UserNamePassword v této ukázce nesmí být použit v produkčním kódu, je určen pouze pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="20568-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="20568-114">V části Souhrn tento příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="20568-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="20568-115">Klienta lze ověřit pomocí tokenu uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="20568-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="20568-116">Server ověří pověření klienta proti vlastnímu UserNamePasswordValidator a rozšíří vlastní chyby z logiky ověření uživatelského jména a hesla na klienta.</span><span class="sxs-lookup"><span data-stu-id="20568-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="20568-117">Server je ověřený pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="20568-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="20568-118">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config. Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20568-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="20568-119">Vazba je konfigurovaná se standardem `wsHttpBinding` , který používá výchozí ověřování pomocí protokolu WS-Security a uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="20568-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="20568-120">Chování služby určuje `Custom` režim pro ověření párů uživatelského jména a hesla klienta spolu s typem třídy validátoru.</span><span class="sxs-lookup"><span data-stu-id="20568-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="20568-121">Chování také Určuje certifikát serveru pomocí `serviceCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="20568-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="20568-122">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="20568-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="20568-123">Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20568-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="20568-124">Vazba klienta je nakonfigurovaná s odpovídajícím režimem a `clientCredentialType`zprávou.</span><span class="sxs-lookup"><span data-stu-id="20568-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="20568-125">Implementace klienta vyzve uživatele k zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="20568-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="20568-126">Tato ukázka používá vlastní UserNamePasswordValidator k ověření párů uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="20568-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="20568-127">Ukázka implementuje `CustomUserNamePasswordValidator`odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="20568-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="20568-128">Další informace najdete v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="20568-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="20568-129">Tato konkrétní ukázka vlastního validátoru implementuje `Validate` metodu pro přijetí dvou konkrétních párů uživatelského jména a hesla, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="20568-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="20568-130">Po implementaci ověřovacího modulu v kódu služby musí být hostitel služby informován o instanci validátoru, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="20568-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="20568-131">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="20568-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="20568-132">Nebo můžete stejnou věc provést v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="20568-132">Or you can do the same thing in configuration as follows.</span></span>

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
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="20568-133">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="20568-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="20568-134">Klient by měl úspěšně volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="20568-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="20568-135">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="20568-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="20568-136">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="20568-136">Setup Batch File</span></span>
 <span data-ttu-id="20568-137">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="20568-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="20568-138">Tento dávkový soubor je potřeba upravit tak, aby fungoval napříč počítači nebo fungoval v nesamoobslužném případě.</span><span class="sxs-lookup"><span data-stu-id="20568-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="20568-139">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="20568-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="20568-140">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="20568-140">Creating the server certificate:</span></span>

     <span data-ttu-id="20568-141">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="20568-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="20568-142">Proměnná% SERVER_NAME% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="20568-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="20568-143">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="20568-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="20568-144">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="20568-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="20568-145">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="20568-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="20568-146">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="20568-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="20568-147">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="20568-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="20568-148">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="20568-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="20568-149">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="20568-149">To set up and build the sample</span></span>

1. <span data-ttu-id="20568-150">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20568-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="20568-151">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="20568-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="20568-152">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="20568-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="20568-153">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="20568-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="20568-154">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="20568-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20568-155">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="20568-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="20568-156">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="20568-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="20568-157">Spustit Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="20568-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="20568-158">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="20568-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="20568-159">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="20568-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="20568-160">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20568-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="20568-161">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="20568-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="20568-162">Vytvořte adresář na počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="20568-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="20568-163">Zkopírujte programové soubory služby do adresáře služby na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="20568-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="20568-164">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="20568-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="20568-165">Potřebujete certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="20568-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="20568-166">Konfigurační soubor pro server se musí aktualizovat, aby odrážel tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="20568-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="20568-167">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="20568-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="20568-168">To je nutné provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="20568-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="20568-169">V souboru App. config na počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="20568-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="20568-170">Na počítači služby spusťte z okna příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="20568-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="20568-171">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="20568-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="20568-172">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="20568-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="20568-173">Na klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="20568-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="20568-174">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20568-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="20568-175">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="20568-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="20568-176">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="20568-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="20568-177">Tím se odebere certifikát serveru z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="20568-177">This removes the server certificate from the certificate store.</span></span>  
