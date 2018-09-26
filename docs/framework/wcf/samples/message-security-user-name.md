---
title: Zabezpečení zpráv s uživatelským jménem
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
author: BrucePerlerMS
ms.openlocfilehash: 904916424c3ab199afd09a804c47b57a82e14158
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077730"
---
# <a name="message-security-user-name"></a><span data-ttu-id="41cb0-102">Zabezpečení zpráv s uživatelským jménem</span><span class="sxs-lookup"><span data-stu-id="41cb0-102">Message Security User Name</span></span>
<span data-ttu-id="41cb0-103">Tento příklad ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřením uživatelské jméno pro klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru.</span><span class="sxs-lookup"><span data-stu-id="41cb0-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="41cb0-104">Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="41cb0-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="41cb0-105">Ve výchozím nastavení, uživatelské jméno a heslo, které poskytl klient, slouží k přihlášení k platný účet Windows.</span><span class="sxs-lookup"><span data-stu-id="41cb0-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="41cb0-106">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="41cb0-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="41cb0-107">Tento příklad se skládá z programu konzoly klienta (Client.exe) a knihovna služby (Service.dll) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="41cb0-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="41cb0-108">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="41cb0-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41cb0-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="41cb0-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="41cb0-110">Tento příklad také znázorňuje:</span><span class="sxs-lookup"><span data-stu-id="41cb0-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="41cb0-111">Výchozí mapování na účty Windows tak, že lze provést další ověření.</span><span class="sxs-lookup"><span data-stu-id="41cb0-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="41cb0-112">Jak získat přístup k identity volajícího z kódu služby.</span><span class="sxs-lookup"><span data-stu-id="41cb0-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="41cb0-113">Služba poskytuje jeden koncový bod pro komunikaci se službou, která je definována je používán konfigurační soubor Web.config. Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="41cb0-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="41cb0-114">Je vazba konfigurována se standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), která ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="41cb0-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="41cb0-115">Tato ukázka nastaví standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="41cb0-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="41cb0-116">Chování Určuje, že má být použit pro ověřování služby jsou přihlašovací údaje uživatele.</span><span class="sxs-lookup"><span data-stu-id="41cb0-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="41cb0-117">Certifikát serveru musí obsahovat stejnou hodnotu pro název subjektu, jako `findValue` atribut [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="41cb0-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="41cb0-118">Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="41cb0-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="41cb0-119">Klient vazby je nakonfigurovaný s příslušnou `securityMode` a `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="41cb0-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="41cb0-120">Při spuštění ve scénáři mezi počítači, musíte změnit adresu koncového bodu služby odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="41cb0-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="41cb0-121">Implementace klienta nastaví uživatelské jméno a heslo pro použití.</span><span class="sxs-lookup"><span data-stu-id="41cb0-121">The client implementation sets the user name and password to use.</span></span>  

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

 <span data-ttu-id="41cb0-122">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="41cb0-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="41cb0-123">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="41cb0-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="41cb0-124">Dávkový soubor Setup.bat součástí ukázky MessageSecurity umožňuje nakonfigurovat server se příslušný certifikát ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="41cb0-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="41cb0-125">Dávkový soubor může běžet ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="41cb0-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="41cb0-126">Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="41cb0-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="41cb0-127">Ke spuštění v režimu typ služby `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="41cb0-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="41cb0-128">Tento režim se použijte při spuštění ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="41cb0-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="41cb0-129">Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="41cb0-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="41cb0-130">Následující body nabízí stručný přehled o různých částech dávkové soubory.</span><span class="sxs-lookup"><span data-stu-id="41cb0-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="41cb0-131">Vytváří se certifikát serveru</span><span class="sxs-lookup"><span data-stu-id="41cb0-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="41cb0-132">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="41cb0-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="41cb0-133">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="41cb0-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="41cb0-134">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="41cb0-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="41cb0-135">Pokud Setup.bat dávkový soubor se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="41cb0-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="41cb0-136">Jinak je výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="41cb0-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="41cb0-137">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta</span><span class="sxs-lookup"><span data-stu-id="41cb0-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="41cb0-138">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="41cb0-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="41cb0-139">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="41cb0-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="41cb0-140">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="41cb0-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="41cb0-141">Udělení oprávnění pro privátní klíč certifikátu</span><span class="sxs-lookup"><span data-stu-id="41cb0-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="41cb0-142">Následující řádky do dávkový soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="41cb0-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="41cb0-143">Pokud používáte mimo USA Anglickou verzi Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu se místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="41cb0-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41cb0-144">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="41cb0-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="41cb0-145">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41cb0-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="41cb0-146">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41cb0-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="41cb0-147">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="41cb0-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="41cb0-148">Ujistěte se, že cesta obsahuje složku, ve kterém jsou umístěny Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="41cb0-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="41cb0-149">Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="41cb0-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="41cb0-150">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="41cb0-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41cb0-151">Dávkový soubor Setup.bat slouží ke spuštění z příkazového řádku aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41cb0-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="41cb0-152">To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="41cb0-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="41cb0-153">Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41cb0-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="41cb0-154">Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="41cb0-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="41cb0-155">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="41cb0-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="41cb0-156">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="41cb0-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="41cb0-157">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="41cb0-157">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="41cb0-158">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="41cb0-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="41cb0-159">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="41cb0-159">Create a directory on the service computer.</span></span> <span data-ttu-id="41cb0-160">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby.</span><span class="sxs-lookup"><span data-stu-id="41cb0-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="41cb0-161">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="41cb0-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="41cb0-162">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="41cb0-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="41cb0-163">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="41cb0-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="41cb0-164">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="41cb0-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="41cb0-165">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="41cb0-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="41cb0-166">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="41cb0-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="41cb0-167">Na serveru, spusťte `setup.bat service` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="41cb0-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="41cb0-168">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="41cb0-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="41cb0-169">Upravit soubor Web.config tak, aby odrážely nový název certifikátu (u atributu findValue v aplikaci prvku serviceCertificate) která je stejná jako plně kvalifikovaný název domény počítače`.`</span><span class="sxs-lookup"><span data-stu-id="41cb0-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="41cb0-170">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="41cb0-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="41cb0-171">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="41cb0-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="41cb0-172">Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="41cb0-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="41cb0-173">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="41cb0-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="41cb0-174">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="41cb0-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="41cb0-175">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="41cb0-175">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="41cb0-176">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="41cb0-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="41cb0-177">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="41cb0-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41cb0-178">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="41cb0-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="41cb0-179">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="41cb0-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="41cb0-180">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="41cb0-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41cb0-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="41cb0-181">See Also</span></span>
