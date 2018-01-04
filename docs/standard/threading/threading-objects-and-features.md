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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cb36c004c46e22256928b3b2432da59fb3e6fa2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="0a2db-102">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="0a2db-102">Threading Objects and Features</span></span>
<span data-ttu-id="0a2db-103">Rozhraní .NET Framework poskytuje mnoho objektů, které vám pomůžou vytvářet a spravovat vícevláknové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a2db-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="0a2db-104">Spravovaných vláknech jsou reprezentované pomocí <xref:System.Threading.Thread> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a2db-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="0a2db-105"><xref:System.Threading.ThreadPool> Třída poskytuje snadné vytváření a Správa úloh na pozadí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="0a2db-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="0a2db-106"><xref:System.ComponentModel.BackgroundWorker> Třída nemá stejný pro úlohy, které zajišťují interakci s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="0a2db-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="0a2db-107"><xref:System.Threading.Timer> Třída spustí úlohy na pozadí v určitých intervalech.</span><span class="sxs-lookup"><span data-stu-id="0a2db-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="0a2db-108">Kromě toho existuje několik tříd, které se synchronizují aktivity vláken, včetně <xref:System.Threading.Semaphore> a <xref:System.Threading.EventWaitHandle> třídy zavedené v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="0a2db-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0a2db-109">Funkce tyto třídy jsou porovnávány v [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="0a2db-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a2db-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a2db-110">In This Section</span></span>  
 [<span data-ttu-id="0a2db-111">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="0a2db-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="0a2db-112">Vysvětluje **zachovalo** třídy, která umožňuje žádost vlákno k provedení úlohy bez nutnosti jakékoli správy vláken sami.</span><span class="sxs-lookup"><span data-stu-id="0a2db-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="0a2db-113">Časovače</span><span class="sxs-lookup"><span data-stu-id="0a2db-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="0a2db-114">Vysvětluje, jak používat **časovače** k určení delegáta, kterého se volat v zadanou dobu.</span><span class="sxs-lookup"><span data-stu-id="0a2db-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="0a2db-115">Monitorování</span><span class="sxs-lookup"><span data-stu-id="0a2db-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="0a2db-116">Vysvětluje, jak používat **monitorování** třída k synchronizaci přístup na člena, nebo vytvořit vlastní vlákno typy správy.</span><span class="sxs-lookup"><span data-stu-id="0a2db-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="0a2db-117">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="0a2db-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="0a2db-118">Popisuje <xref:System.Threading.WaitHandle> třída, počkejte abstraktní základní třída pro událost obslužné rutiny, mutex – třídy a semaforů, které umožňuje čeká na více událostí synchronizace.</span><span class="sxs-lookup"><span data-stu-id="0a2db-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="0a2db-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="0a2db-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="0a2db-120">Popisuje obslužné rutiny čekání spravované události, které slouží k synchronizaci aktivity vlákno signalizace a čekání signály.</span><span class="sxs-lookup"><span data-stu-id="0a2db-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="0a2db-121">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="0a2db-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="0a2db-122">Vysvětluje, jak používat <xref:System.Threading.Mutex> k synchronizaci přístup k objektu nebo vytvořit vlastní mechanismy synchronizace.</span><span class="sxs-lookup"><span data-stu-id="0a2db-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="0a2db-123">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="0a2db-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="0a2db-124">Vysvětluje, jak používat <xref:System.Threading.Interlocked> třída zvýší nebo sníží hodnotu a uložit hodnotu v rámci jedné atomické operace.</span><span class="sxs-lookup"><span data-stu-id="0a2db-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="0a2db-125">Zámky modulů pro čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="0a2db-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="0a2db-126">Definuje zámku, která implementuje sémantiku single zapisovače nebo více čtecími.</span><span class="sxs-lookup"><span data-stu-id="0a2db-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="0a2db-127">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="0a2db-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="0a2db-128">Popisuje <xref:System.Threading.Semaphore> objekty a vysvětluje, jak je používat k řízení přístupu k prostředků omezené.</span><span class="sxs-lookup"><span data-stu-id="0a2db-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="0a2db-129">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="0a2db-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="0a2db-130">Porovnává funkce tříd rozhraní .NET Framework poskytuje pro zamykání a synchronizace spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="0a2db-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="0a2db-131">Barrier</span><span class="sxs-lookup"><span data-stu-id="0a2db-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="0a2db-132">Popisuje <xref:System.Threading.Barrier> objekty, které implementovat bariéry vzor pro koordinaci vláken v postupné operacích.</span><span class="sxs-lookup"><span data-stu-id="0a2db-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="0a2db-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="0a2db-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="0a2db-134">Popisuje <xref:System.Threading.SpinLock>, lightweight alternativa k třídě monitorování pro určité scénáře nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="0a2db-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="0a2db-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="0a2db-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="0a2db-136">Popisuje <xref:System.Threading.SpinWait>, nízkou úroveň synchronizace primitivní, který provádí zaneprázdnění před zahájením čekání základě jádra.</span><span class="sxs-lookup"><span data-stu-id="0a2db-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a2db-137">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0a2db-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="0a2db-138">Poskytuje referenční dokumentaci pro **vlákno** třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0a2db-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="0a2db-139">Umožňuje úlohy na pozadí, které zajišťují interakci s uživatelským rozhraním, komunikaci přes události vyvolané vlákna uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0a2db-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a2db-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0a2db-140">Related Sections</span></span>  
 [<span data-ttu-id="0a2db-141">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="0a2db-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="0a2db-142">Popisuje, jak porty vstupně-výstupní operace asynchronní dokončení použít fondu vláken tak, aby vyžadovala zpracování jenom v případě, že dokončení vstupně výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="0a2db-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="0a2db-143">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="0a2db-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="0a2db-144">Popisuje, o doporučený postup pro vícevláknové programování v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="0a2db-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
