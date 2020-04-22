---
title: Asynchronní programování
description: Zjistěte, jak F# poskytuje čistou podporu pro asynchronii založenou na programovacím modelu na úrovni jazyka odvozeném z konceptů základního funkčního programování.
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021517"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="1f489-103">Asynchronní programování v F\#</span><span class="sxs-lookup"><span data-stu-id="1f489-103">Async programming in F\#</span></span>

<span data-ttu-id="1f489-104">Asynchronní programování je mechanismus, který je nezbytný pro moderní aplikace z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="1f489-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="1f489-105">Existují dva případy primárního použití, se kterými se většina vývojářů setká:</span><span class="sxs-lookup"><span data-stu-id="1f489-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="1f489-106">Prezentace procesu serveru, který může obsluhovat významný počet souběžných příchozích požadavků, při minimalizaci systémových prostředků obsazených při zpracování požadavků čeká na vstupy ze systémů nebo služeb mimo tento proces.</span><span class="sxs-lookup"><span data-stu-id="1f489-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="1f489-107">Udržování responzivního uživatelského rozhraní nebo hlavního vlákna při souběžném průběhu práce na pozadí</span><span class="sxs-lookup"><span data-stu-id="1f489-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="1f489-108">Přestože práce na pozadí často zahrnuje využití více vláken, je důležité zvážit koncepty asynchronia a více vláken samostatně.</span><span class="sxs-lookup"><span data-stu-id="1f489-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="1f489-109">Ve skutečnosti se jedná o samostatné obavy a jeden neznamená druhý.</span><span class="sxs-lookup"><span data-stu-id="1f489-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="1f489-110">Tento článek popisuje samostatné koncepty podrobněji.</span><span class="sxs-lookup"><span data-stu-id="1f489-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="1f489-111">Asynchronní definice</span><span class="sxs-lookup"><span data-stu-id="1f489-111">Asynchrony defined</span></span>

<span data-ttu-id="1f489-112">Předchozí bod - že asynchronie je nezávislá na využití více vláken - stojí za to vysvětlit trochu dále.</span><span class="sxs-lookup"><span data-stu-id="1f489-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="1f489-113">Existují tři pojmy, které jsou někdy související, ale přísně nezávislé na sobě:</span><span class="sxs-lookup"><span data-stu-id="1f489-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="1f489-114">Souběžnost; při provádění více výpočtů v překrývajících se časových obdobích.</span><span class="sxs-lookup"><span data-stu-id="1f489-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="1f489-115">Paralelismus; při spuštění více výpočtů nebo několika částí jednoho výpočtu přesně ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1f489-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="1f489-116">Asynchronní; pokud jeden nebo více výpočtů lze spustit odděleně od toku hlavního programu.</span><span class="sxs-lookup"><span data-stu-id="1f489-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="1f489-117">Všechny tři jsou ortogognální pojmy, ale mohou být snadno splynutí, zvláště když jsou používány společně.</span><span class="sxs-lookup"><span data-stu-id="1f489-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="1f489-118">Například může být nutné provést více asynchronních výpočtů paralelně.</span><span class="sxs-lookup"><span data-stu-id="1f489-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="1f489-119">Tento vztah neznamená, že paralelismus nebo asynchronie implikují navzájem.</span><span class="sxs-lookup"><span data-stu-id="1f489-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="1f489-120">Pokud vezmete v úvahu etymologii slova "asynchronní", existují dva kusy:</span><span class="sxs-lookup"><span data-stu-id="1f489-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="1f489-121">"a", což znamená "ne".</span><span class="sxs-lookup"><span data-stu-id="1f489-121">"a", meaning "not".</span></span>
- <span data-ttu-id="1f489-122">"synchronní", což znamená "současně".</span><span class="sxs-lookup"><span data-stu-id="1f489-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="1f489-123">Když dáte tyto dva termíny dohromady, uvidíte, že "asynchronní" znamená "není ve stejnou dobu".</span><span class="sxs-lookup"><span data-stu-id="1f489-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="1f489-124">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="1f489-124">That's it!</span></span> <span data-ttu-id="1f489-125">Neexistuje žádný důsledek souběžnosti nebo paralelismu v této definici.</span><span class="sxs-lookup"><span data-stu-id="1f489-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="1f489-126">To platí i v praxi.</span><span class="sxs-lookup"><span data-stu-id="1f489-126">This is also true in practice.</span></span>

