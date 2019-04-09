---
title: 'Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: ec4177e71c7d46dc5c908f01a051dc5a0df6baa4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168613"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient
Použití <xref:System.ServiceModel.Description.MetadataExchangeClient> třídy ke stažení metadat pomocí protokolu WS-MetadataExchange (MEX). Soubory načtených metadat se vrátí jako <xref:System.ServiceModel.Description.MetadataSet> objektu. Vrácený <xref:System.ServiceModel.Description.MetadataSet> objekt obsahuje kolekci <xref:System.ServiceModel.Description.MetadataSection> objektů, z nichž každý obsahuje metadata specifická dialekt a identifikátor. Můžete napsat vrácených metadat pro soubory, nebo pokud vrácených metadat obsahuje dokumenty služby popis jazyka WSDL (Web), můžete importovat pomocí metadat <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktorů, které přijímají adresu tuto vazbu využíval na <xref:System.ServiceModel.Description.MetadataExchangeBindings> statické třídy, která odpovídá schématu identifikátoru URI (Uniform Resource) adresy. Můžete také použít <xref:System.ServiceModel.Description.MetadataExchangeClient> konstruktor, který umožňuje explicitně určit použita. Chcete-li vyřešit všechny odkazy na metadata se používá určenou vazbu.  
  
 Stejně jako všechny ostatní klienty Windows Communication Foundation (WCF), <xref:System.ServiceModel.Description.MetadataExchangeClient> typ poskytuje konstruktor pro načtení konfigurace koncových bodů klienta pomocí název konfigurace koncového bodu. Musíte zadat konfigurace zadaný koncový bod <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Adresa v konfiguraci koncového bodu není načten, proto je nutné použít jeden z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> přetížení, která přijímají adresu. Pokud zadáte pomocí adresu metadat <xref:System.ServiceModel.EndpointAddress> instanci, <xref:System.ServiceModel.Description.MetadataExchangeClient> předpokládá, že na adresu odkazuje na koncový bod MEX. Pokud zadáte adresu metadat jako adresu URL, pak musíte také určit, které <xref:System.ServiceModel.Description.MetadataExchangeClientMode> používat MEX nebo HTTP GET.  
  
> [!IMPORTANT]
>  Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient> řeší všechny odkazy, včetně WSDL a schéma XML importuje a zahrnuje. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `false`. Můžete určit maximální počet odkazů na řešení pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> vlastnost. Tuto vlastnost můžete použít ve spojení s `MaxReceivedMessageSize` vlastnost pro vazbu k řízení, kolik metadata se načítají.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>K získání metadat pomocí vlastnosti MetadataExchangeClient  
  
1.  Vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> objekt explicitním zadáním vazbu, název konfigurace koncového bodu nebo adresu metadat.  
  
2.  Konfigurace <xref:System.ServiceModel.Description.MetadataExchangeClient> tak, aby odpovídala vašim potřebám. Například můžete zadat přihlašovací údaje, které chcete použít, pokud se požaduje metadata, řídit, jak jsou odkazy v metadatech vyřešit a nastavit <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> vlastnosti určují, jak dlouho má požadavek metadat k vrácení před vypršením časového limitu.  
  
3.  Získat <xref:System.ServiceModel.Description.MetadataSet> objekt, který obsahuje voláním jedné z načtených metadat <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> metody. Všimněte si, že lze použít pouze <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> přetížení, které nepřijímá žádné argumenty, pokud jste explicitně zadali adresu při vytváření <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataExchangeClient> ke stažení a vytvoření výčtu souborů metadat.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li tento příklad kódu zkompilovat, musí odkazovat na sestavení System.ServiceModel.dll a importovat <xref:System.ServiceModel.Description> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
