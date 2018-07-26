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
# <a name="threading-objects-and-features"></a><span data-ttu-id="ab74f-102">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="ab74f-102">Threading Objects and Features</span></span>
<span data-ttu-id="ab74f-103">Rozhraní .NET Framework poskytuje mnoho objektů, které vám pomůžou vytvářet a spravovat aplikace s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="ab74f-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="ab74f-104">Spravovaná vlákna jsou reprezentovány <xref:System.Threading.Thread> třídy.</span><span class="sxs-lookup"><span data-stu-id="ab74f-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="ab74f-105"><xref:System.Threading.ThreadPool> Třída umožňuje snadné vytváření a správu úloh na pozadí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="ab74f-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="ab74f-106"><xref:System.ComponentModel.BackgroundWorker> Třídy dělá to samé pro úlohy, které pracují s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="ab74f-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="ab74f-107"><xref:System.Threading.Timer> Třídy spouští úlohy na pozadí v časových intervalech.</span><span class="sxs-lookup"><span data-stu-id="ab74f-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="ab74f-108">Kromě toho existuje několik tříd, které se synchronizují aktivity vláken, včetně <xref:System.Threading.Semaphore> a <xref:System.Threading.EventWaitHandle> třídy zavedené v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="ab74f-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ab74f-109">Porovnání funkcí těchto tříd v [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="ab74f-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab74f-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ab74f-110">In This Section</span></span>  
 [<span data-ttu-id="ab74f-111">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="ab74f-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="ab74f-112">Vysvětluje, **fondu vláken** třídu, která umožňuje požádat o vlákno spustit úlohu, aniž byste museli provést jakékoli vlákno správu sami.</span><span class="sxs-lookup"><span data-stu-id="ab74f-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="ab74f-113">Časovače</span><span class="sxs-lookup"><span data-stu-id="ab74f-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="ab74f-114">Popisuje časovače, které lze použít v prostředí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="ab74f-114">Describes timers that can be used in a multithreaded environment.</span></span>  
  
 [<span data-ttu-id="ab74f-115">Monitorování</span><span class="sxs-lookup"><span data-stu-id="ab74f-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="ab74f-116">Vysvětluje způsob používání **monitorování** třídy k synchronizaci přístupu k člena nebo vytvářet vlastní vlákno typy správy.</span><span class="sxs-lookup"><span data-stu-id="ab74f-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="ab74f-117">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="ab74f-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="ab74f-118">Popisuje <xref:System.Threading.WaitHandle> třídy, abstraktní základní třída pro událost počkejte obslužné rutiny, vzájemně vyloučené přístupy a semafory, které umožňují čekání na více událostí synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ab74f-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="ab74f-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="ab74f-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="ab74f-120">Popisuje obslužné rutiny čekání spravované události, které se používají k synchronizaci aktivity vláken signalizace a čeká na signál.</span><span class="sxs-lookup"><span data-stu-id="ab74f-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="ab74f-121">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="ab74f-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="ab74f-122">Vysvětluje způsob používání <xref:System.Threading.Mutex> k synchronizaci přístupu k objektu nebo vytvářet vlastní mechanismy synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ab74f-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="ab74f-123">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="ab74f-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="ab74f-124">Vysvětluje způsob používání <xref:System.Threading.Interlocked> třídy zvýší nebo sníží hodnotu a uložte hodnotu v jediné atomické operaci.</span><span class="sxs-lookup"><span data-stu-id="ab74f-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="ab74f-125">Zámky modulů pro čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="ab74f-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="ab74f-126">Definuje zámek, který implementuje sémantiku single zapisovače/více reader.</span><span class="sxs-lookup"><span data-stu-id="ab74f-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="ab74f-127">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="ab74f-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="ab74f-128">Popisuje <xref:System.Threading.Semaphore> objektů a vysvětluje, jak se dají použít k řízení přístupu k prostředkům omezené.</span><span class="sxs-lookup"><span data-stu-id="ab74f-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="ab74f-129">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="ab74f-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="ab74f-130">Obsahuje porovnání funkcí tříd rozhraní .NET Framework poskytuje pro uzamčení a synchronizaci spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="ab74f-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="ab74f-131">Barrier</span><span class="sxs-lookup"><span data-stu-id="ab74f-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="ab74f-132">Popisuje <xref:System.Threading.Barrier> objekty, které implementují vzor barrier koordinace vláken v postupné operacích.</span><span class="sxs-lookup"><span data-stu-id="ab74f-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="ab74f-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="ab74f-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="ab74f-134">Popisuje <xref:System.Threading.SpinLock>, zjednodušené alternativou k třídě monitorování pro určité scénáře nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="ab74f-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="ab74f-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="ab74f-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="ab74f-136">Popisuje <xref:System.Threading.SpinWait>, synchronizace na nízké úrovni jednoduchého typu, který provádí zaneprázdnění před zahajuje čekání na základě jádra.</span><span class="sxs-lookup"><span data-stu-id="ab74f-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ab74f-137">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ab74f-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="ab74f-138">Poskytuje referenční dokumentaci pro **vlákno** třídu, která představuje spravované vlákno, ať už pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ab74f-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ab74f-139">Umožňuje úlohy na pozadí, které pracují s uživatelským rozhraním, komunikace prostřednictvím událostí vyvolaných ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab74f-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab74f-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ab74f-140">Related Sections</span></span>  
 [<span data-ttu-id="ab74f-141">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="ab74f-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="ab74f-142">Popisuje použití fondu vláken portů dokončení asynchronních vstupně-výstupních operací tak, aby vyžadovala zpracování pouze v případě, že dokončení vstupně výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="ab74f-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="ab74f-143">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="ab74f-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="ab74f-144">Popisuje doporučený postup pro programování s více vlákny v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="ab74f-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
