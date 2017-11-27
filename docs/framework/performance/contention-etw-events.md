---
title: "Kolizní události Trasování událostí pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a>Kolizní události Trasování událostí pro Windows
Kolizní události jsou vyvolány vždy, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používá modulem runtime. Kolize nastane, když je při jiné vlákno má zámek vlákno čekání na zámek.  
  
 V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány kolizní události a úroveň události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ContentionKeyword`(0x4000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Kolizní spustí. Tato událost nezahrnuje množství otáčí dobu, než je vlákno čeká na získání zámku; je vyvolána, pouze v případě, že vlákno čeká na získání zámku.|  
|`ContentionStop`|81|Kolizní ukončí.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Příznaky|Win: UInt8|0 pro spravované; 1 pro nativní.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR.|  
  
## <a name="see-also"></a>Viz také  
 [CLR ETW – události](../../../docs/framework/performance/clr-etw-events.md)
