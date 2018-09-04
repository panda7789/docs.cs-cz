---
title: Validátor certifikátu X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: e54f79046113e5f1a1a1cc065606fd5b706b49ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533506"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="03cf8-102">Validátor certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="03cf8-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="03cf8-103">Tento příklad ukazuje, jak implementovat vlastní validátor certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="03cf8-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="03cf8-104">To je užitečné v případech, kdy je vhodné pro požadavky na aplikace žádná z předdefinovaných režimy ověřování certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="03cf8-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="03cf8-105">Tento příklad ukazuje služba, která má vlastní validátor, který přijímá samostatně vydané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="03cf8-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="03cf8-106">Klient používá tento certifikát k ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="03cf8-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="03cf8-107">Poznámka: jako kdokoli může vytvořit certifikát vystavený je méně bezpečné než výchozí chování poskytované ChainTrust X509CertificateValidationMode vlastní validátor používané službou.</span><span class="sxs-lookup"><span data-stu-id="03cf8-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="03cf8-108">Důsledky zabezpečení tohoto objektu je třeba pečlivě zvážit před použitím této logiky ověřování v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="03cf8-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="03cf8-109">V souhrnu Tato ukázka předvádí, jak:</span><span class="sxs-lookup"><span data-stu-id="03cf8-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="03cf8-110">Klient lze ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="03cf8-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="03cf8-111">Server ověří klienta přihlašovacích údajů, kteří vlastní X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="03cf8-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="03cf8-112">Server byl ověřovaný pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="03cf8-113">Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="03cf8-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="03cf8-114">Je vazba konfigurována se standardní `wsHttpBinding` , která ve výchozím nastavení používá `WSSecurity` a ověření klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="03cf8-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="03cf8-115">Chování služby určuje vlastní režim ověřování klientských certifikátů X.509 spolu s typem třídy program pro ověření.</span><span class="sxs-lookup"><span data-stu-id="03cf8-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="03cf8-116">Chování také Určuje certifikát serveru pomocí serviceCertificate elementu.</span><span class="sxs-lookup"><span data-stu-id="03cf8-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="03cf8-117">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="03cf8-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 <span data-ttu-id="03cf8-118">Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="03cf8-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="03cf8-119">Klient vazby je nakonfigurován příslušný režim, zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="03cf8-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="03cf8-120">Implementace klienta nastaví klientský certifikát k použití.</span><span class="sxs-lookup"><span data-stu-id="03cf8-120">The client implementation sets the client certificate to use.</span></span>  
  
```csharp
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="03cf8-121">Tato ukázka používá vlastní X509CertificateValidator ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="03cf8-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="03cf8-122">Ukázka implementuje CustomX509CertificateValidator odvozený od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="03cf8-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="03cf8-123">Najdete v dokumentaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> Další informace.</span><span class="sxs-lookup"><span data-stu-id="03cf8-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="03cf8-124">Tato ukázka konkrétní vlastní validátor implementuje metodu Validate tak, aby přijímal libovolný certifikát X.509, která je držitelem vydala, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="03cf8-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```csharp
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 <span data-ttu-id="03cf8-125">Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="03cf8-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="03cf8-126">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="03cf8-126">This is done using the following code.</span></span>  
  