<span data-ttu-id="1f489-127">V praxi jsou naplánovány asynchronní výpočty v F# nezávisle na toku hlavního programu.</span><span class="sxs-lookup"><span data-stu-id="1f489-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="1f489-128">Toto nezávislé spuštění neznamená souběžnost nebo paralelismus, ani neznamená, že výpočtu vždy dochází na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1f489-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="1f489-129">Ve skutečnosti asynchronní výpočty lze dokonce spustit synchronně, v závislosti na povaze výpočtu a prostředí, ve kterých je prováděna výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="1f489-130">Hlavní stánek s jídlem, který byste měli mít, je, že asynchronní výpočty jsou nezávislé na toku hlavního programu.</span><span class="sxs-lookup"><span data-stu-id="1f489-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="1f489-131">Přestože existuje jen málo záruky o tom, kdy a jak se provádí asynchronní výpočty, existují některé přístupy k jejich orchestraci a plánování.</span><span class="sxs-lookup"><span data-stu-id="1f489-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="1f489-132">Zbytek tohoto článku zkoumá základní koncepty pro f# asynchrony a jak používat typy, funkce a výrazy integrované do F#.</span><span class="sxs-lookup"><span data-stu-id="1f489-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="1f489-133">Základní koncepty</span><span class="sxs-lookup"><span data-stu-id="1f489-133">Core concepts</span></span>

<span data-ttu-id="1f489-134">V jazyce F# je asynchronní programování soustředěno na tři základní koncepty:</span><span class="sxs-lookup"><span data-stu-id="1f489-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="1f489-135">Typ, `Async<'T>` který představuje kompozitovatelné asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="1f489-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="1f489-136">Funkce `Async` modulu, které umožňují plánovat asynchronní práci, skládat asynchronní výpočty a transformovat asynchronní výsledky.</span><span class="sxs-lookup"><span data-stu-id="1f489-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="1f489-137">`async { }` [Výpočetní výraz](../../language-reference/computation-expressions.md), který poskytuje pohodlnou syntaxi pro vytváření a řízení asynchronních výpočtů.</span><span class="sxs-lookup"><span data-stu-id="1f489-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="1f489-138">Tyto tři koncepty můžete vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1f489-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="1f489-139">V příkladu `printTotalFileBytes` je funkce `string -> Async<unit>`typu .</span><span class="sxs-lookup"><span data-stu-id="1f489-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="1f489-140">Volání funkce ve skutečnosti neprovede asynchronní výpočt.</span><span class="sxs-lookup"><span data-stu-id="1f489-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="1f489-141">Místo toho `Async<unit>` vrátí, který funguje jako *specifikace* práce, která je provádět asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1f489-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="1f489-142">Volá `Async.AwaitTask` ve svém těle, který převádí výsledek <xref:System.IO.File.ReadAllBytesAsync%2A> na vhodný typ.</span><span class="sxs-lookup"><span data-stu-id="1f489-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="1f489-143">Další důležitou linkou `Async.RunSynchronously`je volání na .</span><span class="sxs-lookup"><span data-stu-id="1f489-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="1f489-144">Toto je jedna z funkcí spuštění modulu Async, které budete muset volat, pokud chcete skutečně spustit asynchronní výpočty F#.</span><span class="sxs-lookup"><span data-stu-id="1f489-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="1f489-145">To je zásadní rozdíl s C#/Visual `async` Basic styl programování.</span><span class="sxs-lookup"><span data-stu-id="1f489-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="1f489-146">V F#, asynchronní výpočty lze považovat za **studené úkoly**.</span><span class="sxs-lookup"><span data-stu-id="1f489-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="1f489-147">Musí být explicitně zahájeny skutečně spustit.</span><span class="sxs-lookup"><span data-stu-id="1f489-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="1f489-148">To má některé výhody, protože umožňuje kombinovat a sekvenční asynchronní práci mnohem snadněji než v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f489-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="1f489-149">Kombinování asynchronních výpočtů</span><span class="sxs-lookup"><span data-stu-id="1f489-149">Combine asynchronous computations</span></span>

