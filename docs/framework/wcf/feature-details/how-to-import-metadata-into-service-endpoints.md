---
title: 'Postupy: Import metadat do koncových bodů služeb'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: dce65c31134c211c134cbae2b9bd8296f74b1627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930717"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Postupy: Import metadat do koncových bodů služeb
Toto téma vysvětluje, jak importovat metadata do kolekce koncových bodů služby a používat službu definovanou v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Toto téma ukazuje, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a pak zavolá `Add` metodu služby.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Import metadat do koncových bodů služby  
  
1. <xref:System.ServiceModel.EndpointAddress> Deklarovat objekt a inicializovat ho pomocí identifikátoru URI (Uniform Resource Identifier) pro adresu výměny metadat (MEX) služby.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Vytvořte a předejte adresu MEX a zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. <xref:System.ServiceModel.Description.MetadataExchangeClient> Tím se načtou metadata ze služby.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Vytvořte a předejte dříve načtená metadata a zavolejte <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. <xref:System.ServiceModel.Description.WsdlImporter> Tím se vygeneruje kolekce <xref:System.ServiceModel.Description.ContractDescription> objektů. Můžete také volat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, v závislosti na vašich potřebách.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Po importu metadat nebudete moci vytvořit klientský kanál ani exportovat metadata. Důvodem je skutečnost, že v tuto chvíli nejsou k dispozici žádné informace o typu. Pro skutečnou interakci se službou nebo exportem metadat jsou vyžadovány informace o typu. Chcete-li vygenerovat informace o typu, je nutné vygenerovat kód, který je zobrazen v krocích 4 a 5. Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocnou třídu. Další informace najdete v tématu [jak: Pomocí třídy MetadataResolver můžete dynamicky](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)získat metadata vazby.  
  
4. Generování informací o typu pro každou kontrakt.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Nyní můžete použít tyto informace. Následující ukázka generuje C# zdrojový kód.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
