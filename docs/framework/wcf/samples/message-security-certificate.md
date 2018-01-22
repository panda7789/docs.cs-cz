---
title: "Certifikát zabezpečení zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
caps.latest.revision: "51"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 9339258c4f5df606db9126c8b4b886b0a26029a6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-certificate"></a><span data-ttu-id="a4841-102">Certifikát zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="a4841-102">Message Security Certificate</span></span>
<span data-ttu-id="a4841-103">Tento příklad znázorňuje implementaci aplikace, která používá WS-zabezpečení X.509 v3 s ověřováním pomocí certifikátu pro klienta a vyžaduje ověření serveru pomocí serveru certifikát X.509 v3.</span><span class="sxs-lookup"><span data-stu-id="a4841-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="a4841-104">Tato ukázka používá výchozí nastavení tak, aby všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="a4841-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="a4841-105">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z konzoly programu klienta knihovnu služby hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="a4841-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a4841-106">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a4841-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4841-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a4841-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a4841-108">Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a4841-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  
  
```  
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="a4841-109">Službu zpřístupní jeden koncový bod pro komunikaci s službu a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definované za použití konfiguračního souboru (Web.config).</span><span class="sxs-lookup"><span data-stu-id="a4841-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="a4841-110">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a4841-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a4841-111">Vazba je nakonfigurována s standard [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, který ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="a4841-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="a4841-112">Tato ukázka se nastaví `clientCredentialType` atribut certifikát tak, aby vyžadovala ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="a4841-113">Chování Určuje přihlašovací údaje služby, které se používají, když klient se ověří službu.</span><span class="sxs-lookup"><span data-stu-id="a4841-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="a4841-114">Název subjektu certifikátu serveru je zadán v `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span><span class="sxs-lookup"><span data-stu-id="a4841-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="a4841-115">Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a4841-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="a4841-116">Klient pro vazby nastavena příslušná bezpečnostní režim a režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="a4841-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="a4841-117">Při spuštění ve scénáři mezi počítači, ujistěte se, že adresa koncového bodu služby se změní odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a4841-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a4841-118">Implementace klienta můžete nastavit certifikát, který chcete použít, prostřednictvím konfiguračního souboru nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="a4841-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="a4841-119">Následující příklad ukazuje, jak nastavit certifikát, který chcete použít v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a4841-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a4841-120">Následující příklad ukazuje způsob volání služby v programu.</span><span class="sxs-lookup"><span data-stu-id="a4841-120">The following sample shows how to call the service in your program.</span></span>  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="a4841-121">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a4841-122">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="a4841-123">Dávkový soubor Setup.bat součástí Ukázky zabezpečení zpráv umožňuje nakonfigurovat příslušné certifikáty spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="a4841-124">Dávkový soubor se může spouštět ve tři režimy.</span><span class="sxs-lookup"><span data-stu-id="a4841-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="a4841-125">Ke spuštění v režimu jednoho počítače typu **setup.bat** v Visual Studio – příkazový řádek; pro typ služby režimu **setup.bat služby**; a pro typ režimu klienta **setup.bat klienta** .</span><span class="sxs-lookup"><span data-stu-id="a4841-125">To run in single-computer mode type **setup.bat** in a Visual Studio Command Prompt ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="a4841-126">Režim klienta a serveru použijte při spuštění ukázky pro počítače.</span><span class="sxs-lookup"><span data-stu-id="a4841-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="a4841-127">Přečtěte si postup instalace na konci tohoto tématu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="a4841-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="a4841-128">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="a4841-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
-   <span data-ttu-id="a4841-129">Vytvoření certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="a4841-130">Následující řádek v dávkovém souboru, vytvoří certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="a4841-131">Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a4841-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="a4841-132">Certifikát je uložen v `My` uložit na `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="a4841-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="a4841-133">Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="a4841-134">Následující řádek v kopie souborů batch certifikát klienta do serveru TrustedPeople úložiště tak, aby server můžete provést příslušné důvěryhodnosti nebo ne důvěryhodnosti rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="a4841-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="a4841-135">V pořadí pro certifikát nainstalovaný v úložišti TrustedPeople být důvěryhodný [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, režim ověření certifikátu klienta musí být nastavená na `PeerOrChainTrust` nebo `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="a4841-135">In order for a certificate installed in the TrustedPeople store to be trusted by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="a4841-136">Viz předchozí ukázka konfigurace služby se dozvíte, jak to můžete provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a4841-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   <span data-ttu-id="a4841-137">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="a4841-138">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a4841-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="a4841-139">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="a4841-140">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a4841-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="a4841-141">Pokud dávkový soubor Setup.bat spuštění s argumentem služby (například **setup.bat služby**) název_serveru % obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="a4841-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a4841-142">V opačném případě bude výchozí localhost.</span><span class="sxs-lookup"><span data-stu-id="a4841-142">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="a4841-143">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="a4841-144">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a4841-145">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a4841-146">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="a4841-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="a4841-147">Udělení oprávnění pro privátní klíč certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a4841-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="a4841-148">Zkontrolujte následující řádky v souboru Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="a4841-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="a4841-149">Pokud používáte jiný USA Anglickou verzi systému Windows, je nutné upravit Setup.bat souboru a název účtu "Služba NT AUTHORITY\NETWORK" nahraďte vaše místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="a4841-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4841-150">Nástroje používané v tomto souboru batch jsou umístěny v sadě Visual Studio C:\Program Files\Microsoft 8\Common7\tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="a4841-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="a4841-151">Jedna z těchto adresářů musí být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="a4841-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="a4841-152">Pokud máte nainstalovanou sadu Visual Studio, otevřete příkazový řádek sady Visual Studio je nejjednodušší způsob, jak získat tento adresář v cestě.</span><span class="sxs-lookup"><span data-stu-id="a4841-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Visual Studio Command Prompt.</span></span> <span data-ttu-id="a4841-153">Klikněte na tlačítko **spustit**a potom vyberte **všechny programy**, **Visual Studio 2012**, **nástroje**.</span><span class="sxs-lookup"><span data-stu-id="a4841-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="a4841-154">Tento příkaz má odpovídající cesty již nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="a4841-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="a4841-155">V opačném případě je nutné přidat do příslušného adresáře pro vaši cestu ručně.</span><span class="sxs-lookup"><span data-stu-id="a4841-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4841-156">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a4841-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a4841-157">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="a4841-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a4841-158">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a4841-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4841-159">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="a4841-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4841-160">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="a4841-160">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a4841-161">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4841-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a4841-162">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4841-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a4841-163">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="a4841-163">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="a4841-164">Otevřete příkazový řádek Visual Studio s oprávněními správce a spusťte Setup.bat z ukázkové složky instalace.</span><span class="sxs-lookup"><span data-stu-id="a4841-164">Open a Visual Studio Command Prompt  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="a4841-165">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="a4841-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4841-166">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio – příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="a4841-166">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt .</span></span> <span data-ttu-id="a4841-167">To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="a4841-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a4841-168">Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio – příkazový řádek (2010).</span><span class="sxs-lookup"><span data-stu-id="a4841-168">This environment variable is automatically set within a Visual Studio Command Prompt (2010).</span></span>  
  
