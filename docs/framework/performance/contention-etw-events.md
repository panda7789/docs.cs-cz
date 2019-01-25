---
title: Kolizní události Trasování událostí pro Windows
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575564"
---
# <a name="contention-etw-events"></a>Kolizní události Trasování událostí pro Windows
Kolizní události jsou vyvolány pokaždé, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> uzamčení nebo nativní zámky modulem runtime. Kolize nastane, pokud vlákno čeká na zámek a jiné vlákno drží zámek.  
  
 V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány události kolize a úroveň události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Kolize spustí. Tato událost nezahrnuje množství zprovozňování dobu, než vlákno čeká na získání zámku; je aktivována pouze v případě, že vlákno čeká na získání zámku.|  
|`ContentionStop`|81|Kolize skončí.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Příznaky|win:UInt8|0 pro spravované; 1 pro nativní.|  
|ClrInstanceID|win:UInt16|Jedinečné ID pro instanci modulu CLR.|  
  
## <a name="see-also"></a>Viz také:
- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
