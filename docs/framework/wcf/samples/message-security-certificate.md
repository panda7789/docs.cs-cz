---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 496589a0c1a5a0a029e464bfdd87caf8515bb9e3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044871"
---
# <a name="message-security-certificate"></a><span data-ttu-id="d1baf-102">Certifikát zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="d1baf-102">Message Security Certificate</span></span>
<span data-ttu-id="d1baf-103">Tato ukázka předvádí, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátů X. 509 v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X. 509 v3 serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="d1baf-104">Tato ukázka používá výchozí nastavení, aby všechny zprávy aplikací mezi klientem a serverem byly podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="d1baf-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="d1baf-105">Tato ukázka je založená na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z klientského konzolového programu a knihovny služeb hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d1baf-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d1baf-106">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="d1baf-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1baf-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d1baf-108">Ukázka znázorňuje řízení ověřování pomocí konfigurace a způsobu získání identity volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
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
  
 <span data-ttu-id="d1baf-109">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, který je definován pomocí konfiguračního souboru (Web. config).</span><span class="sxs-lookup"><span data-stu-id="d1baf-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="d1baf-110">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="d1baf-111">Vazba je nakonfigurována pomocí standardního [ \<prvku WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , který se standardně používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="d1baf-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="d1baf-112">Tato ukázka nastaví `clientCredentialType` atribut na certifikát, aby vyžadoval ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="d1baf-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="d1baf-113">Chování určuje přihlašovací údaje služby, které se používají, když klient ověřuje službu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="d1baf-114">Název subjektu certifikátu serveru je zadán v `findValue` atributu [ \<v elementu ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="d1baf-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="d1baf-115">Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="d1baf-116">Vazba klienta je nakonfigurovaná s příslušným režimem zabezpečení a režimem ověřování.</span><span class="sxs-lookup"><span data-stu-id="d1baf-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="d1baf-117">Pokud používáte scénář pro různé počítače, ujistěte se, že se adresa koncového bodu služby odpovídajícím způsobem změnila.</span><span class="sxs-lookup"><span data-stu-id="d1baf-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="d1baf-118">Implementace klienta může použít certifikát k použití, a to buď prostřednictvím konfiguračního souboru, nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="d1baf-119">Následující příklad ukazuje, jak nastavit certifikát pro použití v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d1baf-120">Následující příklad ukazuje, jak volat službu v programu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="d1baf-121">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d1baf-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d1baf-122">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="d1baf-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="d1baf-123">Dávkový soubor Setup. bat, který je součástí ukázek zabezpečení zpráv, vám umožní nakonfigurovat klienta a server s relevantními certifikáty pro spuštění hostované aplikace, která vyžaduje zabezpečení založené na certifikátech.</span><span class="sxs-lookup"><span data-stu-id="d1baf-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="d1baf-124">Dávkový soubor lze spustit ve třech režimech.</span><span class="sxs-lookup"><span data-stu-id="d1baf-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="d1baf-125">Spuštění v režimu jednoho počítače **Setup. bat** v Developer Command Prompt pro Visual Studio; pro typ Service Mode **Setup. bat service**; a v režimu klienta typ **instalace klient. bat**.</span><span class="sxs-lookup"><span data-stu-id="d1baf-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="d1baf-126">Při spuštění ukázky mezi počítači použijte režim klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="d1baf-127">Podrobnosti najdete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="d1baf-128">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="d1baf-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="d1baf-129">Vytváří se klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="d1baf-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="d1baf-130">Následující řádek v dávkovém souboru vytvoří klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="d1baf-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="d1baf-131">Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="d1baf-132">Certifikát je uložený v `My` úložišti `CurrentUser` v umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="d1baf-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="d1baf-133">Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="d1baf-134">Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl učinit příslušná rozhodnutí týkající se vztahu důvěryhodnosti nebo bez vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="d1baf-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="d1baf-135">Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou Windows Communication Foundation (WCF), musí být režim ověřování klientského certifikátu nastaven na `PeerOrChainTrust` nebo. `PeerTrust`</span><span class="sxs-lookup"><span data-stu-id="d1baf-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="d1baf-136">V předchozí ukázce konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- <span data-ttu-id="d1baf-137">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="d1baf-138">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d1baf-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="d1baf-139">Proměnná% Název_serveru% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="d1baf-140">Certifikát je uložený v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="d1baf-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="d1baf-141">Pokud se dávkový soubor Setup. bat spustí s argumentem služby (například **Instalační služba. bat**),% název_serveru% obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="d1baf-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="d1baf-142">V opačném případě se použije jako localhost.</span><span class="sxs-lookup"><span data-stu-id="d1baf-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="d1baf-143">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="d1baf-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="d1baf-144">Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="d1baf-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="d1baf-145">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="d1baf-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="d1baf-146">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="d1baf-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="d1baf-147">Udělení oprávnění k privátnímu klíči certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d1baf-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="d1baf-148">Následující řádky v souboru Setup. bat zpřístupní certifikát serveru, který je uložený v úložišti LocalMachine, přístupný pro účet pracovního procesu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1baf-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="d1baf-149">Pokud používáte jinou než U. S. Anglická edice systému Windows, je nutné upravit soubor Setup. bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE svým regionálním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="d1baf-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1baf-150">Nástroje používané v tomto dávkovém souboru jsou umístěné ve složce C:\Program Files\Microsoft Visual Studio 8 \ Common7\tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="d1baf-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="d1baf-151">Jeden z těchto adresářů musí být ve vaší systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="d1baf-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="d1baf-152">Pokud máte nainstalovanou aplikaci Visual Studio, nejjednodušší způsob, jak získat tento adresář ve vaší cestě, je otevřít Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1baf-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="d1baf-153">Klikněte na tlačítko **Start**a potom na položku **všechny programy**, **Visual Studio 2012**, **nástroje**.</span><span class="sxs-lookup"><span data-stu-id="d1baf-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="d1baf-154">Tento příkazový řádek má již nakonfigurovanou odpovídající cesty.</span><span class="sxs-lookup"><span data-stu-id="d1baf-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="d1baf-155">V opačném případě musíte do cesty ručně přidat příslušný adresář.</span><span class="sxs-lookup"><span data-stu-id="d1baf-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1baf-156">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d1baf-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d1baf-157">Než budete pokračovat, vyhledejte následující (výchozí) adresář:</span><span class="sxs-lookup"><span data-stu-id="d1baf-157">Check for the following (default) directory before continuing:</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d1baf-158">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="d1baf-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1baf-159">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="d1baf-159">This sample is located in the following directory:</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d1baf-160">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d1baf-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d1baf-161">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1baf-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d1baf-162">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1baf-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d1baf-163">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="d1baf-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="d1baf-164">Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="d1baf-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d1baf-165">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="d1baf-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1baf-166">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1baf-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="d1baf-167">Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="d1baf-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="d1baf-168">Tato proměnná prostředí se automaticky nastaví v rámci Developer Command Prompt pro Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="d1baf-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="d1baf-169">Zadáním adresy `http://localhost/servicemodelsamples/service.svc`ověřte přístup ke službě pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="d1baf-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="d1baf-170">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="d1baf-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="d1baf-171">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="d1baf-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="d1baf-172">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d1baf-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d1baf-173">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="d1baf-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="d1baf-174">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="d1baf-174">Create a directory on the service computer.</span></span> <span data-ttu-id="d1baf-175">Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d1baf-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="d1baf-176">Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="d1baf-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="d1baf-177">Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="d1baf-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="d1baf-178">Zkopírujte také soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="d1baf-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="d1baf-179">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="d1baf-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="d1baf-180">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="d1baf-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="d1baf-181">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="d1baf-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="d1baf-182">Na serveru spusťte ve Developer Command Prompt pro Visual Studio **službu Setup. bat** s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="d1baf-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="d1baf-183">Spuštění souboru **Setup. bat** s argumentem **Služba** vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="d1baf-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="d1baf-184">Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="d1baf-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="d1baf-185">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="d1baf-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="d1baf-186">Na straně klienta spusťte **klienta Setup. bat** v Developer Command Prompt pro Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="d1baf-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="d1baf-187">Spuštěním souboru **Setup. bat** s argumentem **klienta** se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.</span><span class="sxs-lookup"><span data-stu-id="d1baf-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="d1baf-188">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="d1baf-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="d1baf-189">Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="d1baf-190">Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="d1baf-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="d1baf-191">Na straně klienta spusťte ImportServiceCert. bat v Developer Command Prompt pro Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="d1baf-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="d1baf-192">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d1baf-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="d1baf-193">Na serveru spusťte ImportClientCert. bat v Developer Command Prompt pro Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="d1baf-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="d1baf-194">Tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d1baf-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="d1baf-195">V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d1baf-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="d1baf-196">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d1baf-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d1baf-197">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="d1baf-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d1baf-198">Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.</span><span class="sxs-lookup"><span data-stu-id="d1baf-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1baf-199">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="d1baf-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="d1baf-200">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d1baf-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d1baf-201">K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="d1baf-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
