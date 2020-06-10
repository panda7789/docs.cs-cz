---
title: Validátor certifikátu X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 32d99b93ef014967aa04bc70f73fbd2ebcfe2c60
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594826"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="3c00c-102">Validátor certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="3c00c-102">X.509 Certificate Validator</span></span>

<span data-ttu-id="3c00c-103">Tato ukázka předvádí, jak implementovat vlastní validátor certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="3c00c-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="3c00c-104">To je užitečné v případech, kdy žádný z vestavěných režimů ověřování certifikátů X. 509 není vhodný pro požadavky aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c00c-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="3c00c-105">Tato ukázka obsahuje službu, která má vlastní validátor, který přijímá certifikáty, které byly vydány samostatně.</span><span class="sxs-lookup"><span data-stu-id="3c00c-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="3c00c-106">Klient používá takový certifikát k ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="3c00c-106">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="3c00c-107">Poznámka: Jelikož kdokoli může vytvořit certifikát vystavený svým držitelem, je vlastní validátor používaný službou méně bezpečný než výchozí chování, které poskytuje ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="3c00c-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="3c00c-108">Aby bylo možné použít tuto logiku ověřování v produkčním kódu, je třeba pečlivě zvážit důsledky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3c00c-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="3c00c-109">V části Souhrn tento příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="3c00c-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="3c00c-110">Klienta lze ověřit pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="3c00c-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="3c00c-111">Server ověří pověření klienta proti vlastnímu X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="3c00c-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="3c00c-112">Server je ověřený pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-112">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="3c00c-113">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config. Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3c00c-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="3c00c-114">Vazba je nakonfigurována se standardem `wsHttpBinding` , který používá výchozí nastavení `WSSecurity` a ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3c00c-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="3c00c-115">Chování služby určuje vlastní režim pro ověřování klientských certifikátů X. 509 spolu s typem třídy validátoru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="3c00c-116">Chování také Určuje certifikát serveru pomocí elementu serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="3c00c-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="3c00c-117">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="3c00c-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="3c00c-118">Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3c00c-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="3c00c-119">Vazba klienta je nakonfigurovaná s odpovídajícím režimem a zprávou `clientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="3c00c-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

<span data-ttu-id="3c00c-120">Implementace klienta nastaví klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="3c00c-120">The client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="3c00c-121">Tato ukázka používá vlastní X509CertificateValidator k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="3c00c-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="3c00c-122">Ukázka implementuje CustomX509CertificateValidator odvozené z <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="3c00c-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="3c00c-123">Další informace najdete v dokumentaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="3c00c-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="3c00c-124">Tato konkrétní ukázka vlastního validátoru implementuje metodu Validate pro přijetí libovolného certifikátu X. 509, který je vystaven vlastním držitelem, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3c00c-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

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

 <span data-ttu-id="3c00c-125">Po implementaci ověřovacího modulu v kódu služby musí být hostitel služby informován o instanci validátoru, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="3c00c-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="3c00c-126">To se provádí pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="3c00c-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="3c00c-127">Nebo můžete stejnou věc provést v konfiguraci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3c00c-127">Or you can do the same thing in configuration as follows.</span></span>

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
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="3c00c-128">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3c00c-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3c00c-129">Klient by měl úspěšně volat všechny metody.</span><span class="sxs-lookup"><span data-stu-id="3c00c-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="3c00c-130">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="3c00c-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="3c00c-131">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="3c00c-131">Setup Batch File</span></span>

