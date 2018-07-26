---
title: Dělení objektů a funkcí na vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d689aeb91ad79b776c3b93c1809ec46947ea60b
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874784"
---
# <a name="threading-objects-and-features"></a>Dělení objektů a funkcí na vlákna
Rozhraní .NET Framework poskytuje mnoho objektů, které vám pomůžou vytvářet a spravovat aplikace s více vlákny. Spravovaná vlákna jsou reprezentovány <xref:System.Threading.Thread> třídy. <xref:System.Threading.ThreadPool> Třída umožňuje snadné vytváření a správu úloh na pozadí s více vlákny. <xref:System.ComponentModel.BackgroundWorker> Třídy dělá to samé pro úlohy, které pracují s uživatelským rozhraním. <xref:System.Threading.Timer> Třídy spouští úlohy na pozadí v časových intervalech.  
  
 Kromě toho existuje několik tříd, které se synchronizují aktivity vláken, včetně <xref:System.Threading.Semaphore> a <xref:System.Threading.EventWaitHandle> třídy zavedené v rozhraní .NET Framework verze 2.0. Porovnání funkcí těchto tříd v [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spravovaný fond vláken](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Vysvětluje, **fondu vláken** třídu, která umožňuje požádat o vlákno spustit úlohu, aniž byste museli provést jakékoli vlákno správu sami.  
  
 [Časovače](../../../docs/standard/threading/timers.md)  
 Popisuje časovače, které lze použít v prostředí s více vlákny.  
  
 [Monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Vysvětluje způsob používání **monitorování** třídy k synchronizaci přístupu k člena nebo vytvářet vlastní vlákno typy správy.  
  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Popisuje <xref:System.Threading.WaitHandle> třídy, abstraktní základní třída pro událost počkejte obslužné rutiny, vzájemně vyloučené přístupy a semafory, které umožňují čekání na více událostí synchronizace.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Popisuje obslužné rutiny čekání spravované události, které se používají k synchronizaci aktivity vláken signalizace a čeká na signál.  
  
 [Mutex – třídy](../../../docs/standard/threading/mutexes.md)  
 Vysvětluje způsob používání <xref:System.Threading.Mutex> k synchronizaci přístupu k objektu nebo vytvářet vlastní mechanismy synchronizace.  
  
 [Propojené operace](../../../docs/standard/threading/interlocked-operations.md)  
 Vysvětluje způsob používání <xref:System.Threading.Interlocked> třídy zvýší nebo sníží hodnotu a uložte hodnotu v jediné atomické operaci.  
  
 [Zámky modulů pro čtení a zápis](../../../docs/standard/threading/reader-writer-locks.md)  
 Definuje zámek, který implementuje sémantiku single zapisovače/více reader.  
  
 [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Popisuje <xref:System.Threading.Semaphore> objektů a vysvětluje, jak se dají použít k řízení přístupu k prostředkům omezené.  
  
 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Obsahuje porovnání funkcí tříd rozhraní .NET Framework poskytuje pro uzamčení a synchronizaci spravovaných vláken.  
  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 Popisuje <xref:System.Threading.Barrier> objekty, které implementují vzor barrier koordinace vláken v postupné operacích.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Popisuje <xref:System.Threading.SpinLock>, zjednodušené alternativou k třídě monitorování pro určité scénáře nízké úrovně.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Popisuje <xref:System.Threading.SpinWait>, synchronizace na nízké úrovni jednoduchého typu, který provádí zaneprázdnění před zahajuje čekání na základě jádra.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro **vlákno** třídu, která představuje spravované vlákno, ať už pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Umožňuje úlohy na pozadí, které pracují s uživatelským rozhraním, komunikace prostřednictvím událostí vyvolaných ve vlákně uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje použití fondu vláken portů dokončení asynchronních vstupně-výstupních operací tak, aby vyžadovala zpracování pouze v případě, že dokončení vstupně výstupní operace.  
  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Popisuje doporučený postup pro programování s více vlákny v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a novější.
