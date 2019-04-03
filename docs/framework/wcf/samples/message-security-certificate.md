---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 0e21f0acaf6c9bf0b0c7fc48648ad6a26876f9cb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826298"
---
# <a name="message-security-certificate"></a><span data-ttu-id="fd797-102">Certifikát zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="fd797-102">Message Security Certificate</span></span>
<span data-ttu-id="fd797-103">Tento příklad ukazuje, jak implementovat aplikaci, která používá WS-Security X.509 v3 s ověřováním pomocí certifikátu klienta a vyžaduje server ověřování pomocí certifikátu X.509 v3 na server.</span><span class="sxs-lookup"><span data-stu-id="fd797-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="fd797-104">Tato ukázka používá výchozí nastavení tak, že jsou všechny zprávy aplikace mezi klientem a serverem podepsaný a zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="fd797-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="fd797-105">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z programu konzoly klienta a knihovna služby hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="fd797-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="fd797-106">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="fd797-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd797-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="fd797-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fd797-108">Vzorek ukazuje řídicí ověřování pomocí konfigurace a jak získat identity volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="fd797-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

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
  
 <span data-ttu-id="fd797-109">Služba poskytuje jeden koncový bod pro komunikaci s službu a jeden koncový bod pro zveřejnění dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definované pomocí souboru konfigurace (Web.config).</span><span class="sxs-lookup"><span data-stu-id="fd797-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="fd797-110">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fd797-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="fd797-111">Je vazba konfigurována se standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, který ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="fd797-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="fd797-112">Tato ukázka nastaví `clientCredentialType` atributů k certifikátu tak, aby vyžadovala ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="fd797-113">Určuje chování služby přihlašovací údaje, které se používají při ověřování klienta služby.</span><span class="sxs-lookup"><span data-stu-id="fd797-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="fd797-114">Je zadaný název subjektu certifikátu serveru v `findValue` atribut [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fd797-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="fd797-115">Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fd797-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="fd797-116">Vazby klienta se nakonfigurují příslušná bezpečnostní režim a režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="fd797-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="fd797-117">Při spuštění v počítači různé scénáře, zajistěte, adresu koncového bodu služby je odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="fd797-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="fd797-118">Implementace klienta můžete nastavit certifikát, který chcete použít, buď pomocí konfiguračního souboru, nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="fd797-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="fd797-119">Následující příklad ukazuje, jak nastavit certifikát, který chcete použít v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="fd797-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="fd797-120">Následující příklad ukazuje, jak volat služby v programu.</span><span class="sxs-lookup"><span data-stu-id="fd797-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="fd797-121">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fd797-122">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="fd797-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="fd797-123">Dávkový soubor Setup.bat součástí Ukázky zabezpečení zpráv umožňuje nakonfigurovat příslušné certifikáty ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="fd797-124">Dávkový soubor můžete spustit v tří režimů.</span><span class="sxs-lookup"><span data-stu-id="fd797-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="fd797-125">Ke spuštění v režimu jednoho počítače typu **setup.bat** v příkazový řádek vývojáře pro sadu Visual Studio; pro typ služby režimu **setup.bat služby**; a pro typ režimu klienta **setup.bat klienta**.</span><span class="sxs-lookup"><span data-stu-id="fd797-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="fd797-126">Při spuštění ukázky mezi počítači, použije se režim klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="fd797-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="fd797-127">Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="fd797-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="fd797-128">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="fd797-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