<span data-ttu-id="3c00c-132">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="3c00c-133">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="3c00c-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="3c00c-134">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="3c00c-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="3c00c-135">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="3c00c-135">Creating the server certificate:</span></span>

     <span data-ttu-id="3c00c-136">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="3c00c-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="3c00c-137">Proměnná% SERVER_NAME% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="3c00c-138">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="3c00c-139">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="3c00c-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="3c00c-140">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="3c00c-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="3c00c-141">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="3c00c-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="3c00c-142">Tento krok je vyžadován, protože certifikáty generované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="3c00c-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="3c00c-143">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="3c00c-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="3c00c-144">Vytváří se klientský certifikát:</span><span class="sxs-lookup"><span data-stu-id="3c00c-144">Creating the client certificate:</span></span>

     <span data-ttu-id="3c00c-145">Následující řádky z dávkového souboru Setup. bat vytvoří klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="3c00c-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="3c00c-146">Proměnná% USER_NAME% Určuje název klienta.</span><span class="sxs-lookup"><span data-stu-id="3c00c-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="3c00c-147">Tato hodnota je nastavená na "test1", protože se jedná o název, který klientský kód hledá.</span><span class="sxs-lookup"><span data-stu-id="3c00c-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="3c00c-148">Pokud změníte hodnotu% USER_NAME%, je nutné změnit odpovídající hodnotu ve zdrojovém souboru Client.cs a znovu sestavit klienta.</span><span class="sxs-lookup"><span data-stu-id="3c00c-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="3c00c-149">Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="3c00c-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="3c00c-150">Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru:</span><span class="sxs-lookup"><span data-stu-id="3c00c-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="3c00c-151">Následující řádky v dávkovém souboru Setup. bat kopírují klientský certifikát do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="3c00c-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="3c00c-152">Tento krok je povinný, protože serverové systémy vygenerované pomocí nástroje MakeCert. exe implicitně nedůvěřují.</span><span class="sxs-lookup"><span data-stu-id="3c00c-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="3c00c-153">Pokud již máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu, například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů serveru pomocí klientského certifikátu není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="3c00c-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="3c00c-154">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="3c00c-154">To set up and build the sample</span></span>

1. <span data-ttu-id="3c00c-155">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c00c-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="3c00c-156">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="3c00c-156">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="3c00c-157">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="3c00c-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="3c00c-158">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3c00c-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3c00c-159">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="3c00c-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3c00c-160">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3c00c-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="3c00c-161">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="3c00c-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="3c00c-162">Spustit Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="3c00c-162">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="3c00c-163">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="3c00c-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="3c00c-164">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="3c00c-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="3c00c-165">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3c00c-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3c00c-166">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="3c00c-166">To run the sample across computers</span></span>

1. <span data-ttu-id="3c00c-167">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="3c00c-167">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="3c00c-168">Zkopírujte programové soubory služby z \service\bin do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="3c00c-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="3c00c-169">Zkopírujte také soubory Setup. bat, Cleanup. bat, GetComputerName. vbs a ImportClientCert. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="3c00c-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="3c00c-170">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="3c00c-170">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="3c00c-171">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="3c00c-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="3c00c-172">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="3c00c-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="3c00c-173">Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3c00c-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3c00c-174">Při spuštění `setup.bat` s `service` argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="3c00c-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="3c00c-175">Upravte soubor Service. exe. config tak, aby odrážel nový název certifikátu (v `findValue` atributu [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="3c00c-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="3c00c-176">Také změňte název počítače v \<service> / \<baseAddresses> elementu z localhost na plně kvalifikovaný název počítače služby.</span><span class="sxs-lookup"><span data-stu-id="3c00c-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="3c00c-177">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="3c00c-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="3c00c-178">Na straně klienta spusťte `setup.bat client` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3c00c-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3c00c-179">Při spuštění `setup.bat` s `client` argumentem se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.</span><span class="sxs-lookup"><span data-stu-id="3c00c-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="3c00c-180">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="3c00c-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="3c00c-181">Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="3c00c-182">Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="3c00c-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="3c00c-183">Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3c00c-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3c00c-184">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3c00c-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="3c00c-185">Na serveru spusťte ImportClientCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3c00c-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3c00c-186">Tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3c00c-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="3c00c-187">V počítači serveru spusťte z okna příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="3c00c-187">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="3c00c-188">V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3c00c-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="3c00c-189">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3c00c-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3c00c-190">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="3c00c-190">To clean up after the sample</span></span>

1. <span data-ttu-id="3c00c-191">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="3c00c-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="3c00c-192">Tím dojde k odebrání certifikátů serveru a klienta z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="3c00c-192">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="3c00c-193">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="3c00c-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="3c00c-194">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3c00c-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3c00c-195">Použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="3c00c-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
