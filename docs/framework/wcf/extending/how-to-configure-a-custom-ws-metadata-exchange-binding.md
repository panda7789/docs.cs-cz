---
title: "Postupy: Konfigurace vlastních metadat WS Exchange vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 497d7242b581a61aa156741a8c2f0ea278fe2372
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Postupy: Konfigurace vlastních metadat WS Exchange vazby
Toto téma vysvětluje, jak nakonfigurovat vlastní WS-Metadata exchange vazby. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zahrnuje čtyři metadata definovaná systémem vazby, ale můžete metadat pomocí žádné vazby, které chcete publikovat. Toto téma vám ukáže, jak publikovat pomocí metadat `wsHttpBinding`. Tato vazba vám dává možnost vystavení metadata zabezpečené způsobem. Kód v tomto článku je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Použití konfiguračního souboru  
  
1.  V konfiguračním souboru služby, přidat chování služby, který obsahuje `serviceMetadata` značky:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Přidat `behaviorConfiguration` atribut ke značce služby, který odkazuje toto nové chování:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  Přidat koncový bod metadat zadání mex jako adresu, `wsHttpBinding` jako vazba, a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  Ověřte, zda má koncový bod metadat exchange pracovní správně přidejte značku koncového bodu v konfiguračním souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  Metoda Main() klienta, vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte jeho <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a pak iteraci prostřednictvím kolekce metadat vrátil:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurace v kódu  
  
1.  Vytvoření <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> instanci vazby:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  Vytvoření <xref:System.ServiceModel.ServiceHost> instance:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  Přidání koncového bodu služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  Přidat koncový bod metadat systému exchange, určení <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> vytvořili dříve:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  Ověřte, zda je koncovým bodem metadat exchange funguje správně, přidejte značku koncového bodu v konfiguračním souboru klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  Metoda Main() klienta, vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a pak iteraci prostřednictvím kolekce metadat vrátil:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Chování publikování metadat](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [Načtení metadat](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Publikování kocových bodů metadat](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
