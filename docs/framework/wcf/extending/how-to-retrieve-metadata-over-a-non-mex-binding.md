---
title: 'Postupy: Načítání metadat přes vazbu jiného typu než MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: a006795c87a2ae845d03db90dce296692c4339fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186450"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="b1657-102">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="b1657-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="b1657-103">Toto téma popisuje, jak načíst metadata z koncového bodu MEX přes vazby mimo MEX.</span><span class="sxs-lookup"><span data-stu-id="b1657-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="b1657-104">Kód v této ukázce je založen na [ukázce vlastní zabezpečené metadata koncového bodu.](../samples/custom-secure-metadata-endpoint.md)</span><span class="sxs-lookup"><span data-stu-id="b1657-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="b1657-105">Načtení metadat přes vazbu mimo MEX</span><span class="sxs-lookup"><span data-stu-id="b1657-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="b1657-106">Určete vazbu používanou koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="b1657-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="b1657-107">Pro služby Windows Communication Foundation (WCF) můžete určit vazbu MEX přístupem ke konfiguračnímu souboru služby.</span><span class="sxs-lookup"><span data-stu-id="b1657-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="b1657-108">V tomto případě je vazba MEX definována v následující konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="b1657-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="b1657-109">V konfiguračním souboru klienta nakonfigurujte stejnou vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1657-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="b1657-110">Zde klient také definuje `clientCredentials` chování poskytnout certifikát pro ověření služby při vyžádání metadat z koncového bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="b1657-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="b1657-111">Při použití programu Svcutil.exe k vyžádání metadat přes vlastní vazbu byste měli přidat konfiguraci koncového bodu MEX do konfiguračního souboru pro soubor Svcutil.exe (Svcutil.exe.config) a název konfigurace koncového bodu by měl odpovídat schématu URI adresy koncového bodu MEX, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b1657-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="b1657-112">Vytvořte `MetadataExchangeClient` a `GetMetadata`volejte .</span><span class="sxs-lookup"><span data-stu-id="b1657-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="b1657-113">Existují dva způsoby, jak to provést: můžete zadat vlastní vazbu v konfiguraci, nebo můžete zadat vlastní vazbu v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b1657-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="b1657-114">Vytvořte `WsdlImporter` a `ImportAllEndpoints`volání , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b1657-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="b1657-115">V tomto okamžiku máte kolekci koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="b1657-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="b1657-116">Další informace o importu metadat najdete v [tématu Postup: Import metadat do koncových bodů služby](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="b1657-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1657-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1657-117">See also</span></span>

- [<span data-ttu-id="b1657-118">Metadata</span><span class="sxs-lookup"><span data-stu-id="b1657-118">Metadata</span></span>](../feature-details/metadata.md)