<span data-ttu-id="1f489-150">Zde je příklad, který navazuje na předchozí kombinací výpočtů:</span><span class="sxs-lookup"><span data-stu-id="1f489-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="1f489-151">Jak můžete vidět, `main` funkce má poměrně málo dalších hovorů.</span><span class="sxs-lookup"><span data-stu-id="1f489-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="1f489-152">Koncepčně provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="1f489-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="1f489-153">Transformujte argumenty příkazového `Async<unit>` řádku na `Array.map`výpočty pomocí .</span><span class="sxs-lookup"><span data-stu-id="1f489-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="1f489-154">Vytvořte, `Async<'T[]>` který naplánuje `printTotalFileBytes` a spouští výpočty paralelně při spuštění.</span><span class="sxs-lookup"><span data-stu-id="1f489-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="1f489-155">Vytvořte, `Async<unit>` který spustí paralelní výpočtu a ignorovat jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="1f489-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="1f489-156">Explicitně spustit poslední výpočtu s `Async.RunSynchronously` a blokovat, dokud nebude dokončena.</span><span class="sxs-lookup"><span data-stu-id="1f489-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="1f489-157">Při spuštění tohoto `printTotalFileBytes` programu běží paralelně pro každý argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1f489-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="1f489-158">Vzhledem k tomu, že asynchronní výpočty spustit nezávisle na toku programu, neexistuje žádné pořadí, ve kterém vytisknout své informace a dokončit provádění.</span><span class="sxs-lookup"><span data-stu-id="1f489-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="1f489-159">Výpočty budou naplánovány paralelně, ale jejich pořadí provádění není zaručeno.</span><span class="sxs-lookup"><span data-stu-id="1f489-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="1f489-160">Sekvenční asynchronní výpočty</span><span class="sxs-lookup"><span data-stu-id="1f489-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="1f489-161">Vzhledem k tomu, `Async<'T>` že je specifikace práce, nikoli již spuštěná úloha, můžete snadno provádět složitější transformace.</span><span class="sxs-lookup"><span data-stu-id="1f489-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="1f489-162">Zde je příklad, který sekvencí sadu asynchronních výpočtů tak, aby spustit jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="1f489-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="1f489-163">To bude `printTotalFileBytes` naplánovat spuštění v pořadí `argv` prvků spíše než jejich plánování paralelně.</span><span class="sxs-lookup"><span data-stu-id="1f489-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="1f489-164">Vzhledem k tomu, že další položka nebude naplánována až po dokončení provádění posledního výpočtu, jsou výpočty seřazeny tak, aby nedošlo k překrytí jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="1f489-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="1f489-165">Důležité funkce modulu Async</span><span class="sxs-lookup"><span data-stu-id="1f489-165">Important Async module functions</span></span>

<span data-ttu-id="1f489-166">Při psaní asynchronního kódu v F#, obvykle budete pracovat s rámcem, který zpracovává plánování výpočtů za vás.</span><span class="sxs-lookup"><span data-stu-id="1f489-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="1f489-167">To však není vždy případ, takže je dobré se naučit různé počáteční funkce naplánovat asynchronní práci.</span><span class="sxs-lookup"><span data-stu-id="1f489-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="1f489-168">Vzhledem k tomu, že f# asynchronní výpočty jsou _specifikace_ práce spíše než reprezentace práce, která je již provádí, musí být explicitně spuštěna s počáteční funkce.</span><span class="sxs-lookup"><span data-stu-id="1f489-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="1f489-169">Existuje mnoho [funkcí spuštění asynchronního](https://msdn.microsoft.com/library/ee370232.aspx) spuštění, které jsou užitečné v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="1f489-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="1f489-170">Následující část popisuje některé běžné funkce spuštění.</span><span class="sxs-lookup"><span data-stu-id="1f489-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="1f489-171">Async.StartChild</span><span class="sxs-lookup"><span data-stu-id="1f489-171">Async.StartChild</span></span>

