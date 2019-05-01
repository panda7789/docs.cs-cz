---
title: Dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6447cd37e4718093acfb3a0e2db053c13a027d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015137"
---
# <a name="managed-threading"></a><span data-ttu-id="c5148-102">Dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="c5148-102">Managed Threading</span></span>
<span data-ttu-id="c5148-103">Ať už vyvíjíte pro počítače s jedním procesorem nebo několik, má aplikace poskytují největší responzivní interakci s uživatelem, i v případě, že aplikace je aktuálně provádění jiné práce.</span><span class="sxs-lookup"><span data-stu-id="c5148-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="c5148-104">Použití více vláken, která je jedním z nejúčinnějších způsobů, jak udržovat vaše aplikace reagovat na uživatele a ujistěte se, v době, využívání procesoru mezi nebo i během událostí uživatele.</span><span class="sxs-lookup"><span data-stu-id="c5148-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="c5148-105">Zatímco tato část představuje základní koncepce práce s vlákny, zaměřuje se na spravované koncepce práce s vlákny a použití dělení na spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="c5148-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5148-106">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna.</span><span class="sxs-lookup"><span data-stu-id="c5148-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="c5148-107">Další informace najdete v tématu [paralelního programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5148-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5148-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c5148-108">In This Section</span></span>  
 [<span data-ttu-id="c5148-109">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="c5148-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="c5148-110">Obsahuje základní informace o správě vláken a popisuje použití více vláken.</span><span class="sxs-lookup"><span data-stu-id="c5148-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="c5148-111">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="c5148-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="c5148-112">Vysvětluje, jak vytvořit a spuštění, pozastavení, obnovení a přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="c5148-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="c5148-113">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="c5148-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="c5148-114">Tento článek popisuje úrovně synchronizace, jak se vyhnout zablokování a konflikty časování a dalších dělení na vlákna problémy.</span><span class="sxs-lookup"><span data-stu-id="c5148-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="c5148-115">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="c5148-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="c5148-116">Popisuje spravované třídy, které lze použít k synchronizaci aktivity vláken a datové objekty přístupné v různých vláknech a najdete zde přehled vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="c5148-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5148-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c5148-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="c5148-118">Obsahuje třídy pro použití a synchronizaci spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="c5148-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="c5148-119">Obsahuje třídy kolekcí, které jsou bezpečné pro použití s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="c5148-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="c5148-120">Obsahuje třídy pro vytváření a plánování úloh souběžné zpracování.</span><span class="sxs-lookup"><span data-stu-id="c5148-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5148-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c5148-121">Related Sections</span></span>  
 [<span data-ttu-id="c5148-122">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="c5148-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="c5148-123">Poskytuje přehled domén aplikací a jejich použití Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c5148-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="c5148-124">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="c5148-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="c5148-125">Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="c5148-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="c5148-126">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="c5148-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="c5148-127">Poskytuje přehled o doporučený model pro asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c5148-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="c5148-128">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="c5148-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="c5148-129">Vysvětluje, jak volat metody ve vlákně fondu vláken pomocí integrované funkce delegátů.</span><span class="sxs-lookup"><span data-stu-id="c5148-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="c5148-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="c5148-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="c5148-131">Popisuje paralelní programování knihoven, které zjednodušují používání více vláken v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="c5148-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="c5148-132">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c5148-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="c5148-133">Popisuje systém pro spouštění dotazů paralelně, abyste mohli využívat více procesorů.</span><span class="sxs-lookup"><span data-stu-id="c5148-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
