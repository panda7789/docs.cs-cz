---
title: "Postupy: Import metadat do koncových bodů služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afc08d08a8843460972daf259027475cbbc10b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Postupy: Import metadat do koncových bodů služby
Toto téma vysvětluje, jak importovat metadata do kolekce koncové body služby a používat službu definované v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V tomto tématu ukazují, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a poté zavolá `Add` metoda ve službě.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Import metadat do koncových bodů služby  
  
1.  Deklarace <xref:System.ServiceModel.EndpointAddress> objektu a provést jeho inicializaci s identifikátor URI (Uniform Resource) pro adresu exchange (MEX) metadata služby.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  Vytvoření <xref:System.ServiceModel.Description.MetadataExchangeClient>, předejte v MEX adresu a volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Tato metadata načte ze služby.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  Vytvoření <xref:System.ServiceModel.Description.WsdlImporter>a předejte dříve načíst metadata a volání <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Tento postup vytvoří kolekci <xref:System.ServiceModel.Description.ContractDescription> objekty. Může také zavolat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, v závislosti na vašich potřeb.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Po importu metadat, nebude možné vytvořit kanál klienta nebo exportovat metadata. Je to proto, že v tomto okamžiku je k dispozici žádné informace o typu. Informace o typu, je potřeba ve skutečnosti komunikovat se službou nebo export metadat. Chcete-li generovat informace o typu, je potřeba generovat kód, uvedené v kroku 4 a 5. Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocná třída. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: použití třídy MetadataResolver k dynamickému získání metadat vazby](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  Generovat informace o typu pro každý kontrakt.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  Nyní můžete tyto informace. Následující příklad vytvoří zdrojový kód C#.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
