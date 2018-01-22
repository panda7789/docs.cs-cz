---
title: "Validátor certifikátu X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08ccbbf50db089841d2af2205c7a7cb289a8767c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="8ef49-102">Validátor certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="8ef49-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="8ef49-103">Tento příklad ukazuje, jak implementovat vlastní validátor certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="8ef49-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="8ef49-104">To je užitečné v případech, kdy se jeden z režimů integrované ověření certifikátu X.509 je vhodné pro požadavky na aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ef49-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="8ef49-105">Tento příklad ukazuje služba, která má vlastní validátor, který přijímá samoobslužné vydaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8ef49-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="8ef49-106">Klient používá tento certifikát k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="8ef49-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="8ef49-107">Poznámka: jako každý, kdo může vytvořit certifikát vystavený vlastní validátor používá služba je méně bezpečné než výchozí chování poskytované ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="8ef49-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="8ef49-108">Zabezpečení důsledky tohoto objektu je třeba pečlivě zvážit před použitím této logiku ověření v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="8ef49-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="8ef49-109">V souhrnu tento příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="8ef49-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="8ef49-110">Klienta můžete ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="8ef49-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="8ef49-111">Server ověřuje pověření klienta proti vlastní X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="8ef49-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="8ef49-112">Server byl ověřovaný pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="8ef49-113">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8ef49-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="8ef49-114">Vazba je nakonfigurována s standard `wsHttpBinding` který ve výchozím nastavení používá `WSSecurity` a ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="8ef49-115">Chování služby určuje vlastní režim pro ověřování klientských certifikátů X.509 společně s typ validátoru třídu.</span><span class="sxs-lookup"><span data-stu-id="8ef49-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="8ef49-116">Chování určuje také pomocí elementu serviceCertificate certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="8ef49-117">Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="8ef49-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="8ef49-118">Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8ef49-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="8ef49-119">Klient vazba je konfigurován s odpovídající režim a zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="8ef49-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="8ef49-120">Implementace klienta nastaví certifikát klienta, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="8ef49-120">The client implementation sets the client certificate to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="8ef49-121">Tato ukázka používá vlastní X509CertificateValidator k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8ef49-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="8ef49-122">Ukázka implementuje CustomX509CertificateValidator, odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="8ef49-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="8ef49-123">Naleznete v dokumentaci k <xref:System.IdentityModel.Selectors.X509CertificateValidator> Další informace.</span><span class="sxs-lookup"><span data-stu-id="8ef49-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="8ef49-124">Tato ukázka konkrétní vlastní validátor implementuje metodu Validate tak, aby přijímal všechny certifikátu X.509, který je vydán samoobslužné, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8ef49-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="8ef49-125">Po validátor je implementovaná v kódu služby, hostitele služby musí být informováni o instanci program pro ověření používat.</span><span class="sxs-lookup"><span data-stu-id="8ef49-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="8ef49-126">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="8ef49-126">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="8ef49-127">Nebo můžete provést totéž v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="8ef49-127">Or you can do the same thing in configuration as follows.</span></span>  
  
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
  
 <span data-ttu-id="8ef49-128">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8ef49-129">Klient úspěšně by měly volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="8ef49-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="8ef49-130">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="8ef49-131">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="8ef49-131">Setup Batch File</span></span>  
 <span data-ttu-id="8ef49-132">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="8ef49-133">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="8ef49-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="8ef49-134">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="8ef49-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="8ef49-135">Vytvoření certifikátu serveru:</span><span class="sxs-lookup"><span data-stu-id="8ef49-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="8ef49-136">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="8ef49-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="8ef49-137">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="8ef49-138">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="8ef49-139">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="8ef49-139">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="8ef49-140">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="8ef49-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="8ef49-141">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="8ef49-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="8ef49-142">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou implicitně důvěřují systému klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="8ef49-143">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8ef49-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="8ef49-144">Vytvoření certifikátu klienta:</span><span class="sxs-lookup"><span data-stu-id="8ef49-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="8ef49-145">Následující řádky z dávkového souboru Setup.bat vytvořit klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8ef49-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="8ef49-146">Proměnná % uživatelské_jméno % Určuje název klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="8ef49-147">Tato hodnota nastavena na "test1", protože je to název, který hledá kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="8ef49-148">Pokud změníte hodnotu % uživatelské_jméno % musíte změnit s odpovídající hodnotou v Client.cs zdrojový soubor a znovu sestavte klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="8ef49-149">Certifikát je uložen v tomto úložišti (osobních) v umístění úložiště CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="8ef49-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="8ef49-150">Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru:</span><span class="sxs-lookup"><span data-stu-id="8ef49-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="8ef49-151">Následující řádky v dávkovém souboru, Setup.bat zkopírujte certifikát klienta do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="8ef49-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="8ef49-152">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="8ef49-153">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů serveru pomocí certifikátu klienta se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8ef49-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="8ef49-154">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="8ef49-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="8ef49-155">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ef49-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="8ef49-156">Ke spuštění ukázky v jedním - nebo cross-computerconfiguration, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="8ef49-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="8ef49-157">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="8ef49-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="8ef49-158">Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8ef49-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8ef49-159">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="8ef49-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8ef49-160">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8ef49-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="8ef49-161">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="8ef49-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="8ef49-162">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="8ef49-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="8ef49-163">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="8ef49-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="8ef49-164">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="8ef49-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="8ef49-165">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="8ef49-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="8ef49-166">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="8ef49-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="8ef49-167">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="8ef49-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="8ef49-168">Zkopírujte soubory programu služby z \service\bin do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="8ef49-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="8ef49-169">Taky zkopírujte soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="8ef49-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="8ef49-170">Vytvoření adresáře na klienta počítačeDalší binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="8ef49-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="8ef49-171">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8ef49-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="8ef49-172">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="8ef49-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="8ef49-173">Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8ef49-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8ef49-174">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s názvem plně kvalifikované domény computerand Exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="8ef49-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="8ef49-175">Upravit Service.exe.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="8ef49-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="8ef49-176">Taky změnit název počítače v \<služby > /\<baseAddresses > element z localhost pro plně kvalifikovaný název služby počítače.</span><span class="sxs-lookup"><span data-stu-id="8ef49-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="8ef49-177">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8ef49-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="8ef49-178">Na klientovi, spusťte `setup.bat client` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8ef49-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8ef49-179">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="8ef49-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="8ef49-180">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8ef49-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="8ef49-181">To nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="8ef49-182">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="8ef49-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="8ef49-183">V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8ef49-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8ef49-184">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="8ef49-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="8ef49-185">Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce otevřít.</span><span class="sxs-lookup"><span data-stu-id="8ef49-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8ef49-186">Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="8ef49-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="8ef49-187">Na počítači serveru spusťte Service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8ef49-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="8ef49-188">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8ef49-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="8ef49-189">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="8ef49-189">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="8ef49-190">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="8ef49-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="8ef49-191">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="8ef49-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="8ef49-192">Tím se odebere z úložiště certifikátů serveru a klientské certifikáty.</span><span class="sxs-lookup"><span data-stu-id="8ef49-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ef49-193">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="8ef49-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="8ef49-194">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="8ef49-194">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="8ef49-195">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="8ef49-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef49-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef49-196">See Also</span></span>
