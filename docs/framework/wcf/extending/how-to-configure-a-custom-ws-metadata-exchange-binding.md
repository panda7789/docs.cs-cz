---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 6459e3f0cf0ab72af8027bd6802a0e7aa574aece
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635788"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange

Tento článek vysvětluje, jak nakonfigurovat vlastní vazby výměny ws-metadata. Windows Communication Foundation (WCF) obsahuje čtyři systémem definované vazby metadat, ale můžete publikovat metadata pomocí libovolné vazby, které chcete. Tento článek ukazuje, jak publikovat `wsHttpBinding`metadata pomocí . Tato vazba poskytuje možnost vystavení metadat bezpečným způsobem. Kód v tomto článku je založen na [začínáme](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Použití konfiguračního souboru  
  
1. Do konfiguračního souboru služby přidejte chování služby, které obsahuje `serviceMetadata` značku:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Přidejte `behaviorConfiguration` atribut k výrobníznačce, která odkazuje na toto nové chování:  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. Přidejte koncový bod metadat určující mex `wsHttpBinding` jako adresu, <xref:System.ServiceModel.Description.IMetadataExchange> jako vazbu a jako smlouvu:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte značku koncového bodu do konfiguračního souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. V metodě Main() klienta <xref:System.ServiceModel.Description.MetadataExchangeClient> vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> instanci, nastavte její vlastnost na `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iterace prostřednictvím kolekce vrácených metadat:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurace podle kódu  
  
1. Vytvoření <xref:System.ServiceModel.WSHttpBinding> instance vazby:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Vytvoření <xref:System.ServiceModel.ServiceHost> instance:  
  
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
  
4. Přidejte koncový bod výměny metadat <xref:System.ServiceModel.WSHttpBinding> a určete dříve vytvořený:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte značku koncového bodu do konfiguračního souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. V metodě Main() klienta <xref:System.ServiceModel.Description.MetadataExchangeClient> vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> instanci, nastavte vlastnost na `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iterace prostřednictvím kolekce vrácených metadat:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Viz také

- [Chování publikování metadat](../samples/metadata-publishing-behavior.md)
- [Načítání metadat](../samples/retrieve-metadata.md)
- [Metadata](../feature-details/metadata.md)
- [Publikování metadat](../feature-details/publishing-metadata.md)
- [Publikování kocových bodů metadat](../publishing-metadata-endpoints.md)