<span data-ttu-id="1f489-172">Spustí podřízený výpočetní v rámci asynchronní ho výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="1f489-173">To umožňuje souběžné provádění více asynchronních výpočtů.</span><span class="sxs-lookup"><span data-stu-id="1f489-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="1f489-174">Podřízený výpočet sdílí token zrušení s nadřazeným výpočtem.</span><span class="sxs-lookup"><span data-stu-id="1f489-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="1f489-175">Pokud je nadřazený výpočetní byl zrušen, podřízený výpočt je také zrušena.</span><span class="sxs-lookup"><span data-stu-id="1f489-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="1f489-176">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="1f489-177">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-177">When to use:</span></span>

- <span data-ttu-id="1f489-178">Pokud chcete spustit více asynchronních výpočtů současně, nikoli jeden po druhém, ale nemít je naplánováno paralelně.</span><span class="sxs-lookup"><span data-stu-id="1f489-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="1f489-179">Pokud chcete spojit životnost podřízeného výpočtu s nadřazeným výpočtem.</span><span class="sxs-lookup"><span data-stu-id="1f489-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="1f489-180">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-180">What to watch out for:</span></span>

- <span data-ttu-id="1f489-181">Spuštění více výpočtů `Async.StartChild` s není totéž jako jejich paralelní plánování.</span><span class="sxs-lookup"><span data-stu-id="1f489-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="1f489-182">Chcete-li naplánovat výpočty paralelně, `Async.Parallel`použijte .</span><span class="sxs-lookup"><span data-stu-id="1f489-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="1f489-183">Zrušení nadřazeného výpočtu spustí zrušení všech podřízených výpočtů, které bylo spuštěno.</span><span class="sxs-lookup"><span data-stu-id="1f489-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="1f489-184">Async.StartOkamžité</span><span class="sxs-lookup"><span data-stu-id="1f489-184">Async.StartImmediate</span></span>

<span data-ttu-id="1f489-185">Spustí asynchronní výpočt, který začíná okamžitě v aktuálním vlákně operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1f489-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="1f489-186">To je užitečné, pokud potřebujete aktualizovat něco na volající vlákno během výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="1f489-187">Například pokud asynchronní výpočtu musí aktualizovat uI (například aktualizace indikátoru průběhu), pak `Async.StartImmediate` by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="1f489-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="1f489-188">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="1f489-189">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-189">When to use:</span></span>

- <span data-ttu-id="1f489-190">Když potřebujete aktualizovat něco na volající vlákno uprostřed asynchronní ho výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="1f489-191">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-191">What to watch out for:</span></span>

- <span data-ttu-id="1f489-192">Kód v asynchronním výpočtu bude spuštěn na libovolné vlákno, které se stane, že je naplánováno.</span><span class="sxs-lookup"><span data-stu-id="1f489-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="1f489-193">To může být problematické, pokud je toto vlákno nějakým způsobem citlivé, například vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f489-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="1f489-194">V takových `Async.StartImmediate` případech, je pravděpodobné, že nevhodné k použití.</span><span class="sxs-lookup"><span data-stu-id="1f489-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="1f489-195">Async.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="1f489-195">Async.StartAsTask</span></span>

