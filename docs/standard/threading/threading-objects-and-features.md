---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25609bc3c4dd829c66a1a4514b7f1121f9c0909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940930"
---
# <a name="threading-objects-and-features"></a>Dělení objektů a funkcí na vlákna

Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídy .NET poskytuje několik tříd, které umožňují vývoj aplikací s více vlákny. Následující články poskytují přehled těchto tříd:

|Název|Popis|  
|-----------|-----------------|  
|[Spravovaný fond vláken](the-managed-thread-pool.md)|Popisuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType> třídu, která poskytuje fondu pracovních vláken, které se spravují přes rozhraní .NET.|  
|[Časovače](timers.md)|Popisuje .NET časovače, které lze použít v prostředí s více vlákny.|
|[Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)|Popisuje typy, které slouží k synchronizaci přístupu k sdíleného prostředku nebo vlákna interakce ovládacího prvku.|
|[EventWaitHandle](eventwaithandle.md)|Popisuje <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> třídu, která představuje událost synchronizace vlákna.|
|[CountdownEvent](countdownevent.md)|Popisuje <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> třídu, která představuje událost synchronizace podproces, který bude nastaven při její vlastnosti count je nula.|
|[Mutex – třídy](mutexes.md)|Popisuje <xref:System.Threading.Mutex?displayProperty=nameWithType> třídu, která udělí se výhradní přístup ke sdíleným prostředkům.|
|[Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md)|Popisuje <xref:System.Threading.Semaphore?displayProperty=nameWithType> třídu, která omezuje počet vláken, které můžete přístup ke sdílenému prostředku nebo fond prostředků současně.|
|[Barrier](barrier.md)|Popisuje <xref:System.Threading.Barrier?displayProperty=nameWithType> třídy, která implementuje vzor barrier koordinace vláken v postupné operacích.|
|[SpinLock](spinlock.md)|Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturu, která představuje jednoduché alternativa <xref:System.Threading.Monitor?displayProperty=nameWithType> třídy pro určité scénáře nízké úrovně zamykání.|
|[SpinWait](spinwait.md)|Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturu, která poskytuje podporu pro čekání na základě typu číselník.|

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
