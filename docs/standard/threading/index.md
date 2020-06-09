---
title: Dělení na spravovaná vlákna
description: Přečtěte si odkazy na články o spravovaném vláknování v rozhraní .NET pokrývající základy, osvědčené postupy, objekty vláken & funkce, referenční stránky, & další.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 570db45138c85c4252967404da4404d434660d69
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599747"
---
# <a name="managed-threading"></a><span data-ttu-id="2e0c1-103">Dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2e0c1-103">Managed Threading</span></span>
<span data-ttu-id="2e0c1-104">Bez ohledu na to, zda vyvíjíte pro počítače s jedním nebo několika procesory, chcete, aby vaše aplikace poskytovala co nejrychlejší interakci s uživatelem, a to i v případě, že aplikace právě provádí jinou práci.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-104">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="2e0c1-105">Použití několika podprocesů provádění je jedním z nejúčinnějších způsobů, jak zajistit, aby aplikace reagovala na uživatele a zároveň používala procesor v rámci událostí uživatele nebo dokonce i během nich.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-105">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="2e0c1-106">V této části se seznámíte se základními koncepcemi dělení na vlákna, zaměřuje se na koncepty spravovaného vlákna a pomocí spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-106">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e0c1-107">Počínaje .NET Framework 4 je vícevláknové programování značně zjednodušené s <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídami, [Paralelní LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), nové souběžné třídy kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů a nový programovací model, který je založen na konceptu úkolů, nikoli na vláknech.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-107">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="2e0c1-108">Další informace najdete v tématu [paralelní programování](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e0c1-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e0c1-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2e0c1-109">In This Section</span></span>  
 [<span data-ttu-id="2e0c1-110">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2e0c1-110">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="2e0c1-111">Poskytuje přehled spravovaného zřetězení a popisuje, kdy použít více vláken.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-111">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="2e0c1-112">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2e0c1-112">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="2e0c1-113">Vysvětluje, jak vytvořit, spustit, pozastavit, obnovit a přerušit vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-113">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="2e0c1-114">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2e0c1-114">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="2e0c1-115">Popisuje úrovně synchronizace, jak zabránit zablokování a konfliktům časování a dalším problémům s vlákny.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-115">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="2e0c1-116">Dělení objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="2e0c1-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="2e0c1-117">Popisuje spravované třídy, které lze použít k synchronizaci aktivit vláken a dat objektů, ke kterým přistupovalo v různých vláknech, a poskytuje přehled vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-117">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2e0c1-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="2e0c1-118">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="2e0c1-119">Obsahuje třídy pro použití a synchronizaci spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-119">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="2e0c1-120">Obsahuje třídy kolekcí, které jsou bezpečné pro použití s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-120">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="2e0c1-121">Obsahuje třídy pro vytváření a plánování souběžných úloh zpracování.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-121">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2e0c1-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2e0c1-122">Related Sections</span></span>  
 [<span data-ttu-id="2e0c1-123">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="2e0c1-123">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="2e0c1-124">Poskytuje přehled aplikačních domén a jejich použití Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-124">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="2e0c1-125">I/O asynchronní soubory</span><span class="sxs-lookup"><span data-stu-id="2e0c1-125">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="2e0c1-126">Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-126">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="2e0c1-127">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="2e0c1-127">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="2e0c1-128">Poskytuje přehled o doporučeném vzoru pro asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-128">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="2e0c1-129">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="2e0c1-129">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="2e0c1-130">Vysvětluje, jak volat metody v vláknech fondu vláken pomocí integrovaných funkcí delegátů.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-130">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="2e0c1-131">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="2e0c1-131">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="2e0c1-132">Popisuje knihovny paralelního programování, které zjednodušují použití více vláken v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-132">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="2e0c1-133">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2e0c1-133">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="2e0c1-134">Popisuje systém pro souběžné spouštění dotazů, aby bylo možné využít více procesorů.</span><span class="sxs-lookup"><span data-stu-id="2e0c1-134">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