<span data-ttu-id="1f489-196">Provede výpočtu ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="1f489-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="1f489-197">Vrátí, <xref:System.Threading.Tasks.Task%601> který bude dokončen v odpovídajícím stavu po ukončení výpočtu (vytvoří výsledek, vyvolá výjimku nebo získá zrušena).</span><span class="sxs-lookup"><span data-stu-id="1f489-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="1f489-198">Pokud není k dispozici žádný token zrušení, použije se výchozí token zrušení.</span><span class="sxs-lookup"><span data-stu-id="1f489-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="1f489-199">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="1f489-200">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-200">When to use:</span></span>

- <span data-ttu-id="1f489-201">Když potřebujete volat do rozhraní .NET API, které očekává, <xref:System.Threading.Tasks.Task%601> že bude představovat výsledek asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="1f489-202">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-202">What to watch out for:</span></span>

- <span data-ttu-id="1f489-203">Toto volání přidělí další `Task` objekt, který může zvýšit režii, pokud se používá často.</span><span class="sxs-lookup"><span data-stu-id="1f489-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="1f489-204">Async.Paralelní</span><span class="sxs-lookup"><span data-stu-id="1f489-204">Async.Parallel</span></span>

<span data-ttu-id="1f489-205">Naplánuje posloupnost asynchronních výpočtů, které mají být provedeny paralelně.</span><span class="sxs-lookup"><span data-stu-id="1f489-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="1f489-206">Stupeň paralelismu lze volitelně vyladit/omezit zadáním parametru. `maxDegreesOfParallelism`</span><span class="sxs-lookup"><span data-stu-id="1f489-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="1f489-207">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="1f489-208">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-208">When to use it:</span></span>

- <span data-ttu-id="1f489-209">Pokud potřebujete spustit sadu výpočtů současně a nespoléhali se na jejich pořadí provádění.</span><span class="sxs-lookup"><span data-stu-id="1f489-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="1f489-210">Pokud nepožadujete výsledky z výpočtů naplánovaných paralelně, dokud nebudou všechny dokončeny.</span><span class="sxs-lookup"><span data-stu-id="1f489-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="1f489-211">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-211">What to watch out for:</span></span>

- <span data-ttu-id="1f489-212">K výslednému poli hodnot lze získat přístup pouze po dokončení všech výpočtů.</span><span class="sxs-lookup"><span data-stu-id="1f489-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="1f489-213">Výpočty budou spuštěny vždy, když skončí naplánované.</span><span class="sxs-lookup"><span data-stu-id="1f489-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="1f489-214">Toto chování znamená, že se nemůžete spoléhat na jejich pořadí jejich provedení.</span><span class="sxs-lookup"><span data-stu-id="1f489-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="1f489-215">Async.Sekvenční</span><span class="sxs-lookup"><span data-stu-id="1f489-215">Async.Sequential</span></span>

<span data-ttu-id="1f489-216">Naplánuje posloupnost asynchronních výpočtů, které mají být provedeny v pořadí, v jakém jsou předány.</span><span class="sxs-lookup"><span data-stu-id="1f489-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="1f489-217">První výpočtbude proveden, pak další a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1f489-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="1f489-218">Souběžně nebudou prováděny žádné výpočty.</span><span class="sxs-lookup"><span data-stu-id="1f489-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="1f489-219">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="1f489-220">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-220">When to use it:</span></span>

- <span data-ttu-id="1f489-221">Pokud potřebujete provést více výpočtů v pořadí.</span><span class="sxs-lookup"><span data-stu-id="1f489-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="1f489-222">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-222">What to watch out for:</span></span>

- <span data-ttu-id="1f489-223">K výslednému poli hodnot lze získat přístup pouze po dokončení všech výpočtů.</span><span class="sxs-lookup"><span data-stu-id="1f489-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="1f489-224">Výpočty budou spuštěny v pořadí, v jakém jsou předány této funkci, což může znamenat, že před vrácením výsledků uplyne více času.</span><span class="sxs-lookup"><span data-stu-id="1f489-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="1f489-225">Async.AwaitTask</span><span class="sxs-lookup"><span data-stu-id="1f489-225">Async.AwaitTask</span></span>

