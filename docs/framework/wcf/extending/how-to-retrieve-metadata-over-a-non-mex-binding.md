---
title: "Postupy: Načítání metadat přes vazbu jiného typu než MEX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f214c45ea09c96d5cb77646f31b7c53338761621
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="1450c-102">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="1450c-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="1450c-103">Toto téma popisuje, jak načíst metadata z koncového bodu MEX přes jiný MEX vazby.</span><span class="sxs-lookup"><span data-stu-id="1450c-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="1450c-104">Kód v této ukázce je založen na [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="1450c-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="1450c-105">Pro načtení metadat přes vazbu bez MEX</span><span class="sxs-lookup"><span data-stu-id="1450c-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1.  <span data-ttu-id="1450c-106">Určení vazba použitá v MEX koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="1450c-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="1450c-107">Pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, můžete určit vazby MEX pomocí přístupu k souboru konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="1450c-107">For [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="1450c-108">V takovém případě MEX vazba je definována v následující konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="1450c-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2.  <span data-ttu-id="1450c-109">V konfiguračním souboru klienta nakonfigurujte stejné vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1450c-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="1450c-110">Zde také definuje klienta `clientCredentials` chování poskytnutí certifikátu sloužící k ověření služby při požaduje metadata z koncového bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="1450c-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="1450c-111">Při použití Svcutil.exe k vyžádání metadat prostřednictvím vlastní vazby, měli byste přidat konfiguraci koncového bodu MEX do konfiguračního souboru pro Svcutil.exe (Svcutil.exe.config) a název konfigurace koncového bodu musí odpovídat schéma identifikátoru URI adresy MEX koncového bodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1450c-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3.  <span data-ttu-id="1450c-112">Vytvoření `MetadataExchangeClient` a volání `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="1450c-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="1450c-113">Existují dva způsoby, jak to udělat: můžete zadat vlastní vazby v konfiguraci, nebo můžete zadat vlastní vazby v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1450c-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="1450c-114">Vytvoření `WsdlImporter` a volání `ImportAllEndpoints`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1450c-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  <span data-ttu-id="1450c-115">V tuto chvíli máte kolekci koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="1450c-115">At this point, you have a collection of service endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1450c-116">Import metadat, najdete v části [postupy: Import metadat do koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="1450c-116"> importing metadata, see [How to: Import Metadata into Service Endpoints](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1450c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1450c-117">See Also</span></span>  
 [<span data-ttu-id="1450c-118">Metadata</span><span class="sxs-lookup"><span data-stu-id="1450c-118">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
