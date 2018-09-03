---
title: Práce s vlákny funkce a objekty
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483655"
---
# <a name="threading-objects-and-features"></a>Práce s vlákny funkce a objekty

Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídy .NET poskytuje několik tříd, které umožňují vývoj aplikací s více vlákny. Následující články poskytují přehled těchto tříd:

|Název|Popis|  
|-----------|-----------------|  
|[Spravovaný fond vláken](the-managed-thread-pool.md)|Popisuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType> třídu, která poskytuje fondu pracovních vláken, které se spravují přes rozhraní .NET.|  
|[Časovače](timers.md)|Popisuje časovače, které lze použít v prostředí s více vlákny.|
|[Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)|Popisuje třídy, které slouží k synchronizaci přístupu k data nebo ovládací prvek interakce vlákna.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|Popisuje obslužné rutiny čekání spravované události, které se používají k synchronizaci aktivity vláken signalizace a čeká na signál.|
|[Mutex – třídy](mutexes.md)|Popisuje způsob použití <xref:System.Threading.Mutex?displayProperty=nameWithType> k synchronizaci přístupu k objektu nebo vytvářet vlastní mechanismy synchronizace.|
|[Propojené operace](interlocked-operations.md)|Popisuje <xref:System.Threading.Interlocked?displayProperty=nameWithType> třídu, která poskytuje atomických operací pro proměnné, které jsou sdíleny více vlákny.|
|[Zámky modulů pro čtení a zápis](reader-writer-locks.md)|Popisuje <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> třídu, která poskytne tak sémantiku single zapisovače/více reader.|
|[Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md)|Popisuje <xref:System.Threading.Semaphore?displayProperty=nameWithType> třídy a vysvětluje, jak ho použít k řízení přístupu k prostředkům omezené.|
|[Barrier](barrier.md)|Popisuje <xref:System.Threading.Barrier?displayProperty=nameWithType> třídu, která implementuje vzor barrier koordinace vláken v postupné operacích.|
|[SpinLock](spinlock.md)|Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> třídu, která představuje jednoduché alternativa <xref:System.Threading.Monitor?displayProperty=nameWithType> třídy pro určité scénáře nízké úrovně.|
|[SpinWait](spinwait.md)|Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> třídu, která je nižší úrovně primitiv synchronizace, který provádí zaneprázdnění před zahajuje čekání na základě jádra.|

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
