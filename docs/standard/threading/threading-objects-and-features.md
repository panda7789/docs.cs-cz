---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128959"
---
# <a name="threading-objects-and-features"></a>Dělení objektů a funkcí na vlákna

Společně s třídou <xref:System.Threading.Thread?displayProperty=nameWithType> poskytuje .NET řadu tříd, které vám pomůžou vyvíjet aplikace s více vlákny. Následující články poskytují přehled těchto tříd:

|Název|Popis|  
|-----------|-----------------|  
|[Spravovaný fond vláken](the-managed-thread-pool.md)|Popisuje třídu <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, která poskytuje fond pracovních vláken spravovaných technologií .NET.|  
|[Časovače](timers.md)|Popisuje časovače .NET, které lze použít ve vícevláknovém prostředí.|
|[Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)|Popisuje typy, které lze použít k synchronizaci přístupu k interakci sdíleného vlákna prostředku nebo ovládacího prvku.|
|[EventWaitHandle](eventwaithandle.md)|Popisuje třídu <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, která představuje událost synchronizace vlákna.|
|[CountdownEvent](countdownevent.md)|Popisuje třídu <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, která představuje událost synchronizace vlákna, která se nastaví, když je její počet nula.|
|[Mutex – třídy](mutexes.md)|Popisuje třídu <xref:System.Threading.Mutex?displayProperty=nameWithType>, která uděluje exkluzivní přístup ke sdílenému prostředku.|
|[Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md)|Popisuje třídu <xref:System.Threading.Semaphore?displayProperty=nameWithType>, která omezuje počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků.|
|[Barrier](barrier.md)|Popisuje třídu <xref:System.Threading.Barrier?displayProperty=nameWithType>, která implementuje vzor bariéry pro koordinaci vláken v rámci dvoufázové operace.|
|[SpinLock](spinlock.md)|V této části najdete popis <xref:System.Threading.SpinLock?displayProperty=nameWithType> struktury, což je zjednodušená alternativa ke třídě <xref:System.Threading.Monitor?displayProperty=nameWithType> pro určité scénáře zamykání nízké úrovně.|
|[SpinWait](spinwait.md)|Popisuje strukturu <xref:System.Threading.SpinWait?displayProperty=nameWithType>, která poskytuje podporu pro čekání na číselník.|

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
- [Asynchronní vstupně-výstupní operace se soubory](../io/asynchronous-file-i-o.md)
- [Paralelní programování](../parallel-programming/index.md)
- [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)
