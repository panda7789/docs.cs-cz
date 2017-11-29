---
title: "Zabezpečení zpráv s uživatelským jménem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: acf01818a697f2267307bdf7b9e469fec5741511
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-user-name"></a><span data-ttu-id="6aa57-102">Zabezpečení zpráv s uživatelským jménem</span><span class="sxs-lookup"><span data-stu-id="6aa57-102">Message Security User Name</span></span>
<span data-ttu-id="6aa57-103">Tento příklad znázorňuje implementaci aplikace, která využívá WS-zabezpečení pomocí uživatelského jména ověřování klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru.</span><span class="sxs-lookup"><span data-stu-id="6aa57-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="6aa57-104">Všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="6aa57-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="6aa57-105">Ve výchozím nastavení, uživatelské jméno a heslo, které poskytl klient, se používají k přihlašování platný účet systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa57-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="6aa57-106">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6aa57-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="6aa57-107">Tato ukázka se skládá z konzoly programu klienta (Client.exe) a knihovna service (Service.dll) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="6aa57-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="6aa57-108">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6aa57-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6aa57-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6aa57-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6aa57-110">Tento příklad také ukazuje:</span><span class="sxs-lookup"><span data-stu-id="6aa57-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="6aa57-111">Výchozí mapování na účty v systému Windows tak, že lze provést další autorizace.</span><span class="sxs-lookup"><span data-stu-id="6aa57-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="6aa57-112">Jak pro přístup k informacím identitu volajícího z kódu služby.</span><span class="sxs-lookup"><span data-stu-id="6aa57-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="6aa57-113">Službu zpřístupní jeden koncový bod pro komunikaci se službou, která je definovaná pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6aa57-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6aa57-114">Vazba je nakonfigurována s standard [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), který používá ve výchozím nastavení zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="6aa57-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="6aa57-115">Tato ukázka nastaví standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="6aa57-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="6aa57-116">Chování Určuje, zda má být použit pro ověřování služby jsou pověření uživatele.</span><span class="sxs-lookup"><span data-stu-id="6aa57-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="6aa57-117">Certifikát serveru musí obsahovat stejnou hodnotu pro název subjektu, jako `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="6aa57-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="6aa57-118">Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6aa57-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="6aa57-119">Klient vazba je konfigurován s odpovídající `securityMode` a `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="6aa57-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="6aa57-120">Při spuštění ve scénáři mezi počítači, musíte změnit odpovídajícím způsobem adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="6aa57-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="6aa57-121">Implementace klienta nastaví uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="6aa57-121">The client implementation sets the user name and password to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="6aa57-122">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa57-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6aa57-123">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa57-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="6aa57-124">Dávkový soubor Setup.bat součástí ukázky MessageSecurity umožňuje nakonfigurovat server se příslušný certifikát spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6aa57-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="6aa57-125">Dávkový soubor lze spustit ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="6aa57-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="6aa57-126">Chcete-li spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="6aa57-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="6aa57-127">Chcete-li používat typ režim služby `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="6aa57-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="6aa57-128">Můžete použít tento režim při spuštění ukázky pro počítače.</span><span class="sxs-lookup"><span data-stu-id="6aa57-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="6aa57-129">Přečtěte si postup instalace na konci tohoto tématu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="6aa57-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="6aa57-130">Následující poskytuje stručný přehled různých oddílů dávkové soubory.</span><span class="sxs-lookup"><span data-stu-id="6aa57-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="6aa57-131">Vytvoření certifikátu serveru</span><span class="sxs-lookup"><span data-stu-id="6aa57-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="6aa57-132">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6aa57-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="6aa57-133">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="6aa57-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6aa57-134">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="6aa57-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="6aa57-135">Pokud dávkový soubor Setup.bat spuštění s argumentem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="6aa57-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="6aa57-136">V opačném případě bude výchozí localhost.</span><span class="sxs-lookup"><span data-stu-id="6aa57-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="6aa57-137">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta</span><span class="sxs-lookup"><span data-stu-id="6aa57-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="6aa57-138">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa57-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6aa57-139">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa57-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6aa57-140">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="6aa57-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="6aa57-141">Udělení oprávnění pro privátní klíč certifikátu</span><span class="sxs-lookup"><span data-stu-id="6aa57-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="6aa57-142">Zkontrolujte následující řádky v dávkovém souboru, Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="6aa57-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
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
    >  <span data-ttu-id="6aa57-143">Pokud používáte jiný USA Anglickou verzi systému Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu s vaší místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="6aa57-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6aa57-144">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="6aa57-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6aa57-145">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6aa57-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6aa57-146">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6aa57-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6aa57-147">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="6aa57-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="6aa57-148">Ujistěte se, že cesta obsahuje složku, kde jsou umístěny Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="6aa57-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="6aa57-149">Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazový řádek s oprávněními správce otevřít.</span><span class="sxs-lookup"><span data-stu-id="6aa57-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="6aa57-150">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="6aa57-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6aa57-151">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio – příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="6aa57-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="6aa57-152">To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="6aa57-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6aa57-153">Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio – příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="6aa57-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="6aa57-154">Ověřte přístup ke službě pomocí prohlížeče zadáním adresy http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="6aa57-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="6aa57-155">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="6aa57-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="6aa57-156">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="6aa57-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="6aa57-157">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="6aa57-157">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6aa57-158">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="6aa57-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="6aa57-159">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="6aa57-159">Create a directory on the service computer.</span></span> <span data-ttu-id="6aa57-160">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6aa57-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="6aa57-161">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="6aa57-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="6aa57-162">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="6aa57-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="6aa57-163">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="6aa57-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="6aa57-164">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa57-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="6aa57-165">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="6aa57-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="6aa57-166">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="6aa57-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="6aa57-167">Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6aa57-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="6aa57-168">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="6aa57-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="6aa57-169">Upravit soubor Web.config tak, aby odrážela nový název certifikátu (v atributu findValue v elementu serviceCertificate), která je stejná jako plně kvalifikovaný název domény počítače`.`</span><span class="sxs-lookup"><span data-stu-id="6aa57-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="6aa57-170">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="6aa57-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="6aa57-171">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="6aa57-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="6aa57-172">V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6aa57-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="6aa57-173">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="6aa57-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="6aa57-174">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="6aa57-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="6aa57-175">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="6aa57-175">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6aa57-176">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="6aa57-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="6aa57-177">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="6aa57-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6aa57-178">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="6aa57-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="6aa57-179">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="6aa57-179">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6aa57-180">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="6aa57-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa57-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="6aa57-181">See Also</span></span>
