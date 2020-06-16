---
title: Základy dělení na spravovaná vlákna
description: Viz odkazy na další články spravovaného vlákna, které pokrývají témata, například výjimky, synchronizaci dat, popředí & vlákny na pozadí, místní úložiště a další.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769090"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="dd5db-103">Základy spravovaného zřetězení</span><span class="sxs-lookup"><span data-stu-id="dd5db-103">Managed threading basics</span></span>

<span data-ttu-id="dd5db-104">Prvních pět témat této části vám pomůže určit, kdy použít spravované zřetězení a vysvětlit některé základní funkce.</span><span class="sxs-lookup"><span data-stu-id="dd5db-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="dd5db-105">Informace o třídách, které poskytují další funkce, naleznete v tématu [vlákna objektů a funkcí](threading-objects-and-features.md) a [Přehled základních synchronizací](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="dd5db-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="dd5db-106">Zbývající témata v této části se týkají pokročilých témat, včetně interakce spravovaného vlákna s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="dd5db-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd5db-107">V .NET Framework 4 poskytuje Task Parallel Library a PLINQ rozhraní API pro paralelismus Task a data v programech s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="dd5db-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="dd5db-108">Další informace najdete v tématu [paralelní programování](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd5db-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd5db-109">V této části</span><span class="sxs-lookup"><span data-stu-id="dd5db-109">In this section</span></span>

 [<span data-ttu-id="dd5db-110">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="dd5db-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="dd5db-111">Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých je možné vytvářet vlákna nebo používat vlákna fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="dd5db-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="dd5db-112">Výjimky ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="dd5db-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="dd5db-113">Popisuje chování neošetřených výjimek v vláknech pro různé verze .NET Framework, zejména v situacích, kdy mají za následek ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd5db-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="dd5db-114">Synchronizace dat pro vícevláknové zpracování</span><span class="sxs-lookup"><span data-stu-id="dd5db-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="dd5db-115">Popisuje strategie pro synchronizaci dat ve třídách, které budou použity s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="dd5db-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="dd5db-116">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="dd5db-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="dd5db-117">Vysvětluje rozdíly mezi vlákny v popředí a na pozadí.</span><span class="sxs-lookup"><span data-stu-id="dd5db-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="dd5db-118">Dělení na spravovaná a nespravovaná vlákna ve Windows</span><span class="sxs-lookup"><span data-stu-id="dd5db-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="dd5db-119">Popisuje vztah mezi spravovaným a nespravovaným vláknem, uvádí spravované ekvivalenty pro rozhraní API pro dělení na vlákna systému Windows a popisuje interakci objektů COM a spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="dd5db-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="dd5db-120">Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům</span><span class="sxs-lookup"><span data-stu-id="dd5db-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="dd5db-121">Popisuje mechanismy úložiště související s vlákny.</span><span class="sxs-lookup"><span data-stu-id="dd5db-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dd5db-122">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="dd5db-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="dd5db-123">Poskytuje referenční dokumentaci pro třídu **vlákna** , která představuje spravované vlákno, bez ohledu na to, zda pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dd5db-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="dd5db-124">Poskytuje bezpečný způsob implementace multithreading ve spojení s objekty uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dd5db-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd5db-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="dd5db-125">Related sections</span></span>

 [<span data-ttu-id="dd5db-126">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="dd5db-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="dd5db-127">Popisuje spravované třídy, které slouží k synchronizaci aktivit více vláken.</span><span class="sxs-lookup"><span data-stu-id="dd5db-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="dd5db-128">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="dd5db-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="dd5db-129">Popisuje běžné problémy s více vlákny a strategiemi pro předcházení problémů.</span><span class="sxs-lookup"><span data-stu-id="dd5db-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="dd5db-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="dd5db-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="dd5db-131">Popisuje úlohu Parallel Library and PLINQ, která významně zjednodušuje práci při vytváření asynchronních a vícevláknových .NET Framework aplikací.</span><span class="sxs-lookup"><span data-stu-id="dd5db-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
