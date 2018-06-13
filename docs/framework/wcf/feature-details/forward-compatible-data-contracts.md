---
title: Kontrakty dat s dopřednou kompatibilitou
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 95a72d5d09538bc6f663f2376c7f8f928909cd57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492203"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty dat s dopřednou kompatibilitou
Funkce z Windows Communication Foundation (WCF) je systém kontraktu dat, měnící můžete rozvíjet časem pevných způsoby. To znamená klient se starší verzí systému kontraktu dat může komunikovat se službou novější verzi stejné kontrakt dat nebo klient novější verzi kontraktu dat může komunikovat s starší verze stejné kontrakt dat. Další informace najdete v tématu [osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Většina funkcí správy verzí na podle potřeby můžete použít při vytváření nové verze existující smlouvy data. Ale jedna z funkcí správy verzí, *odezvy*, musí být typu z první verze součástí správné fungování.  
  
## <a name="round-tripping"></a>Odezvy  
 Odezvy nastane, když data předává z novou verzi na předchozí verzi a zpět na novou verzi sady kontraktu dat. Odezvy zaručuje, že je ztracena žádná data. Povolení odezvy díky typ dopřednou s všechny budoucí změny nepodporuje kontrakt datový model správy verzí.  
  
 Pokud chcete povolit odezvy pro určitý typ, musí typ implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (vrácení <xref:System.Runtime.Serialization.ExtensionDataObject> typ). Vlastnost ukládá všechna data v budoucích verzích kontrakt dat, který neznámý na aktuální verzi.  
  
### <a name="example"></a>Příklad  
 Následující kontrakt dat není dopřednou budoucí změny.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Chcete-li typ kompatibilní s budoucí změny (jako je například přidávání nového člena dat s názvem "phoneNumber"), implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Když infrastruktury WCF zaznamená data, která není součástí původní kontrakt dat, data uložená ve vlastnosti a zachovají. Jiným způsobem s výjimkou dočasné úložiště není zpracován. Pokud objekt se vrátí zpět na místo původu, vrátí se také původní data (neznámé). Proto data udělal dobu odezvy na a z původní koncového bodu bez ztráty. Upozorňujeme však, že v případě potřeby data ke zpracování výchozí koncový bod této očekávání je unmet, a koncový bod musí nějakým způsobem zjistit a uložení změn.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Typ obsahuje žádné veřejné metody nebo vlastnosti. Proto není možné získat přímý přístup k datům uloženým v <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost.  
  
 Funkci odezvy může být vypnutý, buď nastavením `ignoreExtensionDataObject` k `true` v <xref:System.Runtime.Serialization.DataContractSerializer> konstruktor nebo nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost `true` na <xref:System.ServiceModel.ServiceBehaviorAttribute>. Když tato funkce je vypnutá, nebudou naplnit deserializátor <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost a serializátor, nebude emitování obsah vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