<span data-ttu-id="1f489-226">Vrátí asynchronní výpočt, který čeká na <xref:System.Threading.Tasks.Task%601> dokončení daného a vrátí jeho výsledek jako`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="1f489-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="1f489-227">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="1f489-228">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-228">When to use:</span></span>

- <span data-ttu-id="1f489-229">Při náročné rozhraní .NET API, <xref:System.Threading.Tasks.Task%601> které vrací v rámci F# asynchronní výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f489-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="1f489-230">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-230">What to watch out for:</span></span>

- <span data-ttu-id="1f489-231">Výjimky jsou zabaleny v <xref:System.AggregateException> následující konvence task paralelní knihovny a toto chování se liší od jak F# async obecně povrchy výjimky.</span><span class="sxs-lookup"><span data-stu-id="1f489-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="1f489-232">Async.Catch</span><span class="sxs-lookup"><span data-stu-id="1f489-232">Async.Catch</span></span>

<span data-ttu-id="1f489-233">Vytvoří asynchronní výpočt, který provede daný `Async<'T>`, vrácení `Async<Choice<'T, exn>>`.</span><span class="sxs-lookup"><span data-stu-id="1f489-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="1f489-234">Pokud daný `Async<'T>` dokončí úspěšně, pak `Choice1Of2` a je vrácena s výslednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="1f489-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="1f489-235">Pokud je vyvolána výjimka před dokončením, pak je vrácena `Choice2of2` s vyzdviženou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="1f489-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="1f489-236">Pokud se používá na asynchronní výpočtu, který se skládá z mnoha výpočtů a jeden z těchto výpočtů vyvolá výjimku, zahrnující výpočetní bude zcela zastavena.</span><span class="sxs-lookup"><span data-stu-id="1f489-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="1f489-237">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="1f489-238">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-238">When to use:</span></span>

- <span data-ttu-id="1f489-239">Při provádění asynchronní práce, která může selhat s výjimkou a chcete zpracovat tuto výjimku v volajícím.</span><span class="sxs-lookup"><span data-stu-id="1f489-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="1f489-240">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-240">What to watch out for:</span></span>

- <span data-ttu-id="1f489-241">Při použití kombinované nebo sekvencované asynchronní výpočty, zahrnující výpočtu se plně zastaví, pokud jeden z jeho "vnitřní" výpočty vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="1f489-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="1f489-242">Asynchronní.Ignorovat</span><span class="sxs-lookup"><span data-stu-id="1f489-242">Async.Ignore</span></span>

<span data-ttu-id="1f489-243">Vytvoří asynchronní výpočt, který spustí daný výpočetní a ignoruje jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="1f489-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="1f489-244">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="1f489-245">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-245">When to use:</span></span>

- <span data-ttu-id="1f489-246">Pokud máte asynchronní výpočty, jejichž výsledek není potřeba.</span><span class="sxs-lookup"><span data-stu-id="1f489-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="1f489-247">To je obdobou `ignore` kódu pro neasynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="1f489-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="1f489-248">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-248">What to watch out for:</span></span>

- <span data-ttu-id="1f489-249">Pokud je `Async.Ignore` nutné použít, `Async.Start` protože chcete použít `Async<unit>`nebo jinou funkci, která vyžaduje , zvažte, zda je zahození výsledku v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1f489-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="1f489-250">Vyhněte se zahození výsledků jen tak, aby se vešly podpis typu.</span><span class="sxs-lookup"><span data-stu-id="1f489-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="1f489-251">Async.RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="1f489-251">Async.RunSynchronously</span></span>

<span data-ttu-id="1f489-252">Spustí asynchronní výpočtu a čeká na jeho výsledek na volající vlákno.</span><span class="sxs-lookup"><span data-stu-id="1f489-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="1f489-253">Tento hovor blokuje.</span><span class="sxs-lookup"><span data-stu-id="1f489-253">This call is blocking.</span></span>

<span data-ttu-id="1f489-254">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="1f489-255">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="1f489-255">When to use it:</span></span>

