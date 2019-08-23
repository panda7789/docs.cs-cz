---
title: 'Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: c9558e1943c3886a61c3b19801e22d57732e459a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968756"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient
<xref:System.ServiceModel.Description.MetadataExchangeClient> Pomocí třídy můžete stahovat metadata pomocí protokolu WS-MetadataExchange (MEX). Načtené soubory metadat se vrátí jako <xref:System.ServiceModel.Description.MetadataSet> objekt. Vrácený <xref:System.ServiceModel.Description.MetadataSet> objekt obsahuje <xref:System.ServiceModel.Description.MetadataSection> kolekci objektů, z nichž každý obsahuje konkrétní dialekt metadat a identifikátor. Můžete zapsat vracená metadata do souborů nebo, pokud Vrácená metadata obsahují dokumenty jazyka WSDL (Web Services Description Language), můžete importovat metadata pomocí <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 Konstruktory, které přijímají adresu, používají vazbu <xref:System.ServiceModel.Description.MetadataExchangeBindings> na statické třídě, která odpovídá schématu identifikátoru URI (Uniform Resource Identifier) adresy. <xref:System.ServiceModel.Description.MetadataExchangeClient> Můžete alternativně použít <xref:System.ServiceModel.Description.MetadataExchangeClient> konstruktor, který umožňuje explicitně zadat vazbu, která se má použít. Zadaná vazba se používá k překladu všech odkazů na metadata.  
  
 Stejně jako u jakéhokoli jiného klienta <xref:System.ServiceModel.Description.MetadataExchangeClient> Windows Communication Foundation (WCF) poskytuje typ konstruktor pro načítání konfigurací koncových bodů klienta pomocí názvu konfigurace koncového bodu. Zadaná konfigurace koncového bodu musí určovat <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt. Adresa v konfiguraci koncového bodu není načtena, takže je nutné použít jedno z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> přetížení, které přebírají adresu. Když zadáte adresu metadat pomocí <xref:System.ServiceModel.EndpointAddress> instance <xref:System.ServiceModel.Description.MetadataExchangeClient> , předpokládá, že adresa odkazuje na koncový bod mex. Pokud zadáte adresu metadat jako adresu URL, je třeba zadat také, která z nich <xref:System.ServiceModel.Description.MetadataExchangeClientMode> se má použít, MEX nebo HTTP GET.  
  
> [!IMPORTANT]
> Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient> vyřeší všechny odkazy za vás, včetně importu schématu WSDL a XML a obsahuje. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnosti na. `false` Můžete určit maximální počet odkazů, které se mají vyřešit, pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> vlastnosti. Tuto vlastnost lze použít společně s `MaxReceivedMessageSize` vlastností vazby k určení, kolik metadat je načteno.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Použití metody MetadataExchangeClient k získání metadat  
  
1. Vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> objekt explicitním zadáním vazby, názvu konfigurace koncového bodu nebo adresy metadat.  
  
2. Nakonfigurujte tak, aby vyhovoval vašim potřebám. <xref:System.ServiceModel.Description.MetadataExchangeClient> Můžete například zadat přihlašovací údaje, které se mají použít při vyžadování metadat, řízení způsobu, jakým jsou vyřešeny <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> odkazy na metadata, a nastavit vlastnost pro řízení, jak dlouho musí požadavek na metadata vrátit před vypršením časového limitu.  
  
3. Získejte objekt, který obsahuje načtená metadata, voláním jedné <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> z metod. <xref:System.ServiceModel.Description.MetadataSet> Všimněte si, že můžete použít <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> pouze přetížení, které nepřijímá žádné argumenty, pokud explicitně zadáte adresu při sestavování. <xref:System.ServiceModel.Description.MetadataExchangeClient>  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít <xref:System.ServiceModel.Description.MetadataExchangeClient> ke stažení a zobrazení výčtu souborů metadat.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat tento příklad kódu, musíte odkazovat na sestavení System. ServiceModel. dll a importovat <xref:System.ServiceModel.Description> obor názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
