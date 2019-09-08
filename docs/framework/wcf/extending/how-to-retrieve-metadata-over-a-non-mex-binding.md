---
title: 'Postupy: Načítání metadat přes vazbu jiného typu než MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 6cd6e0ce5dc287c826179c152b989b5f7842bb6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795582"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Postupy: Načítání metadat přes vazbu jiného typu než MEX
Toto téma popisuje, jak načíst metadata z koncového bodu MEX přes vazbu, která není MEX. Kód v této ukázce je založen na vlastní ukázce [zabezpečeného koncového bodu metadat](../samples/custom-secure-metadata-endpoint.md) .  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Načtení metadat přes vazbu jiného typu než MEX  
  
1. Určete vazbu používanou koncovým bodem MEX. V případě služby Windows Communication Foundation (WCF) můžete určit vazbu MEX pomocí přístupu ke konfiguračnímu souboru služby. V tomto případě je vazba MEX definována v následující konfiguraci služby.  
  
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
  
2. V konfiguračním souboru klienta nakonfigurujte stejnou vlastní vazbu. V tomto článku je také definováno `clientCredentials` chování, které poskytuje certifikát, který se má použít k ověření služby pro službu při požadování metadat z koncového bodu MEX. Při použití nástroje Svcutil. exe k vyžádání metadat prostřednictvím vlastní vazby byste měli přidat konfiguraci koncového bodu MEX do konfiguračního souboru pro Svcutil. exe (Svcutil. exe. config) a název konfigurace koncového bodu by měl odpovídat schématu identifikátoru URI adresy koncový bod MEX, jak je znázorněno v následujícím kódu.  
  
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
  
3. Vytvořte volání `MetadataExchangeClient` `GetMetadata`a. Existují dva způsoby, jak to provést: můžete zadat vlastní vazbu v konfiguraci nebo můžete zadat vlastní vazbu v kódu, jak je znázorněno v následujícím příkladu.  
  
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
  
4. Vytvořte volání `WsdlImporter` `ImportAllEndpoints`a, jak je znázorněno v následujícím kódu.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. V tomto okamžiku máte kolekci koncových bodů služby. Další informace o importu metadat naleznete v tématu [How to: Importuje metadata do koncových](../feature-details/how-to-import-metadata-into-service-endpoints.md)bodů služby.  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../feature-details/metadata.md)