- <span data-ttu-id="1f489-256">Pokud ji potřebujete, použijte ji pouze jednou v aplikaci - na vstupním místě pro spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1f489-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="1f489-257">Když se nestaráte o výkon a chcete provést sadu dalších asynchronních operací najednou.</span><span class="sxs-lookup"><span data-stu-id="1f489-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="1f489-258">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-258">What to watch out for:</span></span>

- <span data-ttu-id="1f489-259">Volání `Async.RunSynchronously` blokuje volající vlákno, dokud nebude dokončeno spuštění.</span><span class="sxs-lookup"><span data-stu-id="1f489-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="1f489-260">Async.Start</span><span class="sxs-lookup"><span data-stu-id="1f489-260">Async.Start</span></span>

<span data-ttu-id="1f489-261">Spustí asynchronní výpočtve fondu vláken, který `unit`vrátí .</span><span class="sxs-lookup"><span data-stu-id="1f489-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="1f489-262">Nečeká na jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="1f489-262">Doesn't wait for its result.</span></span> <span data-ttu-id="1f489-263">Vnořené výpočty `Async.Start` zahájené s jsou spuštěny nezávisle na nadřazeném výpočtu, který je nazval.</span><span class="sxs-lookup"><span data-stu-id="1f489-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="1f489-264">Jejich životnost není vázána na žádné nadřazené výpočty.</span><span class="sxs-lookup"><span data-stu-id="1f489-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="1f489-265">Pokud je nadřazený výpočetní byl zrušen, žádné podřízené výpočty jsou zrušeny.</span><span class="sxs-lookup"><span data-stu-id="1f489-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="1f489-266">Podpis:</span><span class="sxs-lookup"><span data-stu-id="1f489-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="1f489-267">Používejte pouze v případě, že:</span><span class="sxs-lookup"><span data-stu-id="1f489-267">Use only when:</span></span>

- <span data-ttu-id="1f489-268">Máte asynchronní výpočt, který neposkytuje výsledek nebo vyžaduje zpracování jednoho.</span><span class="sxs-lookup"><span data-stu-id="1f489-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="1f489-269">Nemusíte vědět, kdy je dokončen asynchronní výpočt.</span><span class="sxs-lookup"><span data-stu-id="1f489-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="1f489-270">Je vám jedno, které vlákno asynchronní výpočty běží na.</span><span class="sxs-lookup"><span data-stu-id="1f489-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="1f489-271">Nemusíte znát nebo hlásit výjimky vyplývající z úkolu.</span><span class="sxs-lookup"><span data-stu-id="1f489-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="1f489-272">Na co si dát pozor:</span><span class="sxs-lookup"><span data-stu-id="1f489-272">What to watch out for:</span></span>

- <span data-ttu-id="1f489-273">Výjimky vyvolané výpočty, které `Async.Start` byly spuštěny, se volajícímu nešíří.</span><span class="sxs-lookup"><span data-stu-id="1f489-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="1f489-274">Zásobník volání bude zcela odvinut.</span><span class="sxs-lookup"><span data-stu-id="1f489-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="1f489-275">Jakákoli práce (například volání) `printfn`spuštěná s `Async.Start` nezpůsobí, že k efektu dojde v hlavním vlákně spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="1f489-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="1f489-276">Spolupracujte s rozhraním .NET</span><span class="sxs-lookup"><span data-stu-id="1f489-276">Interoperate with .NET</span></span>

