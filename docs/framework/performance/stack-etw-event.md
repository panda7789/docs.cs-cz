---
title: "Událost Trasování událostí pro Windows zásobníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a>Událost Trasování událostí pro Windows zásobníku
Událost zásobníku by používána v kombinaci s jinými událostmi ke generování trasování zásobníku po událost se vyvolá. Je zaznamenána, pokud je povolen zprostředkovatel modulu runtime. Toto je velmi vysoká frekvence událost, protože se vyvolá, vždy, když se jiný modul runtime událost se vyvolá. Z tohoto důvodu doporučujeme používat tato událost se zvýšenou opatrností.  
  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`StackKeyword`(0x40000000)|LogAlways(0)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Ve spojení s jinými událostmi ke generování následující událost trasování zásobníku.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: Uint16|Modul runtime jedinečný identifikátor.|  
|Reserved1|Win: UInt8|Vyhrazena.|  
|Vyhrazeno2|Win: UInt8|Vyhrazena.|  
|FrameCount|Win: UInt32|Počet rámců v trasování zásobníku.|  
|Rámec|Win: ukazatele|Sloupce ukazatele na instrukce.|  
  
## <a name="see-also"></a>Viz také  
 [CLR ETW – události](../../../docs/framework/performance/clr-etw-events.md)
