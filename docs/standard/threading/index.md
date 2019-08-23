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
ms.openlocfilehash: 763646bfb358b8e5faf13a14f2facb98f855b5c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913286"
---
# <a name="managed-threading"></a><span data-ttu-id="3df23-102">Dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="3df23-102">Managed Threading</span></span>
<span data-ttu-id="3df23-103">Bez ohledu na to, zda vyvíjíte pro počítače s jedním nebo několika procesory, chcete, aby vaše aplikace poskytovala co nejrychlejší interakci s uživatelem, a to i v případě, že aplikace právě provádí jinou práci.</span><span class="sxs-lookup"><span data-stu-id="3df23-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="3df23-104">Použití několika podprocesů provádění je jedním z nejúčinnějších způsobů, jak zajistit, aby aplikace reagovala na uživatele a zároveň používala procesor v rámci událostí uživatele nebo dokonce i během nich.</span><span class="sxs-lookup"><span data-stu-id="3df23-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="3df23-105">V této části se seznámíte se základními koncepcemi dělení na vlákna, zaměřuje se na koncepty spravovaného vlákna a pomocí spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="3df23-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3df23-106">Počínaje .NET Framework 4 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> je vícevláknové programování značně zjednodušené s třídami a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> , [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) <xref:System.Collections.Concurrent?displayProperty=nameWithType> , nové souběžné třídy kolekcí v oboru názvů a nové programování. model, který je založen na konceptu úkolů, nikoli na vláknech.</span><span class="sxs-lookup"><span data-stu-id="3df23-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="3df23-107">Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="3df23-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3df23-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3df23-108">In This Section</span></span>  
 [<span data-ttu-id="3df23-109">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="3df23-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="3df23-110">Poskytuje přehled spravovaného zřetězení a popisuje, kdy použít více vláken.</span><span class="sxs-lookup"><span data-stu-id="3df23-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="3df23-111">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3df23-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="3df23-112">Vysvětluje, jak vytvořit, spustit, pozastavit, obnovit a přerušit vlákna.</span><span class="sxs-lookup"><span data-stu-id="3df23-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="3df23-113">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="3df23-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="3df23-114">Popisuje úrovně synchronizace, jak zabránit zablokování a konfliktům časování a dalším problémům s vlákny.</span><span class="sxs-lookup"><span data-stu-id="3df23-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="3df23-115">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3df23-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="3df23-116">Popisuje spravované třídy, které lze použít k synchronizaci aktivit vláken a dat objektů, ke kterým přistupovalo v různých vláknech, a poskytuje přehled vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="3df23-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3df23-117">Reference</span><span class="sxs-lookup"><span data-stu-id="3df23-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="3df23-118">Obsahuje třídy pro použití a synchronizaci spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="3df23-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="3df23-119">Obsahuje třídy kolekcí, které jsou bezpečné pro použití s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="3df23-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="3df23-120">Obsahuje třídy pro vytváření a plánování souběžných úloh zpracování.</span><span class="sxs-lookup"><span data-stu-id="3df23-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3df23-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3df23-121">Related Sections</span></span>  
 [<span data-ttu-id="3df23-122">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="3df23-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="3df23-123">Poskytuje přehled aplikačních domén a jejich použití Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="3df23-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="3df23-124">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="3df23-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="3df23-125">Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="3df23-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="3df23-126">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="3df23-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="3df23-127">Poskytuje přehled o doporučeném vzoru pro asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3df23-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="3df23-128">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="3df23-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="3df23-129">Vysvětluje, jak volat metody v vláknech fondu vláken pomocí integrovaných funkcí delegátů.</span><span class="sxs-lookup"><span data-stu-id="3df23-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="3df23-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="3df23-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="3df23-131">Popisuje knihovny paralelního programování, které zjednodušují použití více vláken v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="3df23-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="3df23-132">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3df23-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="3df23-133">Popisuje systém pro souběžné spouštění dotazů, aby bylo možné využít více procesorů.</span><span class="sxs-lookup"><span data-stu-id="3df23-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
