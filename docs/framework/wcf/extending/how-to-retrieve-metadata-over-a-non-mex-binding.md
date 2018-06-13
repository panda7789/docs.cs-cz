---
title: 'Postupy: Načítání metadat přes vazbu jiného typu než MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 198c343aa6f25d55e518990dc1dbd2667a8c17ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488085"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Postupy: Načítání metadat přes vazbu jiného typu než MEX
Toto téma popisuje, jak načíst metadata z koncového bodu MEX přes jiný MEX vazby. Kód v této ukázce je založen na [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázka.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Pro načtení metadat přes vazbu bez MEX  
  
1.  Určení vazba použitá v MEX koncovém bodě. Pro služby Windows Communication Foundation (WCF) můžete určit vazby MEX pomocí přístupu k souboru konfigurace služby. V takovém případě MEX vazba je definována v následující konfiguraci služby.  
  
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
  
2.  V konfiguračním souboru klienta nakonfigurujte stejné vlastní vazby. Zde také definuje klienta `clientCredentials` chování poskytnutí certifikátu sloužící k ověření služby při požaduje metadata z koncového bodu MEX. Při použití Svcutil.exe k vyžádání metadat prostřednictvím vlastní vazby, měli byste přidat konfiguraci koncového bodu MEX do konfiguračního souboru pro Svcutil.exe (Svcutil.exe.config) a název konfigurace koncového bodu musí odpovídat schéma identifikátoru URI adresy MEX koncového bodu, jak je znázorněno v následujícím kódu.  
  
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
  
3.  Vytvoření `MetadataExchangeClient` a volání `GetMetadata`. Existují dva způsoby, jak to udělat: můžete zadat vlastní vazby v konfiguraci, nebo můžete zadat vlastní vazby v kódu, jak je znázorněno v následujícím příkladu.  
  
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
  
4.  Vytvoření `WsdlImporter` a volání `ImportAllEndpoints`, jak je znázorněno v následujícím kódu.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  V tuto chvíli máte kolekci koncové body služby. Další informace o importu metadat najdete v tématu [postupy: Import metadat do koncových bodů služby](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
