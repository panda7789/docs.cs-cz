---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128959"
---
# <a name="threading-objects-and-features"></a>Dělení objektů a funkcí na vlákna

Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídou .NET poskytuje řadu tříd, které vám pomohou vyvíjet aplikace s více vlákny. Následující články poskytují přehled těchto tříd:

|Nadpis|Popis|  
|-----------|-----------------|  
|[Spravovaný fond vláken](the-managed-thread-pool.md)|Popisuje třídu, <xref:System.Threading.ThreadPool?displayProperty=nameWithType> která poskytuje fond pracovních podprocesů, které jsou spravovány rozhraním .NET.|  
|[Časovače](timers.md)|Popisuje časovače rozhraní .NET, které lze použít v prostředí s více vlákny.|
|[Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)|Popisuje typy, které lze použít k synchronizaci přístupu ke sdílenému prostředku nebo ovládacímu vláknu.|
|[EventWaitHandle](eventwaithandle.md)|Popisuje třídu, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> která představuje událost synchronizace vláken.|
|[CountdownEvent](countdownevent.md)|Popisuje třídu, <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> která představuje událost synchronizace vláken, která se nastaví, když je její počet nula.|
|[Mutex – třídy](mutexes.md)|Popisuje třídu, <xref:System.Threading.Mutex?displayProperty=nameWithType> která uděluje výhradní přístup ke sdílenému prostředku.|
|[Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md)|Popisuje třídu, <xref:System.Threading.Semaphore?displayProperty=nameWithType> která omezuje počet podprocesů, které mají přístup ke sdílenému prostředku nebo fondu prostředků současně.|
|[Bariéra](barrier.md)|Popisuje třídu, <xref:System.Threading.Barrier?displayProperty=nameWithType> která implementuje bariérový vzor pro koordinaci vláken v postupných operacích.|
|[SpinLock](spinlock.md)|Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturu, která je zjednodušenou <xref:System.Threading.Monitor?displayProperty=nameWithType> alternativou ke třídě pro určité scénáře uzamčení nižší úrovně.|
|[SpinWait](spinwait.md)|Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturu, která poskytuje podporu pro čekání na základě spin.|

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
- [Asynchronní I/O soubory](../io/asynchronous-file-i-o.md)
- [Paralelní programování](../parallel-programming/index.md)
- [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)
