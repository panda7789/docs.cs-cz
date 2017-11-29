---
title: "Dělení objektů a funkcí na vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a>Dělení objektů a funkcí na vlákna
Rozhraní .NET Framework poskytuje mnoho objektů, které vám pomůžou vytvářet a spravovat vícevláknové aplikace. Spravovaných vláknech jsou reprezentované pomocí <xref:System.Threading.Thread> třídy. <xref:System.Threading.ThreadPool> Třída poskytuje snadné vytváření a Správa úloh na pozadí s více vlákny. <xref:System.ComponentModel.BackgroundWorker> Třída nemá stejný pro úlohy, které zajišťují interakci s uživatelským rozhraním. <xref:System.Threading.Timer> Třída spustí úlohy na pozadí v určitých intervalech.  
  
 Kromě toho existuje několik tříd, které se synchronizují aktivity vláken, včetně <xref:System.Threading.Semaphore> a <xref:System.Threading.EventWaitHandle> třídy zavedené v rozhraní .NET Framework verze 2.0. Funkce tyto třídy jsou porovnávány v [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spravovaný fond vláken](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Vysvětluje **zachovalo** třídy, která umožňuje žádost vlákno k provedení úlohy bez nutnosti jakékoli správy vláken sami.  
  
 [Časovače](../../../docs/standard/threading/timers.md)  
 Vysvětluje, jak používat **časovače** k určení delegáta, kterého se volat v zadanou dobu.  
  
 [Monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Vysvětluje, jak používat **monitorování** třída k synchronizaci přístup na člena, nebo vytvořit vlastní vlákno typy správy.  
  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Popisuje <xref:System.Threading.WaitHandle> třída, počkejte abstraktní základní třída pro událost obslužné rutiny, mutex – třídy a semaforů, které umožňuje čeká na více událostí synchronizace.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Popisuje obslužné rutiny čekání spravované události, které slouží k synchronizaci aktivity vlákno signalizace a čekání signály.  
  
 [Mutex – třídy](../../../docs/standard/threading/mutexes.md)  
 Vysvětluje, jak používat <xref:System.Threading.Mutex> k synchronizaci přístup k objektu nebo vytvořit vlastní mechanismy synchronizace.  
  
 [Propojené operace](../../../docs/standard/threading/interlocked-operations.md)  
 Vysvětluje, jak používat <xref:System.Threading.Interlocked> třída zvýší nebo sníží hodnotu a uložit hodnotu v rámci jedné atomické operace.  
  
 [Čtení a zápis zámky.](../../../docs/standard/threading/reader-writer-locks.md)  
 Definuje zámku, která implementuje sémantiku single zapisovače nebo více čtecími.  
  
 [Semafor a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Popisuje <xref:System.Threading.Semaphore> objekty a vysvětluje, jak je používat k řízení přístupu k prostředků omezené.  
  
 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Porovnává funkce tříd rozhraní .NET Framework poskytuje pro zamykání a synchronizace spravovaných vláken.  
  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 Popisuje <xref:System.Threading.Barrier> objekty, které implementovat bariéry vzor pro koordinaci vláken v postupné operacích.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Popisuje <xref:System.Threading.SpinLock>, lightweight alternativa k třídě monitorování pro určité scénáře nižší úrovně.  
  
 [Objektu SpinWait](../../../docs/standard/threading/spinwait.md)  
 Popisuje <xref:System.Threading.SpinWait>, nízkou úroveň synchronizace primitivní, který provádí zaneprázdnění před zahájením čekání základě jádra.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro **vlákno** třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Umožňuje úlohy na pozadí, které zajišťují interakci s uživatelským rozhraním, komunikaci přes události vyvolané vlákna uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje, jak porty vstupně-výstupní operace asynchronní dokončení použít fondu vláken tak, aby vyžadovala zpracování jenom v případě, že dokončení vstupně výstupní operace.  
  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Popisuje, o doporučený postup pro vícevláknové programování v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a novější.
