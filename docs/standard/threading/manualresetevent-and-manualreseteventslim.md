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
ms.openlocfilehash: d69336bd9e4f4ec06e8319d19c1cdab5cf6e1c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583315"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent a ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída reprezentuje událost popisovač místní čekání, která musí být ručně obnovit, jakmile to bylo signalizováno. Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce ručně resetovat události.  
  
 A <xref:System.Threading.ManualResetEvent> objekt zůstane signalizovaného dokud jeho <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda je volána. Libovolný počet čekajících vláken nebo vláken, která čekat na události po byla signál, můžete vydala, zatímco signalizace stav objektu. <xref:System.Threading.ManualResetEvent> odpovídá Win32 `CreateEvent` volání, zadání `true` pro `bManualReset` argument.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> třídy pro lepší výkon, pokud očekávané velmi krátké době čekání a pokud událost nekříží hranice procesu. <xref:System.Threading.ManualResetEventSlim> používá zaneprázdněn otáčí po krátkou dobu, kdy čeká stát signál události. Po krátkou dobu čekání se může být roztočený mnohem míň nákladné než čekání pomocí obslužných rutin čekání. Ale pokud událost stane signál není v rámci určité doby běhu <xref:System.Threading.ManualResetEventSlim> používat popisovač čekání pravidelné události.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