<span data-ttu-id="1f489-277">Pravděpodobně pracujete s knihovnou .NET nebo základnou kódu Jazyka C#, který používá asynchronní programování [asynchronního stylu async/await-style.](../../../standard/async.md)</span><span class="sxs-lookup"><span data-stu-id="1f489-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="1f489-278">Vzhledem k tomu, že C# a <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> většina knihoven .NET používají `Async<'T>`a typy jako jejich základní abstrakce spíše než , je nutné překročit hranici mezi těmito dvěma přístupy k asynchronii.</span><span class="sxs-lookup"><span data-stu-id="1f489-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="1f489-279">Jak pracovat s asynchronní rozhraní .NET a`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="1f489-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="1f489-280">Práce s asynchronními knihovnami .NET a základy kódu, které používají <xref:System.Threading.Tasks.Task%601> (tj. asynchronní výpočty, které mají vrácené hodnoty), je přímočará a má integrovanou podporu s F#.</span><span class="sxs-lookup"><span data-stu-id="1f489-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="1f489-281">`Async.AwaitTask` Funkci můžete použít k čekání na asynchronní výpočty .NET:</span><span class="sxs-lookup"><span data-stu-id="1f489-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="1f489-282">`Async.StartAsTask` Pomocí této funkce můžete předat asynchronní výpočt volajícímu .NET:</span><span class="sxs-lookup"><span data-stu-id="1f489-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="1f489-283">Jak pracovat s asynchronní rozhraní .NET a`Task`</span><span class="sxs-lookup"><span data-stu-id="1f489-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="1f489-284">Chcete-li pracovat s <xref:System.Threading.Tasks.Task> rozhraními API, která používají `Async<'T>` <xref:System.Threading.Tasks.Task>(tj. asynchronní výpočty rozhraní .NET, které nevracejí hodnotu), bude pravděpodobně nutné přidat další funkci, která převede na :</span><span class="sxs-lookup"><span data-stu-id="1f489-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="1f489-285">Již existuje, `Async.AwaitTask` který přijímá <xref:System.Threading.Tasks.Task> jako vstup.</span><span class="sxs-lookup"><span data-stu-id="1f489-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="1f489-286">Pomocí tohoto a `startTaskFromAsyncUnit` dříve definované funkce můžete <xref:System.Threading.Tasks.Task> spustit a čekat typy z výpočtu asynchronní F#.</span><span class="sxs-lookup"><span data-stu-id="1f489-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="1f489-287">Vztah k vícevláknovým</span><span class="sxs-lookup"><span data-stu-id="1f489-287">Relationship to multi-threading</span></span>

<span data-ttu-id="1f489-288">Ačkoli závitování je uvedeno v tomto článku, existují dvě důležité věci, které je třeba mít na paměti:</span><span class="sxs-lookup"><span data-stu-id="1f489-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="1f489-289">Neexistuje žádná spřažení mezi asynchronní výpočtu a podprocesu, pokud explicitně spuštěna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1f489-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="1f489-290">Asynchronní programování v Jazyce F# není abstrakce pro více vláken.</span><span class="sxs-lookup"><span data-stu-id="1f489-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="1f489-291">Například výpočtu může skutečně spustit na jeho volajícího vlákno, v závislosti na povaze práce.</span><span class="sxs-lookup"><span data-stu-id="1f489-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="1f489-292">Výpočtmůže také "přeskočit" mezi vlákny, výpůjčky je na malé množství času dělat užitečnou práci mezi obdobími "čekání" (například když je volání sítě v tranzitu).</span><span class="sxs-lookup"><span data-stu-id="1f489-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="1f489-293">Přestože F# poskytuje některé schopnosti spustit asynchronní výpočtu v aktuálním vlákně (nebo explicitně není v aktuálním vlákně), asynchrony obecně není spojena s konkrétní strategie podprocesu.</span><span class="sxs-lookup"><span data-stu-id="1f489-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f489-294">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f489-294">See also</span></span>

- [<span data-ttu-id="1f489-295">Asynchronní programovací model Jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1f489-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="1f489-296">Jet.com 's F# Asynchronní průvodce</span><span class="sxs-lookup"><span data-stu-id="1f489-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="1f489-297">F# pro zábavu a zisk je asynchronní programování průvodce</span><span class="sxs-lookup"><span data-stu-id="1f489-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="1f489-298">Async v C# a F#: Asynchronní gotchas v C #</span><span class="sxs-lookup"><span data-stu-id="1f489-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
