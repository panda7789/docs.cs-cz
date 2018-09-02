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
ms.openlocfilehash: f4a6950d17fef60298a2e47b63bec068554b2b8b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390498"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent a ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída představuje, které musí obnovit ručně po to bylo signalizováno událost popisovač místní čekání. Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce ruční obnovení události.  
  
 A <xref:System.Threading.ManualResetEvent> objekt zůstane až do signalizovaného jeho <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda je volána. Libovolný počet čekajících vláken, nebo vlákna, která čekání na událost po byl signalizován, mohou být vydány, zatímco signalizován stav objektu. <xref:System.Threading.ManualResetEvent> odpovídá Win32 `CreateEvent` volání, určení `true` pro `bManualReset` argument.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> třídy pro zajištění lepšího výkonu při jsou velmi krátké doby čekání a události přes hranice procesu. <xref:System.Threading.ManualResetEventSlim> používá zaneprázdněný, zprovozňování krátkou dobu, kdy čeká signálování události. Po krátkou dobu čekání se může být zaneprázdnění mnohem levnější než čekání pomocí obslužné rutiny čekání. Nicméně, pokud není stát signalizovanými události v rámci určité časové období <xref:System.Threading.ManualResetEventSlim> používat normální událost popisovač čekání.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Obslužné rutiny čekání](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
