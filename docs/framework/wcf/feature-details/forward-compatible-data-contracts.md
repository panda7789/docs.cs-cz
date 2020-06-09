---
title: Kontrakty dat s dopřednou kompatibilitou
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 34bde56b78ec0148cf6b924f8edd29343b97faa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597381"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty dat s dopřednou kompatibilitou
Pro systém kontraktů dat Windows Communication Foundation (WCF) se kontrakty můžou v průběhu času vyvíjet v nerozdělování. To znamená, že klient starší verze kontraktu dat může komunikovat se službou s novější verzí stejné kontraktu dat nebo klient s novější verzí kontraktu dat může komunikovat se starší verzí stejného kontraktu dat. Další informace najdete v tématu [osvědčené postupy: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md).  
  
 V případě, že jsou vytvořeny nové verze existující kontraktu dat, můžete použít většinu funkcí pro správu verzí podle potřeby. Nicméně jedna funkce správy verzí, *Round-Trip*, musí být integrována do typu z první verze, aby fungovala správně.  
  
## <a name="round-tripping"></a>Round-Trip  
 K kulatému Trip dojde, když data přecházejí z nové verze do staré verze a zpátky do nové verze kontraktu dat. Kulaté Trip zaručuje, že nedojde ke ztrátě dat. Povolení možnosti Round-Trip zajistí, že se typ dopředně dokončí s případnými budoucími změnami, které podporuje model verze kontraktu dat.  
  
 Chcete-li povolit příkaz round-trip pro konkrétní typ, musí tento typ implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (návrat <xref:System.Runtime.Serialization.ExtensionDataObject> typu). Vlastnost ukládá jakákoli data z budoucích verzí kontraktu dat, která jsou pro aktuální verzi neznámá.  
  
### <a name="example"></a>Příklad  
 Následující kontrakt dat není při budoucích změnách kompatibilní s dopředně.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Chcete-li nastavit typ kompatibilní s budoucími změnami (například přidáním nového datového člena s názvem "phoneNumber"), implementujte <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Když infrastruktura WCF narazí na data, která nejsou součástí původní kontraktu dat, uloží se data do vlastnosti a zachovají se. Nezpracovává se žádným jiným způsobem s výjimkou dočasného úložiště. Pokud se objekt vrátí zpět na místo, kde pochází, vrátí se také původní (neznámá) data. Proto data provedla operaci round trip do a z původního koncového bodu bez ztráty. Upozorňujeme však, že pokud koncový bod vyžaduje zpracování dat, očekává se, že je nesplnění, a koncový bod musí nějakým způsobem zjistit a přizpůsobit změnu.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject>Typ neobsahuje žádné veřejné metody nebo vlastnosti. Proto není možné získat přímý přístup k datům uloženým uvnitř <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Vlastnosti.  
  
 Funkce Round-Trip může být vypnuta buď nastavením `ignoreExtensionDataObject` na `true` v <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, nebo nastavením vlastnosti na hodnotu <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> `true` v <xref:System.ServiceModel.ServiceBehaviorAttribute> . Když je tato funkce vypnutá, odsadí Nástroj pro deserializaci <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost a serializátor negeneruje obsah vlastnosti.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Správa verzí kontraktů dat](data-contract-versioning.md)
- [Osvědčené postupy: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md)
