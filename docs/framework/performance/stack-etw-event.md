---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: f3014a04ba7cacbe37b6706e2919ffd7de19aa65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715910"
---
# <a name="stack-etw-event"></a>Událost Trasování událostí pro Windows zásobníku
Událost zásobníku by měla být použita ve spojení s jinými událostmi k vygenerování trasování zásobníku po vyvolání události. Je zaznamenána v případě, že je povolen zprostředkovatel modulu runtime. Jedná se o velmi vysokou frekvenci, protože se vyvolá při každém vyvolání jiné běhové události. Z tohoto důvodu doporučujeme, abyste tuto událost používali opatrně.  
  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways (0)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Ve spojení s dalšími událostmi pro generování trasování zásobníku za událostí.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: Uint16|Jedinečný identifikátor modulu runtime.|  
|Reserved1|Win: UInt8|Rezervovaný.|  
|Reserved2|Win: UInt8|Rezervovaný.|  
|FrameCount|Win: UInt32|Počet snímků v trasování zásobníku.|  
|Zásobník|win:Pointer|Sloupce ukazatelů instrukcí.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
