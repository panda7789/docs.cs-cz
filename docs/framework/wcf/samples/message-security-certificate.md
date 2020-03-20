---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183538"
---
# <a name="message-security-certificate"></a><span data-ttu-id="838a6-102">Certifikát zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="838a6-102">Message Security Certificate</span></span>
<span data-ttu-id="838a6-103">Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátu X.509 v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509 v3 serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="838a6-104">Tato ukázka používá výchozí nastavení tak, aby všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány.</span><span class="sxs-lookup"><span data-stu-id="838a6-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="838a6-105">Tato ukázka je založena na [wshttpbinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z programu konzoly klienta a knihovny služeb hostované Internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="838a6-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="838a6-106">Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="838a6-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="838a6-107">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="838a6-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="838a6-108">Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="838a6-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

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
  
 <span data-ttu-id="838a6-109">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definovaného pomocí konfiguračního souboru (Web.config).</span><span class="sxs-lookup"><span data-stu-id="838a6-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="838a6-110">Koncový bod se skládá z adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="838a6-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="838a6-111">Vazba je nakonfigurována se standardním [ \<prvkem wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) který ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="838a6-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="838a6-112">Tato ukázka `clientCredentialType` nastaví atribut na certifikát tak, aby vyžadoval ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="838a6-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="838a6-113">Chování určuje pověření služby, které se používají při ověření služby klientem.</span><span class="sxs-lookup"><span data-stu-id="838a6-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="838a6-114">Název subjektu certifikátu serveru `findValue` je určen v atributu v elementu [ \<serviceCredentials>.](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="838a6-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="838a6-115">Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu.</span><span class="sxs-lookup"><span data-stu-id="838a6-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="838a6-116">Vazba klienta je konfigurována s příslušným režimem zabezpečení a režimem ověřování.</span><span class="sxs-lookup"><span data-stu-id="838a6-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="838a6-117">Při spuštění ve scénáři mezi počítači se ujistěte, že je odpovídajícím způsobem změněna adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="838a6-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="838a6-118">Implementace klienta můžete nastavit certifikát použít, a to buď prostřednictvím konfiguračního souboru nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="838a6-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="838a6-119">Následující ukázka ukazuje, jak nastavit certifikát pro použití v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="838a6-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="838a6-120">Následující ukázka ukazuje, jak volat službu v programu.</span><span class="sxs-lookup"><span data-stu-id="838a6-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="838a6-121">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="838a6-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="838a6-122">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="838a6-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="838a6-123">Dávkový soubor Setup.bat, který je součástí ukázek Zabezpečení zpráv, umožňuje nakonfigurovat klienta a server s příslušnými certifikáty tak, aby spouštěly hostovnu, která vyžaduje zabezpečení založené na certifikátu.</span><span class="sxs-lookup"><span data-stu-id="838a6-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="838a6-124">Dávkový soubor lze spustit ve třech režimech.</span><span class="sxs-lookup"><span data-stu-id="838a6-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="838a6-125">Chcete-li spustit v režimu jednoho počítače, zadejte **setup.bat** v příkazovém řádku pro vývojáře pro sady Visual Studio ; pro službu typu service type **setup.bat**; a pro klientský režim typu **setup.bat klienta**.</span><span class="sxs-lookup"><span data-stu-id="838a6-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="838a6-126">Při spuštění ukázky v počítačích použijte režim klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="838a6-127">Podrobnosti naleznete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="838a6-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="838a6-128">Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v odpovídající konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="838a6-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="838a6-129">Vytvoření klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="838a6-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="838a6-130">Následující řádek v dávkovém souboru vytvoří klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="838a6-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="838a6-131">Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="838a6-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="838a6-132">Certifikát je uložen `My` v `CurrentUser` úložišti v umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="838a6-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="838a6-133">Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="838a6-134">Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl činit příslušná rozhodnutí o důvěryhodnosti nebo nedůvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="838a6-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="838a6-135">Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou WCF (Windows Communication Foundation), musí `PeerOrChainTrust` `PeerTrust`být režim ověření klientského certifikátu nastaven na nebo .</span><span class="sxs-lookup"><span data-stu-id="838a6-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="838a6-136">Podívejte se na předchozí ukázku konfigurace služby, kde se dozvíte, jak toho lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="838a6-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- <span data-ttu-id="838a6-137">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="838a6-138">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="838a6-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="838a6-139">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="838a6-140">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="838a6-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="838a6-141">Pokud je dávkový soubor Setup.bat spuštěn s argumentem služby (například **služba setup.bat),** obsahuje %SERVER_NAME% plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="838a6-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="838a6-142">V opačném případě je výchozí localhost.</span><span class="sxs-lookup"><span data-stu-id="838a6-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="838a6-143">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="838a6-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="838a6-144">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="838a6-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="838a6-145">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="838a6-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="838a6-146">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="838a6-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="838a6-147">Udělení oprávnění k soukromému klíči certifikátu.</span><span class="sxs-lookup"><span data-stu-id="838a6-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="838a6-148">Následující řádky v souboru Setup.bat zpřístupní certifikát serveru uložený v úložišti LocalMachine ASP.NET účtu pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="838a6-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="838a6-149">Pokud používáte edici systému Windows, která není v USA, je nutné upravit soubor Setup.bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE místním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="838a6-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="838a6-150">Nástroje použité v tomto dávkovém souboru jsou umístěny buď v souborech C:\Program Files\Microsoft Visual Studio 8\Common7\Tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="838a6-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="838a6-151">Jeden z těchto adresářů musí být v cestě systému.</span><span class="sxs-lookup"><span data-stu-id="838a6-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="838a6-152">Pokud máte nainstalovanou aplikaci Visual Studio, nejjednodušší způsob, jak tento adresář získat do cesty, je otevřít příkazový řádek pro vývojáře pro sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="838a6-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="838a6-153">Klepněte na tlačítko **Start**a vyberte možnost **Všechny programy**, **Visual Studio 2012**, **Nástroje**.</span><span class="sxs-lookup"><span data-stu-id="838a6-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="838a6-154">Tento příkazový řádek má již nakonfigurované příslušné cesty.</span><span class="sxs-lookup"><span data-stu-id="838a6-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="838a6-155">V opačném případě je nutné přidat příslušný adresář do cesty ručně.</span><span class="sxs-lookup"><span data-stu-id="838a6-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="838a6-156">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="838a6-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="838a6-157">Před pokračováním zkontrolujte následující (výchozí) adresář:</span><span class="sxs-lookup"><span data-stu-id="838a6-157">Check for the following (default) directory before continuing:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="838a6-158">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="838a6-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="838a6-159">Tato ukázka je umístěna v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="838a6-159">This sample is located in the following directory:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="838a6-160">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="838a6-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="838a6-161">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838a6-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="838a6-162">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838a6-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="838a6-163">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="838a6-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="838a6-164">Otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor Setup.bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="838a6-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="838a6-165">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="838a6-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="838a6-166">Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="838a6-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="838a6-167">Vyžaduje, aby proměnná prostředí cesty přecškovala do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="838a6-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="838a6-168">Tato proměnná prostředí je automaticky nastavena v rámci příkazového řádku pro vývojáře pro sadu Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="838a6-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="838a6-169">Ověřte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním adresy .</span><span class="sxs-lookup"><span data-stu-id="838a6-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="838a6-170">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="838a6-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="838a6-171">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="838a6-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="838a6-172">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="838a6-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="838a6-173">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="838a6-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="838a6-174">Vytvořte adresář v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="838a6-174">Create a directory on the service computer.</span></span> <span data-ttu-id="838a6-175">Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="838a6-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="838a6-176">Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="838a6-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="838a6-177">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="838a6-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="838a6-178">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportClientCert.bat do servisního počítače.</span><span class="sxs-lookup"><span data-stu-id="838a6-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="838a6-179">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="838a6-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="838a6-180">Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="838a6-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="838a6-181">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="838a6-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="838a6-182">Na serveru spusťte **službu setup.bat** v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="838a6-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="838a6-183">**Spuštěnísouboru setup.bat** s argumentem **služby** vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="838a6-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="838a6-184">Upravte web.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="838a6-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="838a6-185">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="838a6-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="838a6-186">V klientovi klienta **setup.bat** spusťte v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="838a6-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="838a6-187">**Spuštěnísouboru setup.bat** s argumentem **klienta** vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="838a6-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="838a6-188">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="838a6-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="838a6-189">To provést nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="838a6-190">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="838a6-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="838a6-191">Na straně klienta spusťte soubor ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="838a6-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="838a6-192">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="838a6-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="838a6-193">Na serveru spusťte soubor ImportClientCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="838a6-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="838a6-194">Tím se klientský certifikát importuje ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="838a6-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="838a6-195">V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="838a6-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="838a6-196">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="838a6-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="838a6-197">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="838a6-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="838a6-198">Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="838a6-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="838a6-199">Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="838a6-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="838a6-200">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="838a6-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="838a6-201">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .</span><span class="sxs-lookup"><span data-stu-id="838a6-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
