---
title: Základy dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139233"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="b3b83-102">Základy spravovaného podprocesu</span><span class="sxs-lookup"><span data-stu-id="b3b83-102">Managed threading basics</span></span>

<span data-ttu-id="b3b83-103">Prvních pět témat této části je navrženo tak, aby vám pomohla určit, kdy použít spravované podprocesy, a vysvětlit některé základní funkce.</span><span class="sxs-lookup"><span data-stu-id="b3b83-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="b3b83-104">Informace o třídách, které poskytují další funkce, naleznete v [tématu Objekty zřetězení a prvky](../../../docs/standard/threading/threading-objects-and-features.md) a [Přehled primitivnísynchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="b3b83-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="b3b83-105">Ostatní témata v této části pokrývají pokročilá témata, včetně interakce spravovaného podprocesu s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="b3b83-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3b83-106">V rozhraní .NET Framework 4 poskytují paralelní knihovna úloh a PLINQ rozhraní API pro paralelismus úloh a dat v programech s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="b3b83-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="b3b83-107">Další informace naleznete [v tématu Paralelní programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3b83-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3b83-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b3b83-108">In this section</span></span>

 [<span data-ttu-id="b3b83-109">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="b3b83-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="b3b83-110">Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých můžete vytvořit vlákna nebo použít vlákna fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b3b83-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="b3b83-111">Výjimky ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="b3b83-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="b3b83-112">Popisuje chování neošetřených výjimek ve vláknech pro různé verze rozhraní .NET Framework, zejména v situacích, ve kterých mají za následek ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3b83-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="b3b83-113">Synchronizace dat pro vícevláknové zpracování</span><span class="sxs-lookup"><span data-stu-id="b3b83-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="b3b83-114">Popisuje strategie pro synchronizaci dat ve třídách, které budou použity s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="b3b83-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="b3b83-115">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="b3b83-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="b3b83-116">Vysvětluje rozdíly mezi popředí a podprocesů na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b3b83-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="b3b83-117">Dělení na spravovaná a nespravovaná vlákna ve Windows</span><span class="sxs-lookup"><span data-stu-id="b3b83-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="b3b83-118">Popisuje vztah mezi spravovaným a nespravovaným podprocesem, uvádí spravované ekvivalenty pro rozhraní API pro podprocesy systému Windows a popisuje interakci komoda a spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="b3b83-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="b3b83-119">Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům</span><span class="sxs-lookup"><span data-stu-id="b3b83-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="b3b83-120">Popisuje mechanismy úložiště relativní k vláknu.</span><span class="sxs-lookup"><span data-stu-id="b3b83-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3b83-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="b3b83-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="b3b83-122">Poskytuje referenční dokumentaci pro třídu **Thread,** která představuje spravované vlákno, zda pochází z nespravovaného kódu nebo byla vytvořena ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b3b83-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b3b83-123">Poskytuje bezpečný způsob implementace multithreading ve spojení s objekty uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3b83-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3b83-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b3b83-124">Related sections</span></span>

 [<span data-ttu-id="b3b83-125">Přehled základních synchronizačních zařízení</span><span class="sxs-lookup"><span data-stu-id="b3b83-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="b3b83-126">Popisuje spravované třídy používané k synchronizaci aktivit více vláken.</span><span class="sxs-lookup"><span data-stu-id="b3b83-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="b3b83-127">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="b3b83-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="b3b83-128">Popisuje běžné problémy s multithreading a strategie pro předcházení problémům.</span><span class="sxs-lookup"><span data-stu-id="b3b83-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="b3b83-129">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="b3b83-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="b3b83-130">Popisuje paralelní knihovnu úloh a PLINQ, které výrazně zjednodušují práci při vytváření asynchronních a vícevláknových aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3b83-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
