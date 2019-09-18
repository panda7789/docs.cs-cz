---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5dc23f5105b589d5b74c9ea6b7f40b84c2b04e6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046155"
---
# <a name="stack-etw-event"></a>Událost Trasování událostí pro Windows zásobníku
Událost zásobníku by měla být použita ve spojení s jinými událostmi k vygenerování trasování zásobníku po vyvolání události. Je zaznamenána v případě, že je povolen zprostředkovatel modulu runtime. Jedná se o velmi vysokou frekvenci, protože se vyvolá při každém vyvolání jiné běhové události. Z tohoto důvodu doporučujeme, abyste tuto událost používali opatrně.  
  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Level|  
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
|Rámec|win:Pointer|Sloupce ukazatelů instrukcí.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