```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="03cf8-127">Nebo můžete provést totéž v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="03cf8-127">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="03cf8-128">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="03cf8-129">Klient úspěšně by měly volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="03cf8-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="03cf8-130">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="03cf8-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="03cf8-131">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="03cf8-131">Setup Batch File</span></span>  
 <span data-ttu-id="03cf8-132">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="03cf8-133">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="03cf8-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="03cf8-134">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="03cf8-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="03cf8-135">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="03cf8-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="03cf8-136">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="03cf8-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="03cf8-137">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="03cf8-138">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="03cf8-139">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="03cf8-139">The default value is localhost.</span></span>  
  
    ```bash  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="03cf8-140">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="03cf8-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="03cf8-141">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="03cf8-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="03cf8-142">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="03cf8-143">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="03cf8-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="03cf8-144">Vytváří se certifikát klienta:</span><span class="sxs-lookup"><span data-stu-id="03cf8-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="03cf8-145">Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="03cf8-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="03cf8-146">% Proměnná % uživatelské_jméno Určuje název klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="03cf8-147">Tato hodnota nastavená na "test1", protože jde o název, který hledá kód klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="03cf8-148">Pokud změníte hodnotu % uživatelské_jméno musíte změnit odpovídající hodnotu ve zdrojovém souboru Client.cs a znovu sestavte klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="03cf8-149">Certifikát je uložen v úložišti (osobních) v části CurrentUser umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="03cf8-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="03cf8-150">Instalaci klientského certifikátu do úložiště důvěryhodných certifikátů serveru:</span><span class="sxs-lookup"><span data-stu-id="03cf8-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="03cf8-151">Následující řádky do dávkový soubor Setup.bat zkopírujte klientský certifikát do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="03cf8-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="03cf8-152">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje serverového systému.</span><span class="sxs-lookup"><span data-stu-id="03cf8-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="03cf8-153">Pokud už máte certifikát, který je integrován v důvěryhodných kořenových certifikátů – například certifikátů vystavených Microsoftem – v tomto kroku naplnění úložiště certifikátů serveru pomocí certifikátu klienta se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="03cf8-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="03cf8-154">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="03cf8-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="03cf8-155">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03cf8-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="03cf8-156">Ke spuštění ukázky v jedním - nebo mezi computerconfiguration, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="03cf8-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="03cf8-157">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="03cf8-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="03cf8-158">Spustit Setup.bat z instalační složky Ukázky uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="03cf8-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="03cf8-159">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="03cf8-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="03cf8-160">Dávkový soubor Setup.bat slouží ke spuštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03cf8-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="03cf8-161">Nastavte proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="03cf8-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="03cf8-162">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="03cf8-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="03cf8-163">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="03cf8-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="03cf8-164">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="03cf8-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="03cf8-165">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="03cf8-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="03cf8-166">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="03cf8-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="03cf8-167">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="03cf8-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="03cf8-168">Zkopírujte soubory programu služby z \service\bin do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="03cf8-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="03cf8-169">Také kopírovat soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="03cf8-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="03cf8-170">Vytvoření adresáře na klienta počítačeDalší binárních souborů klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="03cf8-171">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="03cf8-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="03cf8-172">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="03cf8-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="03cf8-173">Na serveru, spusťte `setup.bat service` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="03cf8-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="03cf8-174">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se název plně kvalifikované domény exporty computerand certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="03cf8-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="03cf8-175">Upravit Service.exe.config tak, aby odrážely nový název certifikátu (v `findValue` atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="03cf8-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="03cf8-176">Také změnit název počítače \<služby > /\<baseAddresses > element z místního hostitele, plně kvalifikovaný název počítače služby.</span><span class="sxs-lookup"><span data-stu-id="03cf8-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="03cf8-177">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="03cf8-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="03cf8-178">Na straně klienta, spouštění `setup.bat client` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="03cf8-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="03cf8-179">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="03cf8-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="03cf8-180">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="03cf8-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="03cf8-181">Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="03cf8-182">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="03cf8-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="03cf8-183">Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="03cf8-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="03cf8-184">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="03cf8-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="03cf8-185">Na serveru spusťte ImportClientCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="03cf8-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="03cf8-186">To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="03cf8-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="03cf8-187">Na počítači serveru spusťte Service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03cf8-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="03cf8-188">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03cf8-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="03cf8-189">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="03cf8-189">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="03cf8-190">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="03cf8-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="03cf8-191">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="03cf8-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="03cf8-192">Tím serverových a klientských certifikátů z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="03cf8-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03cf8-193">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="03cf8-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="03cf8-194">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="03cf8-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="03cf8-195">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="03cf8-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03cf8-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="03cf8-196">See Also</span></span>
