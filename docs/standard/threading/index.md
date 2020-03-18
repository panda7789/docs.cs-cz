---
title: Dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137933"
---
# <a name="managed-threading"></a><span data-ttu-id="42642-102">Dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="42642-102">Managed Threading</span></span>
<span data-ttu-id="42642-103">Bez ohledu na to, zda vyvíjíte pro počítače s jedním nebo několika procesory, chcete, aby aplikace poskytovala nejcitlivější interakci s uživatelem, a to i v případě, že aplikace aktuálně provádí jinou práci.</span><span class="sxs-lookup"><span data-stu-id="42642-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="42642-104">Použití více vláken provádění je jedním z nejvýkonnějších způsobů, jak udržet aplikaci reagovat na uživatele a zároveň využít procesor u nebo dokonce během událostí uživatele.</span><span class="sxs-lookup"><span data-stu-id="42642-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="42642-105">Zatímco tato část představuje základní koncepty zřetězení, zaměřuje se na spravované koncepty vláken a použití spravovaného podprocesu.</span><span class="sxs-lookup"><span data-stu-id="42642-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42642-106">Počínaje rozhraním .NET Framework 4 je programování s více <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> vlákny značně zjednodušeno pomocí tříd a, Paralelní <xref:System.Collections.Concurrent?displayProperty=nameWithType> [LINQ (PLINQ),](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)nové třídy souběžné kolekce v oboru názvů a nový programovací model, který je založen na konceptu úloh spíše než zřetěze.</span><span class="sxs-lookup"><span data-stu-id="42642-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="42642-107">Další informace naleznete [v tématu Paralelní programování](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="42642-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42642-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="42642-108">In This Section</span></span>  
 [<span data-ttu-id="42642-109">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="42642-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="42642-110">Obsahuje přehled spravovaného podprocesu a popisuje, kdy použít více vláken.</span><span class="sxs-lookup"><span data-stu-id="42642-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="42642-111">Použití vláken a zřetězení</span><span class="sxs-lookup"><span data-stu-id="42642-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="42642-112">Vysvětluje, jak vytvořit, spustit, pozastavit, obnovit a přerušit podprocesy.</span><span class="sxs-lookup"><span data-stu-id="42642-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="42642-113">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="42642-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="42642-114">Popisuje úrovně synchronizace, jak se vyhnout zablokování a sporáky a další problémy podprocesem.</span><span class="sxs-lookup"><span data-stu-id="42642-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="42642-115">Objekty a prvky zřetězení</span><span class="sxs-lookup"><span data-stu-id="42642-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="42642-116">Popisuje spravované třídy, které můžete použít k synchronizaci aktivit vláken a dat objektů, ke které se přistupuje v různých vláknech, a poskytuje přehled vláken fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="42642-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42642-117">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="42642-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="42642-118">Obsahuje třídy pro použití a synchronizaci spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="42642-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="42642-119">Obsahuje třídy kolekce, které jsou bezpečné pro použití s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="42642-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="42642-120">Obsahuje třídy pro vytváření a plánování souběžných úloh zpracování.</span><span class="sxs-lookup"><span data-stu-id="42642-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42642-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="42642-121">Related Sections</span></span>  
 [<span data-ttu-id="42642-122">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="42642-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="42642-123">Obsahuje přehled aplikačních domén a jejich použití společnou jazykovou infrastrukturou.</span><span class="sxs-lookup"><span data-stu-id="42642-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="42642-124">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="42642-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="42642-125">Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="42642-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="42642-126">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="42642-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="42642-127">Obsahuje přehled doporučeného vzoru pro asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="42642-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="42642-128">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="42642-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="42642-129">Vysvětluje, jak volat metody ve vláknech fondu vláken pomocí integrovaných funkcí delegátů.</span><span class="sxs-lookup"><span data-stu-id="42642-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="42642-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="42642-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="42642-131">Popisuje paralelní programovací knihovny, které zjednodušují použití více vláken v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="42642-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="42642-132">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="42642-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="42642-133">Popisuje systém pro paralelní spouštění dotazů, aby bylo možné využívat více procesorů.</span><span class="sxs-lookup"><span data-stu-id="42642-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
