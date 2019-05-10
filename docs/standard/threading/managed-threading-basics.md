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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b352c35a327ed4736a1f41816d3f15c1a0f559f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644824"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="cfdbe-102">Dělení na spravovaná vlákna základy</span><span class="sxs-lookup"><span data-stu-id="cfdbe-102">Managed threading basics</span></span>

<span data-ttu-id="cfdbe-103">Prvních pět témata v této části jsou navržené tak, která vám pomůže určit, kdy použití dělení na spravovaná vlákna a vysvětlit jim některé základní funkce.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="cfdbe-104">Informace o třídách, které poskytují další funkce, najdete v části [funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md) a [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="cfdbe-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="cfdbe-105">Zbývající témata v této části pokrývají Pokročilá témata, včetně interakcí správě vláken s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfdbe-106">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Task Parallel Library a PLINQ poskytují rozhraní API pro paralelismus úloh a dat ve vícevláknových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="cfdbe-107">Další informace najdete v tématu [paralelního programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="cfdbe-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfdbe-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cfdbe-108">In this section</span></span>

 [<span data-ttu-id="cfdbe-109">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="cfdbe-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="cfdbe-110">Tento článek popisuje, jaké výhody a nevýhody více vláken a popisuje scénáře, ve kterých může vytvářet vlákna nebo pomocí vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="cfdbe-111">Výjimky ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="cfdbe-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="cfdbe-112">Popisuje chování neošetřené výjimky ve vláknech pro různé verze rozhraní .NET Framework, zejména situace, ve které se za následek ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="cfdbe-113">Synchronizace dat pro vícevláknové zpracování</span><span class="sxs-lookup"><span data-stu-id="cfdbe-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="cfdbe-114">Popisuje strategie pro synchronizaci dat ve třídách, které se použijí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="cfdbe-115">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="cfdbe-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="cfdbe-116">Vysvětluje rozdíly mezi vlákna v popředí a pozadí.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="cfdbe-117">Dělení na spravovaná a nespravovaná vlákna ve Windows</span><span class="sxs-lookup"><span data-stu-id="cfdbe-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="cfdbe-118">Tento článek popisuje vztah mezi spravovaná a nespravovaná vlákna, jsou uvedené spravované ekvivalenty pro dělení na vlákna rozhraní API Windows a popisuje interakce Apartment modelu COM a spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="cfdbe-119">Úložiště Thread Local: Statická pole relativní vůči vláknu a datové sloty ve vztahu</span><span class="sxs-lookup"><span data-stu-id="cfdbe-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="cfdbe-120">Popisuje relativní vůči vláknu úložiště mechanismy.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-120">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="cfdbe-121">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="cfdbe-121">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="cfdbe-122">Popisuje, jak asynchronní nebo dlouhotrvající synchronní operace se může týkat pomocí tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-122">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cfdbe-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="cfdbe-123">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="cfdbe-124">Poskytuje referenční dokumentaci pro **vlákno** třídu, která představuje spravované vlákno, ať už pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-124">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="cfdbe-125">Poskytuje bezpečný způsob, jak implementovat multithreadingu ve spojení s objektů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-125">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cfdbe-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cfdbe-126">Related sections</span></span>

 [<span data-ttu-id="cfdbe-127">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="cfdbe-127">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="cfdbe-128">Popisuje spravované třídy používané pro synchronizaci činností více vláken.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-128">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="cfdbe-129">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="cfdbe-129">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="cfdbe-130">Popisuje běžné problémy s multithreading a strategie, jak se vyhnout problémům.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-130">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="cfdbe-131">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="cfdbe-131">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="cfdbe-132">Popisuje Task Parallel Library a PLINQ, které značně zjednodušují vytváření asynchronní a vícevláknové aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cfdbe-132">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
