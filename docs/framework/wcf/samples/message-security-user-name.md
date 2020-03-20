---
title: Zabezpečení zpráv s uživatelským jménem
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183502"
---
# <a name="message-security-user-name"></a><span data-ttu-id="f5c84-102">Zabezpečení zpráv s uživatelským jménem</span><span class="sxs-lookup"><span data-stu-id="f5c84-102">Message Security User Name</span></span>
<span data-ttu-id="f5c84-103">Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním uživatelského jména pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509v3 serveru.</span><span class="sxs-lookup"><span data-stu-id="f5c84-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="f5c84-104">Všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány.</span><span class="sxs-lookup"><span data-stu-id="f5c84-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="f5c84-105">Ve výchozím nastavení se uživatelské jméno a heslo zadané klientem používají k přihlášení k platnému účtu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f5c84-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="f5c84-106">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f5c84-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="f5c84-107">Tato ukázka se skládá z programu klientské konzole (Client.exe) a knihovny služeb (Service.dll) hostované Internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="f5c84-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="f5c84-108">Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="f5c84-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5c84-109">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f5c84-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5c84-110">Tento vzorek také ukazuje:</span><span class="sxs-lookup"><span data-stu-id="f5c84-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="f5c84-111">Výchozí mapování na účty systému Windows, aby bylo možné provést další autorizaci.</span><span class="sxs-lookup"><span data-stu-id="f5c84-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="f5c84-112">Jak získat přístup k informacím o identitě volajícího z kódu služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="f5c84-113">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="f5c84-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="f5c84-114">Vazba je nakonfigurována se standardním [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), který ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f5c84-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="f5c84-115">Tato ukázka nastaví standardní [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) pro použití ověřování uživatelského jména klienta.</span><span class="sxs-lookup"><span data-stu-id="f5c84-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="f5c84-116">Chování určuje, že pověření uživatele mají být použita pro ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="f5c84-117">Certifikát serveru musí obsahovat stejnou hodnotu `findValue` pro název subjektu jako atribut v [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="f5c84-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f5c84-118">Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu.</span><span class="sxs-lookup"><span data-stu-id="f5c84-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="f5c84-119">Vazby klienta je `securityMode` nakonfigurován s příslušnou a `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="f5c84-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="f5c84-120">Při spuštění ve scénáři mezi počítači musí být odpovídajícím způsobem změněna adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f5c84-121">Implementace klienta nastaví uživatelské jméno a heslo, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="f5c84-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="f5c84-122">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f5c84-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f5c84-123">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="f5c84-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f5c84-124">Dávkový soubor Setup.bat, který je součástí ukázek MessageSecurity, umožňuje nakonfigurovat server s příslušným certifikátem tak, aby spouštěl hostovnu, která vyžaduje zabezpečení založené na certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f5c84-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="f5c84-125">Dávkový soubor lze spustit ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="f5c84-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="f5c84-126">Chcete-li dávkový soubor spustit v `setup.bat` režimu jednoho počítače, zadejte příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="f5c84-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="f5c84-127">Chcete-li jej spustit `setup.bat service`v servisním režimu typu .</span><span class="sxs-lookup"><span data-stu-id="f5c84-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="f5c84-128">Tento režim se používá při spuštění ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="f5c84-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="f5c84-129">Podrobnosti naleznete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f5c84-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="f5c84-130">Následující text poskytuje stručný přehled různých částí dávkových souborů.</span><span class="sxs-lookup"><span data-stu-id="f5c84-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="f5c84-131">Vytvoření certifikátu serveru</span><span class="sxs-lookup"><span data-stu-id="f5c84-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="f5c84-132">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="f5c84-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="f5c84-133">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="f5c84-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="f5c84-134">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f5c84-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="f5c84-135">Pokud je dávkový soubor Setup.bat spuštěn s `setup.bat service`argumentem služby (například) % SERVER_NAME% obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="f5c84-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="f5c84-136">V opačném případě je výchozí localhost.</span><span class="sxs-lookup"><span data-stu-id="f5c84-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="f5c84-137">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta</span><span class="sxs-lookup"><span data-stu-id="f5c84-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="f5c84-138">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="f5c84-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="f5c84-139">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="f5c84-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="f5c84-140">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="f5c84-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="f5c84-141">Udělení oprávnění k soukromému klíči certifikátu</span><span class="sxs-lookup"><span data-stu-id="f5c84-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="f5c84-142">Následující řádky v dávkovém souboru Setup.bat zpřístupní certifikát serveru uložený v úložišti LocalMachine ASP.NET účtu pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="f5c84-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="f5c84-143">Pokud používáte edici systému Windows, která není v USA, je `NT AUTHORITY\NETWORK SERVICE` nutné upravit soubor Setup.bat a nahradit název účtu místním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="f5c84-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5c84-144">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f5c84-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f5c84-145">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5c84-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f5c84-146">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5c84-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="f5c84-147">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="f5c84-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="f5c84-148">Ujistěte se, že cesta obsahuje složku, kde jsou umístěny Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="f5c84-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="f5c84-149">Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku pro vývojáře pro sady Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="f5c84-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="f5c84-150">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="f5c84-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5c84-151">Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5c84-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="f5c84-152">Vyžaduje, aby proměnná prostředí cesty přecškovala do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="f5c84-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="f5c84-153">Tato proměnná prostředí je automaticky nastavena v příkazovém řádku pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5c84-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="f5c84-154">Ověřte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním adresy .</span><span class="sxs-lookup"><span data-stu-id="f5c84-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="f5c84-155">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="f5c84-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="f5c84-156">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="f5c84-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="f5c84-157">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f5c84-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f5c84-158">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="f5c84-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="f5c84-159">Vytvořte adresář v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-159">Create a directory on the service computer.</span></span> <span data-ttu-id="f5c84-160">Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="f5c84-161">Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="f5c84-162">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="f5c84-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="f5c84-163">Zkopírujte také soubory Setup.bat a Cleanup.bat do servisního počítače.</span><span class="sxs-lookup"><span data-stu-id="f5c84-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="f5c84-164">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="f5c84-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="f5c84-165">Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="f5c84-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="f5c84-166">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="f5c84-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="f5c84-167">Na serveru spusťte `setup.bat service` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="f5c84-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="f5c84-168">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="f5c84-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="f5c84-169">Úprava souboru Web.config tak, aby odrážel nový název certifikátu (v atributu findValue v elementu serviceCertificate), který je stejný jako plně kvalifikovaný název domény počítače`.`</span><span class="sxs-lookup"><span data-stu-id="f5c84-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="f5c84-170">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="f5c84-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="f5c84-171">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="f5c84-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="f5c84-172">Na straně klienta spusťte soubor ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="f5c84-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="f5c84-173">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="f5c84-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="f5c84-174">V klientském počítači spusťte soubor Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f5c84-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="f5c84-175">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f5c84-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f5c84-176">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="f5c84-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="f5c84-177">Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="f5c84-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5c84-178">Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="f5c84-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="f5c84-179">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="f5c84-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="f5c84-180">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .</span><span class="sxs-lookup"><span data-stu-id="f5c84-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
