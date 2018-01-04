---
title: "Základy dělení na spravovaná vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 035834959aa5f9340727327b22cae93b3f21b056
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="managed-threading-basics"></a><span data-ttu-id="2b864-102">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2b864-102">Managed Threading Basics</span></span>
<span data-ttu-id="2b864-103">Prvních pět témata v této části jsou navrženy pro vám pomohou určit, kdy používat spravovaného dělení na vlákna a vysvětlit některé základní funkce.</span><span class="sxs-lookup"><span data-stu-id="2b864-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="2b864-104">Informace o třídy, které poskytují další funkce, najdete v části [dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md) a [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="2b864-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="2b864-105">Zbývající témata v této části titulní rozšířené témata, včetně interakci spravovaného dělení na vlákna s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="2b864-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b864-106">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Task Parallel Library a PLINQ poskytují rozhraní API pro úlohy a datový paralelismus v vícevláknových programů.</span><span class="sxs-lookup"><span data-stu-id="2b864-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="2b864-107">Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b864-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b864-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2b864-108">In This Section</span></span>  
 [<span data-ttu-id="2b864-109">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2b864-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="2b864-110">Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých může vytvořit vláken nebo použít podprocesy z fondu podprocesů.</span><span class="sxs-lookup"><span data-stu-id="2b864-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="2b864-111">Výjimky ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="2b864-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="2b864-112">Popisuje chování neošetřenými výjimkami v vláken pro různé verze rozhraní .NET Framework, zejména situace, ve které vedou ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b864-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="2b864-113">Synchronizace dat pro vícevláknové zpracování</span><span class="sxs-lookup"><span data-stu-id="2b864-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="2b864-114">Popisuje strategie pro synchronizaci dat v třídy, které se použije s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="2b864-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="2b864-115">Stavy spravovaných vláken</span><span class="sxs-lookup"><span data-stu-id="2b864-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="2b864-116">Popisuje stavy základní vláken a vysvětluje, jak zjistit, zda je spuštěn vlákna.</span><span class="sxs-lookup"><span data-stu-id="2b864-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="2b864-117">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="2b864-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="2b864-118">Vysvětluje rozdíly mezi vlákna na popředí a na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2b864-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="2b864-119">Dělení na spravovaná a nespravovaná vlákna ve Windows</span><span class="sxs-lookup"><span data-stu-id="2b864-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="2b864-120">Popisuje vztah mezi spravovaná a nespravovaná vlákna, jsou uvedené spravované ekvivalenty pro dělení na vlákna rozhraní API systému Windows a popisuje interakci Apartment COM a spravovaných vláknech.</span><span class="sxs-lookup"><span data-stu-id="2b864-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="2b864-121">Thread.Suspend, uvolňování paměti a bezpečné body</span><span class="sxs-lookup"><span data-stu-id="2b864-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="2b864-122">Popisuje kolekci pozastavení a uvolňování paměti přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b864-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="2b864-123">Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům</span><span class="sxs-lookup"><span data-stu-id="2b864-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="2b864-124">Popisuje mechanismy relativní vůči vláknu úložiště.</span><span class="sxs-lookup"><span data-stu-id="2b864-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="2b864-125">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="2b864-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="2b864-126">Popisuje, jak asynchronní nebo dlouhotrvající synchronní operace se může týkat pomocí tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="2b864-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2b864-127">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2b864-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="2b864-128">Poskytuje referenční dokumentaci pro **vlákno** třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b864-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="2b864-129">Poskytuje bezpečný způsob, jak implementovat více vláken ve spojení s objekty uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b864-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2b864-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2b864-130">Related Sections</span></span>  
 [<span data-ttu-id="2b864-131">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="2b864-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="2b864-132">Popisuje spravované třídy, které jsou použity k synchronizaci aktivity z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2b864-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="2b864-133">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2b864-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="2b864-134">Popisuje časté problémy s více vláken a strategie pro vyhnout se tak problémům.</span><span class="sxs-lookup"><span data-stu-id="2b864-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="2b864-135">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="2b864-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="2b864-136">Popisuje Task Parallel Library a PLINQ, které výrazně usnadňuje práci při vytváření asynchronní a vícevláknových aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b864-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