-   <span data-ttu-id="fd797-129">Vytváří se certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="fd797-130">Následující řádek v dávkovém souboru vytvoří certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="fd797-131">Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili.</span><span class="sxs-lookup"><span data-stu-id="fd797-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="fd797-132">Certifikát je uložen v `My` ukládat na `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="fd797-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="fd797-133">Instalaci klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="fd797-134">Následující řádek v souboru kopie služby batch klientský certifikát do serveru TrustedPeople uložit tak, aby na serveru můžete provádět odpovídající vztah důvěryhodnosti nebo rozhodnutí o důvěryhodnosti č.</span><span class="sxs-lookup"><span data-stu-id="fd797-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="fd797-135">V objednávku na certifikát nainstalován v úložišti TrustedPeople pro důvěryhodného službou Windows Communication Foundation (WCF), musí být nastaven režim ověřování certifikátu klienta `PeerOrChainTrust` nebo `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="fd797-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="fd797-136">Viz předchozí ukázka konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fd797-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   <span data-ttu-id="fd797-137">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="fd797-138">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="fd797-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="fd797-139">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="fd797-140">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="fd797-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="fd797-141">Pokud Setup.bat dávkový soubor se spustí s parametrem služby (jako jsou například **setup.bat služby**) název_serveru % obsahuje název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="fd797-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="fd797-142">Jinak je výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="fd797-142">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="fd797-143">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="fd797-144">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="fd797-145">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="fd797-146">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="fd797-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="fd797-147">Udělení oprávnění pro privátní klíč certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fd797-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="fd797-148">Následující řádky do soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="fd797-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="fd797-149">Pokud používáte mimo USA Anglickou verzi Windows, je nutné pomocí úpravy Setup.bat soubor a nahradit místní ekvivalent názvu účtu "NT AUTHORITY\NETWORK SERVICE".</span><span class="sxs-lookup"><span data-stu-id="fd797-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd797-150">Nástroje používané v tomto souboru batch jsou umístěny v 8\Common7\tools C:\Program Files\Microsoft Visual Studio nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="fd797-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="fd797-151">Jeden z těchto adresářů musí být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="fd797-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="fd797-152">Pokud máte nainstalovanou sadu Visual Studio, otevřete příkazový řádek vývojáře pro sadu Visual Studio je nejjednodušší způsob, jak získat tento adresář v cestě.</span><span class="sxs-lookup"><span data-stu-id="fd797-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="fd797-153">Klikněte na tlačítko **Start**a pak vyberte **všechny programy**, **Visual Studio 2012**, **nástroje**.</span><span class="sxs-lookup"><span data-stu-id="fd797-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="fd797-154">Tento příkazový řádek obsahuje příslušné cesty, které jsou už nakonfigurovaná.</span><span class="sxs-lookup"><span data-stu-id="fd797-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="fd797-155">Jinak je nutné přidat do příslušného adresáře do cesty ručně.</span><span class="sxs-lookup"><span data-stu-id="fd797-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd797-156">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="fd797-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fd797-157">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="fd797-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fd797-158">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="fd797-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd797-159">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="fd797-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fd797-160">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="fd797-160">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fd797-161">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd797-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fd797-162">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd797-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="fd797-163">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="fd797-163">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="fd797-164">Otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="fd797-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="fd797-165">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="fd797-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd797-166">Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd797-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="fd797-167">To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="fd797-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="fd797-168">Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku pro vývojáře pro sadu Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="fd797-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2.  <span data-ttu-id="fd797-169">Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="fd797-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3.  <span data-ttu-id="fd797-170">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="fd797-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="fd797-171">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="fd797-171">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="fd797-172">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fd797-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="fd797-173">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="fd797-173">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="fd797-174">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="fd797-174">Create a directory on the service computer.</span></span> <span data-ttu-id="fd797-175">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="fd797-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="fd797-176">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="fd797-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="fd797-177">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="fd797-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="fd797-178">Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="fd797-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="fd797-179">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="fd797-180">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="fd797-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="fd797-181">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="fd797-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="fd797-182">Na serveru, spusťte **setup.bat služby** v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd797-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="fd797-183">Spuštění **setup.bat** s **služby** argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="fd797-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="fd797-184">Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="fd797-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="fd797-185">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="fd797-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="fd797-186">Na straně klienta, spouštění **setup.bat klienta** v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd797-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="fd797-187">Spuštění **setup.bat** s **klienta** argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="fd797-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="fd797-188">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="fd797-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="fd797-189">Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="fd797-190">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="fd797-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="fd797-191">Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd797-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="fd797-192">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="fd797-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="fd797-193">Na serveru spusťte ImportClientCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd797-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="fd797-194">To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="fd797-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="fd797-195">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fd797-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="fd797-196">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fd797-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fd797-197">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="fd797-197">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="fd797-198">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="fd797-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd797-199">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="fd797-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="fd797-200">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="fd797-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="fd797-201">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fd797-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
