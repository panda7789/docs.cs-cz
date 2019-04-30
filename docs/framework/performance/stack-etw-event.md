---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949146"
---
# <a name="stack-etw-event"></a>Událost Trasování událostí pro Windows zásobníku
Událost zásobníku by měl použít ve spojení s jinými událostmi ke generování trasování zásobníku, poté, co je vyvolána událost. Je zaznamenána, pokud je povolen zprostředkovatel běhového prostředí. To je velmi vysoká frekvence událostí, vzhledem k tomu, že je vyvolána pokaždé, když se jiný modul runtime událost se vyvolá. Z tohoto důvodu doporučujeme použít tuto událost opatrně.  
  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Ve spojení s jinými událostmi generovat následující událost trasování zásobníku.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Windows: Uint16|Identifikátor modulu runtime jedinečný.|  
|Reserved1|win:UInt8|Vyhrazená.|  
|Vyhrazeno2|win:UInt8|Vyhrazená.|  
|Hodnoty FrameCount|win:UInt32|Počet rámců v zásobníku.|  
|Rámec|win:Pointer|Sloupce ukazatele na instrukce.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