2.  <span data-ttu-id="a4841-169">Ověřte přístup ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="a4841-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3.  <span data-ttu-id="a4841-170">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="a4841-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a4841-171">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="a4841-171">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="a4841-172">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a4841-172">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a4841-173">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="a4841-173">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a4841-174">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="a4841-174">Create a directory on the service computer.</span></span> <span data-ttu-id="a4841-175">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="a4841-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="a4841-176">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="a4841-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="a4841-177">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="a4841-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="a4841-178">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="a4841-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="a4841-179">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="a4841-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="a4841-180">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="a4841-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="a4841-181">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="a4841-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="a4841-182">Na serveru, spusťte **setup.bat služby** v sadě Visual Studio příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4841-182">On the server, run **setup.bat service** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="a4841-183">Spuštění **setup.bat** s **služby** argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="a4841-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="a4841-184">Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="a4841-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="a4841-185">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="a4841-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="a4841-186">Na klientovi, spusťte **setup.bat klienta** v sadě Visual Studio příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4841-186">On the client, run **setup.bat client** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="a4841-187">Spuštění **setup.bat** s **klienta** argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="a4841-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="a4841-188">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="a4841-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="a4841-189">To nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="a4841-190">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="a4841-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="a4841-191">Na klientovi spusťte ImportServiceCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4841-191">On the client, run ImportServiceCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="a4841-192">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="a4841-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="a4841-193">Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4841-193">On the server, run ImportClientCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="a4841-194">Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="a4841-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="a4841-195">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a4841-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="a4841-196">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a4841-196">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a4841-197">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="a4841-197">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="a4841-198">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="a4841-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4841-199">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="a4841-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="a4841-200">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="a4841-200">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="a4841-201">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="a4841-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4841-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4841-202">See Also</span></span>
