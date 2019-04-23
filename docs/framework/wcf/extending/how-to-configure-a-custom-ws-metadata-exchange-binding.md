---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 51681e258e6a21b3a7ae604d1c0ef65d320bfb4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311874"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange
Toto téma vysvětluje, jak nakonfigurovat vlastní WS-Metadata exchange vazby. Zahrnuje čtyři vazby metadata definovaná uživatelem systému Windows Communication Foundation (WCF), ale můžete publikovat metadat pomocí všechny vazby, který chcete. V tomto tématu ukazují, jak publikovat pomocí metadat `wsHttpBinding`. Tato vazba získáte možnost bezpečně doručovat jestli vystavuje metadata. Kód v tomto článku je založený na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Použití konfiguračního souboru  
  
1. V konfiguračním souboru služby, přidejte chování služby, který obsahuje `serviceMetadata` značky:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Přidat `behaviorConfiguration` atribut ke značce služby, který odkazuje na toto nové chování:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Přidat koncový bod metadat zadání mex jako adresu, `wsHttpBinding` jako vazbu, a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontrakt:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Chcete-li ověřit, že je koncový bod výměny metadat pracovních správně přidání značky koncového bodu v konfiguračním souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. V metodě Main() klienta, vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte jeho <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iteraci prostřednictvím kolekce metadat vrátil:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurace kódu  
  
1. Vytvoření <xref:System.ServiceModel.WSHttpBinding> instanci vazby:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Vytvoření <xref:System.ServiceModel.ServiceHost> instance:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Přidání koncového bodu služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Přidat koncový bod výměny metadat, určení <xref:System.ServiceModel.WSHttpBinding> vytvořili dříve:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Pokud chcete ověřit, že koncový bod výměny metadat pracuje správně, přidejte značku koncový bod v konfiguračním souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. V metodě Main() klienta, vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iteraci prostřednictvím kolekce metadat vrátil:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Chování při publikování metadat](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [Načítání metadat](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [Publikování koncových bodů metadat](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
