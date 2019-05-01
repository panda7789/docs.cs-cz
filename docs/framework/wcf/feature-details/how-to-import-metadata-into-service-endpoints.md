---
title: 'Postupy: Import metadat do koncových bodů služeb'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: afee3f2236db99b14c0e840d987e4862a260568e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047825"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Postupy: Import metadat do koncových bodů služeb
Toto téma vysvětluje, jak importovat metadata do kolekce koncových bodů služby a použití služby definované v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V tomto tématu ukazují, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a volání `Add` metodu na službu.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Import metadat do koncových bodů služeb  
  
1. Deklarovat <xref:System.ServiceModel.EndpointAddress> objektu a inicializovat s identifikátor URI (Uniform Resource) pro exchange (MEX) adresu metadat služby.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Vytvoření <xref:System.ServiceModel.Description.MetadataExchangeClient>a předejte nebyla určena adresa MEX. a volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. To načte metadata ze služby.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Vytvoření <xref:System.ServiceModel.Description.WsdlImporter>a předejte dříve načíst metadata a volání <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Tím se vytvoří kolekce <xref:System.ServiceModel.Description.ContractDescription> objekty. Lze také volat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, v závislosti na vašich potřeb.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Po importu metadat nebudete mít k vytvoření kanálu klienta nebo exportovat metadata. To je, protože v tuto chvíli není k dispozici žádné informace o typu. Informace o typu je potřeba ve skutečnosti interakci se službou nebo export metadat. Generovat informace o typu, je nutné generovat kód, zobrazený v krocích 4 a 5. Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocná třída. Další informace najdete v tématu [jak: Použití třídy MetadataResolver k dynamickému získání metadat vazby](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4. Generovat informace o typu pro každou smlouvu.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Teď můžete použít tyto informace. Následující ukázka generuje C# zdrojový kód.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
