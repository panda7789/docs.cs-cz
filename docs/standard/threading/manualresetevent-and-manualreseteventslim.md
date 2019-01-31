---
title: ManualResetEvent a ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49af405c7954f18e6f59264182a9a67a0be35d3d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279185"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent a ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída představuje, které musí obnovit ručně po to bylo signalizováno událost popisovač místní čekání. Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce ruční obnovení události.  
  
 A <xref:System.Threading.ManualResetEvent> objekt zůstane až do signalizovaného jeho <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda je volána. Libovolný počet čekajících vláken, nebo vlákna, která čekání na událost po byl signalizován, mohou být vydány, zatímco signalizován stav objektu.
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> třídy pro zajištění lepšího výkonu při jsou velmi krátké doby čekání a události přes hranice procesu. <xref:System.Threading.ManualResetEventSlim> používá zaneprázdněný, zprovozňování krátkou dobu, kdy čeká signálování události. Po krátkou dobu čekání se může být zaneprázdnění mnohem levnější než čekání pomocí obslužné rutiny čekání. Nicméně, pokud není stát signalizovanými události v rámci určité časové období <xref:System.Threading.ManualResetEventSlim> používat normální událost popisovač čekání.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>
- [SpinWait](spinwait.md)
- [Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md)
- [Eventwaithandle – CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
- [Dělení na vlákna](index.md)
