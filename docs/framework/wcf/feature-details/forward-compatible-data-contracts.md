---
title: Kontrakty dat s dopřednou kompatibilitou
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 732c47b03c2769a6147c3c812ddd6e81dab11a55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695644"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty dat s dopřednou kompatibilitou
Funkce z Windows Communication Foundation (WCF) je systém kontraktu dat, která smluv týkajících se může časem vyvíjet pevná způsoby. To znamená klient starší verze kontraktu dat může komunikovat se službou novější verzi stejné kontraktu dat nebo klient novější verze kontraktu dat může komunikovat s starší verzi stejný kontrakt dat. Další informace najdete v tématu [osvědčených postupů: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Při vytváření nových verzí existujících kontraktu dat, můžete použít většinu funkcí správy verzí podle potřeby. Ale pro jednu funkci správy verzí, *verzemi*, musí být sestaveny na typ z první verze, aby vše správně fungovalo.  
  
## <a name="round-tripping"></a>Verzemi  
 Když data úspěšně projdou z novou verzi do starší verze a zpět na novou verzi kontraktu dat dojde k verzemi. Verzemi zaručuje, že se neztratila žádná data. Povolení verzemi díky typ dopřednou obsahující všechny budoucí změny nepodporuje datový model správy verzí kontraktu.  
  
 Pokud chcete povolit verzemi pro určitý typ, musí implementovat typ <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (vrácení <xref:System.Runtime.Serialization.ExtensionDataObject> typu). Vlastnost uloží všechna data z budoucí verze kontraktu dat, který neznámý pro aktuální verzi.  
  
### <a name="example"></a>Příklad  
 Následující kontraktu dat. není dopřednou budoucí změny.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Chcete-li typ kompatibilní s budoucí změny (např. přidejte nový datový člen s názvem "telefonní číslo"), implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Když infrastruktura WCF narazí na data, která není součástí původní kontraktu dat, data jsou uložená ve vlastnosti a zachovají. Není zpracována jiným způsobem s výjimkou dočasné úložiště. Pokud je objekt vrácen zpět na jejím původu, vrátí se také původní data (neznámá). Proto se provedl data z původní koncový bod beze ztrát a latence. Všimněte si však, že v případě potřeby data ke zpracování výchozí koncový bod tohoto očekává se dosud nevyřešených a koncového bodu musí nějakým způsobem detekovat a vyhovují novince.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Typ neobsahuje žádné veřejné metody nebo vlastnosti. Proto není možné získat přímý přístup k datům uloženým v <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost.  
  
 Funkce verzemi může být vypnutý, buď nastavením `ignoreExtensionDataObject` k `true` v <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru nebo nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost `true` na <xref:System.ServiceModel.ServiceBehaviorAttribute>. Když tato funkce je vypnuta, nebude naplnit deserializátor <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost a serializátor nebude generovat obsah vlastnosti.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
