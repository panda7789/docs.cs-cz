---
title: 'Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 1df4bc156485108dc0c11d597b268864c9656b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient
Použití <xref:System.ServiceModel.Description.MetadataExchangeClient> třídy ke stažení metadat pomocí protokolu WS-MetadataExchange (MEX). Soubory načtené metadat se vrátí jako <xref:System.ServiceModel.Description.MetadataSet> objektu. Vrácený <xref:System.ServiceModel.Description.MetadataSet> objektu obsahuje kolekci <xref:System.ServiceModel.Description.MetadataSection> objekty, z nichž každý obsahuje dialekt konkrétních metadat a identifikátor. Metadata vrácená může zapisovat do souborů, nebo pokud vrácený metadat obsahuje webové služby popis Language (WSDL) dokumenty, můžete importovat metadata pomocí <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktory, které nepřijímají adresu použít vazbu na <xref:System.ServiceModel.Description.MetadataExchangeBindings> statická třída, která odpovídá schéma identifikátoru URI (Uniform Resource) adresy. Případně můžete použít <xref:System.ServiceModel.Description.MetadataExchangeClient> konstruktor, který umožňuje explicitně zadat vazby použít. Zadaná vazba slouží k vyřešit všechny odkazy na metadata.  
  
 Stejně jako všechny ostatní klienty Windows Communication Foundation (WCF), <xref:System.ServiceModel.Description.MetadataExchangeClient> typu poskytuje konstruktor pro načtení konfigurace koncového bodu klientů pomocí konfigurace název koncového bodu. Musíte zadat konfiguraci zadaný koncový bod <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt. Adresa v konfiguraci koncového bodu není načten, je nutné použít jeden z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> přetížení, které provést adresu. Pokud zadáte pomocí adres metadata <xref:System.ServiceModel.EndpointAddress> instanci, <xref:System.ServiceModel.Description.MetadataExchangeClient> předpokládá, že adresa ukazuje na koncový bod MEX. Pokud zadáte adresu metadat jako adresu URL, pak je potřeba také určete, které <xref:System.ServiceModel.Description.MetadataExchangeClientMode> chcete použít, MEX nebo HTTP GET.  
  
> [!IMPORTANT]
>  Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient> vyřeší všechny odkazy pro vás, včetně WSDL a schématu XML importuje a obsahuje. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `false`. Můžete řídit maximální počet odkazů na vyřešit pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> vlastnost. Tuto vlastnost můžete použít ve spojení s `MaxReceivedMessageSize` vlastnost vazby k řízení, kolik metadata se načítají.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Chcete-li získat metadata pomocí vlastnosti MetadataExchangeClient  
  
1.  Vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient> objekt explicitním zadáním vazbu, název konfigurace koncového bodu nebo na adresu metadat.  
  
2.  Konfigurace <xref:System.ServiceModel.Description.MetadataExchangeClient> podle svých potřeb. Například můžete zadat pověření pro použití při požaduje metadata, řídit způsob jsou odkazy na metadata vyřešit a nastavte <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> vlastnost k řízení, jak dlouho má požadavek metadat vrátit předtím, než vyprší časový limit.  
  
3.  Získat <xref:System.ServiceModel.Description.MetadataSet> objekt, který obsahuje načtené metadata mezi voláním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> metody. Všimněte si, že lze použít pouze <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> přetížení, které nepřijímá žádné argumenty. Pokud při vytváření explicitně zadat adresu <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataExchangeClient> ke stažení a vytvoření výčtu souborů metadat.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace tento příklad kódu, musí odkazovat na System.ServiceModel.dll sestavení a importovat <xref:System.ServiceModel.Description> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.MetadataResolver>  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>  
 <xref:System.ServiceModel.Description.WsdlImporter>
