---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851220"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange
V tomto tématu se dozvíte, jak nakonfigurovat vlastní vazbu WS-Metadata Exchange. Windows Communication Foundation (WCF) zahrnuje čtyři uživatelsky definované vazby metadat, ale můžete publikovat metadata pomocí libovolné požadované vazby. V `wsHttpBinding`tomto tématu se dozvíte, jak publikovat metadata pomocí. Tato vazba vám dává možnost vystavovat metadata zabezpečeným způsobem. Kód v tomto článku je založen na [Začínáme](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Použití konfiguračního souboru  
  
1. V konfiguračním souboru služby přidejte chování služby, které obsahuje `serviceMetadata` značku:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. `behaviorConfiguration` Přidejte atribut do značky služby, který odkazuje na toto nové chování:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Přidejte koncový bod metadat zadáním formátu MEX jako adresy `wsHttpBinding` , vazby a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte do konfiguračního souboru klienta značku koncového bodu:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. V metodě Main () klienta vytvořte <xref:System.ServiceModel.Description.MetadataExchangeClient> novou instanci, nastavte její <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost na `true`, zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom Iterujte pomocí kolekce vrácených metadat:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurace podle kódu  
  
1. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> vazby:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <xref:System.ServiceModel.ServiceHost> Vytvoření instance:  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Přidejte koncový bod služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Přidejte koncový bod výměny metadat a určete <xref:System.ServiceModel.WSHttpBinding> dříve vytvořený:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte do konfiguračního souboru klienta značku koncového bodu:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. V metodě Main () <xref:System.ServiceModel.Description.MetadataExchangeClient> klienta vytvořte novou instanci, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nastavte vlastnost na `true`, zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom Iterujte pomocí kolekce vrácených metadat:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Chování při publikování metadat](../samples/metadata-publishing-behavior.md)
- [Načítání metadat](../samples/retrieve-metadata.md)
- [Metadata](../feature-details/metadata.md)
- [Publikování metadat](../feature-details/publishing-metadata.md)
- [Publikování koncových bodů metadat](../publishing-metadata-endpoints.md)
