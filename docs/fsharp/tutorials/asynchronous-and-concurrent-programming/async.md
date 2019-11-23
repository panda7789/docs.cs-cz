---
title: Asynchronní programování vF#
description: Naučte F# se, jak poskytuje čistou podporu pro asynchronii na základě programovacího modelu na úrovni jazyka odvozeného od konceptů základních funkcí programování.
ms.date: 12/17/2018
ms.openlocfilehash: 1ede4a5c1e26df271ac94f9b2c216ac84fb38f59
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395794"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="70940-103">Asynchronní programování v F\#</span><span class="sxs-lookup"><span data-stu-id="70940-103">Async programming in F\#</span></span>

<span data-ttu-id="70940-104">Asynchronní programování je mechanismus, který je nezbytný pro moderní aplikace z nejrůznějších důvodů.</span><span class="sxs-lookup"><span data-stu-id="70940-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="70940-105">K dispozici jsou dva primární případy použití, ke kterým dojde ve většině vývojářů:</span><span class="sxs-lookup"><span data-stu-id="70940-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="70940-106">Prezentující proces serveru, který může obsluhovat velký počet souběžných příchozích požadavků a současně minimalizuje systémové prostředky, které při zpracování požadavků čekají na vstupy ze systémů nebo služeb, které jsou pro tento proces externí.</span><span class="sxs-lookup"><span data-stu-id="70940-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="70940-107">Údržba s reagujícím uživatelským rozhraním nebo hlavním vláknem při současném průběhu práce na pozadí</span><span class="sxs-lookup"><span data-stu-id="70940-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="70940-108">I když práce na pozadí často zahrnuje využití více vláken, je důležité vzít v úvahu koncepty asynchronii a multithreading samostatně.</span><span class="sxs-lookup"><span data-stu-id="70940-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="70940-109">Ve skutečnosti se jedná o samostatné obavy a jedna z nich neznamená jinou.</span><span class="sxs-lookup"><span data-stu-id="70940-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="70940-110">Jak je uvedeno v tomto článku, popište to podrobněji.</span><span class="sxs-lookup"><span data-stu-id="70940-110">What follows in this article will describe this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="70940-111">Asynchronii – definováno</span><span class="sxs-lookup"><span data-stu-id="70940-111">Asynchrony defined</span></span>

<span data-ttu-id="70940-112">Předchozí bod – tento asynchronii je nezávislý na využití více vláken – je vysvětlovat trochu dál.</span><span class="sxs-lookup"><span data-stu-id="70940-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="70940-113">Existují tři koncepty, které jsou někdy související, ale výhradně nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="70940-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="70940-114">Concurrency Když je v překrývajících se časových obdobích prováděno více výpočtů.</span><span class="sxs-lookup"><span data-stu-id="70940-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="70940-115">Paralelismu v případě, že se více výpočetních nebo několika částí jednoho výpočtu spouští přesně ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="70940-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="70940-116">Asynchronii Když se jeden nebo víc výpočtů může spouštět odděleně od hlavního toku programu.</span><span class="sxs-lookup"><span data-stu-id="70940-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="70940-117">Všechny tři jsou kolmé koncepty, ale dají se snadno využít, zejména při jejich použití dohromady.</span><span class="sxs-lookup"><span data-stu-id="70940-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="70940-118">Například může být nutné spustit více asynchronních výpočtů paralelně.</span><span class="sxs-lookup"><span data-stu-id="70940-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="70940-119">To neznamená, že paralelismus nebo asynchronii implikuje jednu jinou.</span><span class="sxs-lookup"><span data-stu-id="70940-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="70940-120">Pokud je třeba vzít v úvahu etymology slova "Asynchronous", jsou zapojeny dvě části:</span><span class="sxs-lookup"><span data-stu-id="70940-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="70940-121">"a", což znamená "NOT".</span><span class="sxs-lookup"><span data-stu-id="70940-121">"a", meaning "not".</span></span>
- <span data-ttu-id="70940-122">"synchronní", význam "ve stejnou dobu".</span><span class="sxs-lookup"><span data-stu-id="70940-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="70940-123">Když tyto dvě výrazy zadáte společně, uvidíte, že "asynchronní" znamená ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="70940-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="70940-124">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="70940-124">That's it!</span></span> <span data-ttu-id="70940-125">V této definici neexistuje žádná nenásobení souběžnosti ani paralelismus.</span><span class="sxs-lookup"><span data-stu-id="70940-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="70940-126">To platí také v praxi.</span><span class="sxs-lookup"><span data-stu-id="70940-126">This is also true in practice.</span></span>

<span data-ttu-id="70940-127">V praktických případech jsou asynchronní výpočty v F# nástroji naplánované k provádění nezávisle na hlavním toku programu.</span><span class="sxs-lookup"><span data-stu-id="70940-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="70940-128">To neznamená souběžnost ani paralelismus, ani neznamená, že na pozadí se vždy stane výpočet.</span><span class="sxs-lookup"><span data-stu-id="70940-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="70940-129">V závislosti na povaze výpočtu a prostředí, ve kterém je výpočet prováděn, se asynchronní výpočty mohou dokonce provádět synchronně.</span><span class="sxs-lookup"><span data-stu-id="70940-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="70940-130">Hlavní poznatkem byste měli mít za to, že asynchronní výpočty jsou nezávislé na toku hlavního programu.</span><span class="sxs-lookup"><span data-stu-id="70940-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="70940-131">I když je k dispozici několik záruk, kdy nebo jak se provádí asynchronní výpočty, existují některé přístupy k orchestraci a jejich plánování.</span><span class="sxs-lookup"><span data-stu-id="70940-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="70940-132">Zbývající část tohoto článku se zabývá základními koncepty pro F# asynchronii a používání typů, funkcí a výrazů integrovaných do F#.</span><span class="sxs-lookup"><span data-stu-id="70940-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="70940-133">Základní koncepty</span><span class="sxs-lookup"><span data-stu-id="70940-133">Core concepts</span></span>

<span data-ttu-id="70940-134">V F#nástroji je asynchronní programování na střed kolem tří základních konceptů:</span><span class="sxs-lookup"><span data-stu-id="70940-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="70940-135">Typ `Async<'T>`, který představuje sestavitelný asynchronní výpočet.</span><span class="sxs-lookup"><span data-stu-id="70940-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="70940-136">Funkce modulu `Async`, které umožňují naplánovat asynchronní práci, vytváření asynchronních výpočtů a transformaci asynchronních výsledků.</span><span class="sxs-lookup"><span data-stu-id="70940-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="70940-137">[Výraz výpočtu](../../language-reference/computation-expressions.md)`async { }`, který poskytuje pohodlný Syntax pro sestavování a řízení asynchronních výpočtů.</span><span class="sxs-lookup"><span data-stu-id="70940-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="70940-138">V následujícím příkladu vidíte tyto tři koncepty:</span><span class="sxs-lookup"><span data-stu-id="70940-138">You can see these three concepts in the following example:</span></span>

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

<span data-ttu-id="70940-139">V tomto příkladu je funkce `printTotalFileBytes` typu `string -> Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="70940-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="70940-140">Volání funkce ve skutečnosti neprovede asynchronní výpočet.</span><span class="sxs-lookup"><span data-stu-id="70940-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="70940-141">Místo toho vrátí `Async<unit>`, který funguje jako \* specifikace práce, která má být provedena asynchronně.</span><span class="sxs-lookup"><span data-stu-id="70940-141">Instead, it returns an `Async<unit>` that acts as a \*specification- of the work that is to execute asynchronously.</span></span> <span data-ttu-id="70940-142">Bude volat `Async.AwaitTask` v jeho těle, který převede výsledek <xref:System.IO.File.WriteAllBytesAsync%2A> na odpovídající typ při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="70940-142">It will call `Async.AwaitTask` in its body, which will convert the result of <xref:System.IO.File.WriteAllBytesAsync%2A> to an appropriate type when it is called.</span></span>

<span data-ttu-id="70940-143">Další důležitou linkou je volání `Async.RunSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="70940-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="70940-144">Jedná se o jednu z asynchronních funkcí modulu, které je třeba volat, pokud chcete skutečně provést F# asynchronní výpočet.</span><span class="sxs-lookup"><span data-stu-id="70940-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="70940-145">Toto je zásadní rozdíl se stylem C#/VB `async` programování.</span><span class="sxs-lookup"><span data-stu-id="70940-145">This is a fundamental difference with the C#/VB style of `async` programming.</span></span> <span data-ttu-id="70940-146">V F#asynchronních výpočtech se můžete představit jako **studené úlohy**.</span><span class="sxs-lookup"><span data-stu-id="70940-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="70940-147">Je nutné je explicitně spustit ke skutečnému provedení.</span><span class="sxs-lookup"><span data-stu-id="70940-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="70940-148">To má několik výhod, protože umožňuje kombinovat a sekvencovat asynchronní práci mnohem jednodušší než v C#/VB.</span><span class="sxs-lookup"><span data-stu-id="70940-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C#/VB.</span></span>

## <a name="combining-asynchronous-computations"></a><span data-ttu-id="70940-149">Kombinování asynchronních výpočtů</span><span class="sxs-lookup"><span data-stu-id="70940-149">Combining asynchronous computations</span></span>

<span data-ttu-id="70940-150">Tady je příklad, který sestaví na předchozím základě kombinováním výpočtů:</span><span class="sxs-lookup"><span data-stu-id="70940-150">Here is an example that builds upon the previous one by combining computations:</span></span>

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

<span data-ttu-id="70940-151">Jak vidíte, funkce `main` obsahuje ještě několik dalších volání.</span><span class="sxs-lookup"><span data-stu-id="70940-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="70940-152">V koncepčním případě provede následující:</span><span class="sxs-lookup"><span data-stu-id="70940-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="70940-153">Transformujte argumenty příkazového řádku na `Async<unit>` výpočtů pomocí `Array.map`.</span><span class="sxs-lookup"><span data-stu-id="70940-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="70940-154">Vytvořte `Async<'T[]>`, který plánuje a spouští `printTotalFileBytes` výpočty paralelně při spuštění.</span><span class="sxs-lookup"><span data-stu-id="70940-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="70940-155">Vytvořte `Async<unit>`, který spustí paralelní výpočet a ignoruje jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="70940-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="70940-156">Explicitně spusťte poslední výpočet pomocí `Async.RunSynchronously` a zablokujte ho, dokud se nedokončí.</span><span class="sxs-lookup"><span data-stu-id="70940-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="70940-157">Když se tento program spustí, `printTotalFileBytes` běží paralelně pro každý argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="70940-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="70940-158">Vzhledem k tomu, že asynchronní výpočty provádějí nezávisle na programu flow, neexistuje žádné pořadí, ve kterém tisknou své informace a dokončí provádění.</span><span class="sxs-lookup"><span data-stu-id="70940-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="70940-159">Výpočty budou naplánovány paralelně, ale jejich pořadí provádění není zaručeno.</span><span class="sxs-lookup"><span data-stu-id="70940-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequencing-asynchronous-computations"></a><span data-ttu-id="70940-160">Sekvence asynchronních výpočtů</span><span class="sxs-lookup"><span data-stu-id="70940-160">Sequencing asynchronous computations</span></span>

<span data-ttu-id="70940-161">Vzhledem k tomu, že `Async<'T>` je specifikace práce, nikoli už spuštěná úloha, můžete snadno provádět komplikovanější transformace.</span><span class="sxs-lookup"><span data-stu-id="70940-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="70940-162">Tady je příklad, který sekvencí sadu asynchronních výpočtů, aby se prováděly po druhém.</span><span class="sxs-lookup"><span data-stu-id="70940-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

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
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="70940-163">Tím se naplánuje `printTotalFileBytes` provést v pořadí prvků `argv` místo jejich souběžného naplánování.</span><span class="sxs-lookup"><span data-stu-id="70940-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="70940-164">Vzhledem k tomu, že se další položka nebude naplánovat až po dokončení posledního výpočtu, jsou výpočty sekvencované tak, že při jejich provádění nedojde k překrytí.</span><span class="sxs-lookup"><span data-stu-id="70940-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="70940-165">Důležité funkce asynchronního modulu</span><span class="sxs-lookup"><span data-stu-id="70940-165">Important Async module functions</span></span>

<span data-ttu-id="70940-166">Při psaní asynchronního kódu v F# , obvykle budete pracovat s architekturou, která zpracovává plánování výpočtů za vás.</span><span class="sxs-lookup"><span data-stu-id="70940-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="70940-167">Nejedná se však vždy o případ, takže je dobré zjistit různé počáteční funkce pro plánování asynchronní práce.</span><span class="sxs-lookup"><span data-stu-id="70940-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="70940-168">Vzhledem F# k tomu, že asynchronní výpočty jsou _specifikace_ práce, nikoli reprezentace práce, která je již spuštěna, musí být explicitně spuštěny pomocí počáteční funkce.</span><span class="sxs-lookup"><span data-stu-id="70940-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="70940-169">Existuje mnoho [asynchronních spouštěcích funkcí](https://msdn.microsoft.com/library/ee370232.aspx) , které jsou užitečné v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="70940-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="70940-170">V následující části jsou popsány některé nejběžnější funkce spouštění.</span><span class="sxs-lookup"><span data-stu-id="70940-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="70940-171">Async. StartChild –</span><span class="sxs-lookup"><span data-stu-id="70940-171">Async.StartChild</span></span>

<span data-ttu-id="70940-172">Spustí podřízený výpočet v rámci asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70940-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="70940-173">To umožňuje spustit více asynchronních výpočtů současně.</span><span class="sxs-lookup"><span data-stu-id="70940-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="70940-174">Podřízený výpočet sdílí token zrušení s nadřazeným výpočtem.</span><span class="sxs-lookup"><span data-stu-id="70940-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="70940-175">Pokud je nadřazený výpočet zrušen, je také zrušen podřízený výpočet.</span><span class="sxs-lookup"><span data-stu-id="70940-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="70940-176">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-176">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="70940-177">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-177">When to use:</span></span>

- <span data-ttu-id="70940-178">Pokud chcete spustit více asynchronních výpočtů současně, nikoli v jednom okamžiku, ale nemusíte je naplánovat paralelně.</span><span class="sxs-lookup"><span data-stu-id="70940-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="70940-179">Pokud chcete vytvořit propojení životnosti podřízeného výpočtu s nadřazeným výpočtem.</span><span class="sxs-lookup"><span data-stu-id="70940-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="70940-180">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-180">What to watch out for:</span></span>

- <span data-ttu-id="70940-181">Spuštění více výpočtů s `Async.StartChild` není stejné jako při jejich plánování paralelně.</span><span class="sxs-lookup"><span data-stu-id="70940-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="70940-182">Pokud chcete naplánovat souběžné výpočty, použijte `Async.Parallel`.</span><span class="sxs-lookup"><span data-stu-id="70940-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="70940-183">Zrušením nadřazeného výpočtu se spustí zrušení všech podřízených výpočtů, které začaly.</span><span class="sxs-lookup"><span data-stu-id="70940-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="70940-184">Async. StartImmediate –</span><span class="sxs-lookup"><span data-stu-id="70940-184">Async.StartImmediate</span></span>

<span data-ttu-id="70940-185">Spustí asynchronní výpočet, který se spouští okamžitě na aktuálním vlákně operačního systému.</span><span class="sxs-lookup"><span data-stu-id="70940-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="70940-186">To je užitečné, pokud potřebujete během výpočtu aktualizovat něco v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="70940-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="70940-187">Například pokud asynchronní výpočet musí aktualizovat uživatelské rozhraní (například aktualizace indikátoru průběhu), je třeba použít `Async.StartImmediate`.</span><span class="sxs-lookup"><span data-stu-id="70940-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="70940-188">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="70940-189">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-189">When to use:</span></span>

- <span data-ttu-id="70940-190">Pokud potřebujete něco aktualizovat v volajícím vlákně uprostřed asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70940-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="70940-191">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-191">What to watch out for:</span></span>

- <span data-ttu-id="70940-192">Kód v asynchronním výpočtu se spustí na jakémkoli vlákně, na kterém je naplánováno.</span><span class="sxs-lookup"><span data-stu-id="70940-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="70940-193">To může být problematické, pokud je toto vlákno v nějakých citlivých případech, jako je například vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70940-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="70940-194">V takových případech je `Async.StartImmediate` nejspíš nevhodné použít.</span><span class="sxs-lookup"><span data-stu-id="70940-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="70940-195">Async. Startastask –</span><span class="sxs-lookup"><span data-stu-id="70940-195">Async.StartAsTask</span></span>

<span data-ttu-id="70940-196">Provede výpočet ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="70940-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="70940-197">Vrátí <xref:System.Threading.Tasks.Task%601>, který bude dokončen v odpovídajícím stavu po ukončení výpočtu (vytvoří výsledek, vyvolá výjimku nebo se zruší).</span><span class="sxs-lookup"><span data-stu-id="70940-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="70940-198">Pokud není k dispozici žádný token zrušení, použije se výchozí token zrušení.</span><span class="sxs-lookup"><span data-stu-id="70940-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="70940-199">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="70940-200">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-200">When to use:</span></span>

- <span data-ttu-id="70940-201">Pokud potřebujete zavolat do rozhraní .NET API, které očekává <xref:System.Threading.Tasks.Task%601> pro reprezentaci výsledku asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70940-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="70940-202">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-202">What to watch out for:</span></span>

- <span data-ttu-id="70940-203">Toto volání přidělí další objekt `Task`, což může zvýšit režii v případě, že se často používá.</span><span class="sxs-lookup"><span data-stu-id="70940-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="70940-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="70940-204">Async.Parallel</span></span>

<span data-ttu-id="70940-205">Plánuje sekvenci asynchronních výpočtů, které se mají spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="70940-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="70940-206">Stupeň paralelismu lze volitelně vyladit/omezit zadáním parametru `maxDegreesOfParallelism`.</span><span class="sxs-lookup"><span data-stu-id="70940-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="70940-207">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="70940-208">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="70940-208">When to use it:</span></span>

- <span data-ttu-id="70940-209">Pokud potřebujete spustit sadu výpočetních prostředků současně a nemusíte přitom spoléhat na jejich pořadí spouštění.</span><span class="sxs-lookup"><span data-stu-id="70940-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="70940-210">Pokud nepotřebujete výsledky z plánovaných výpočtů paralelně, dokud nebudou dokončeny všechny.</span><span class="sxs-lookup"><span data-stu-id="70940-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="70940-211">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-211">What to watch out for:</span></span>

- <span data-ttu-id="70940-212">Po dokončení všech výpočtů máte přístup pouze k výslednému poli hodnot.</span><span class="sxs-lookup"><span data-stu-id="70940-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="70940-213">Výpočty se budou spouštět, ale skončí naplánovaných.</span><span class="sxs-lookup"><span data-stu-id="70940-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="70940-214">To znamená, že nemůžete spoléhat na jejich pořadí provádění.</span><span class="sxs-lookup"><span data-stu-id="70940-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="70940-215">Async. sekvenční</span><span class="sxs-lookup"><span data-stu-id="70940-215">Async.Sequential</span></span>

<span data-ttu-id="70940-216">Naplánuje sekvenci asynchronních výpočtů, které se mají provést v pořadí, v jakém jsou předány.</span><span class="sxs-lookup"><span data-stu-id="70940-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="70940-217">První výpočet se spustí, potom klikněte na další atd.</span><span class="sxs-lookup"><span data-stu-id="70940-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="70940-218">Žádné výpočty se nespustí paralelně.</span><span class="sxs-lookup"><span data-stu-id="70940-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="70940-219">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="70940-220">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="70940-220">When to use it:</span></span>

- <span data-ttu-id="70940-221">Pokud potřebujete spustit více výpočtů v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="70940-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="70940-222">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-222">What to watch out for:</span></span>

- <span data-ttu-id="70940-223">Po dokončení všech výpočtů máte přístup pouze k výslednému poli hodnot.</span><span class="sxs-lookup"><span data-stu-id="70940-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="70940-224">Výpočty se spustí v pořadí, v jakém jsou předány této funkci, což může znamenat, že uplyne další doba před vrácením výsledků.</span><span class="sxs-lookup"><span data-stu-id="70940-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="70940-225">Async. Awaittask –</span><span class="sxs-lookup"><span data-stu-id="70940-225">Async.AwaitTask</span></span>

<span data-ttu-id="70940-226">Vrátí asynchronní výpočet, který čeká na dokončení daného <xref:System.Threading.Tasks.Task%601> a vrátí jeho výsledek jako `Async<'T>`.</span><span class="sxs-lookup"><span data-stu-id="70940-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="70940-227">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="70940-228">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-228">When to use:</span></span>

- <span data-ttu-id="70940-229">Když spotřebováváte rozhraní .NET API, které vrací <xref:System.Threading.Tasks.Task%601> v rámci F# asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70940-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="70940-230">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-230">What to watch out for:</span></span>

- <span data-ttu-id="70940-231">Výjimky jsou zabaleny v <xref:System.AggregateException> následující po konvenci paralelní knihovny Tasks, a to se liší od F# toho, jak obvykle výjimky asynchronních povrchů.</span><span class="sxs-lookup"><span data-stu-id="70940-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="70940-232">Async. catch</span><span class="sxs-lookup"><span data-stu-id="70940-232">Async.Catch</span></span>

<span data-ttu-id="70940-233">Vytvoří asynchronní výpočet, který spustí daný `Async<'T>`a vrátí `Async<Choice<'T, exn>>`.</span><span class="sxs-lookup"><span data-stu-id="70940-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="70940-234">Pokud se daná `Async<'T>` úspěšně dokončí, vrátí se výsledná hodnota `Choice1Of2`.</span><span class="sxs-lookup"><span data-stu-id="70940-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="70940-235">Pokud je výjimka vyvolána před dokončením, je vrácena `Choice2of2` s vyvolanou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="70940-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="70940-236">Pokud se používá v asynchronním výpočtu, který je sám složený z mnoha výpočtů, a jeden z těchto výpočtů vyvolá výjimku, Výpočet zahrnuje také úplné zastavení.</span><span class="sxs-lookup"><span data-stu-id="70940-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="70940-237">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="70940-238">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-238">When to use:</span></span>

- <span data-ttu-id="70940-239">Při provádění asynchronní práce, která může selhat s výjimkou a chcete tuto výjimku zpracovat v volajícím.</span><span class="sxs-lookup"><span data-stu-id="70940-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="70940-240">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-240">What to watch out for:</span></span>

- <span data-ttu-id="70940-241">Pokud používáte kombinované nebo sekvencované asynchronní výpočty, výpočet zahrnující výpočty se úplně zastaví, pokud jeden z jeho "interních" výpočtů vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="70940-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="70940-242">Async. Ignore</span><span class="sxs-lookup"><span data-stu-id="70940-242">Async.Ignore</span></span>

<span data-ttu-id="70940-243">Vytvoří asynchronní výpočet, který spustí daný výpočet a ignoruje jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="70940-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="70940-244">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="70940-245">Kdy použít:</span><span class="sxs-lookup"><span data-stu-id="70940-245">When to use:</span></span>

- <span data-ttu-id="70940-246">Pokud máte asynchronní výpočet, jehož výsledek není potřeba.</span><span class="sxs-lookup"><span data-stu-id="70940-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="70940-247">To se podobá kódu `ignore` pro neasynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="70940-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="70940-248">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-248">What to watch out for:</span></span>

- <span data-ttu-id="70940-249">Pokud je nutné použít tuto funkci, protože chcete použít `Async.Start` nebo jinou funkci, která vyžaduje `Async<unit>`, zvažte, zda je zahození výsledku v pořádku.</span><span class="sxs-lookup"><span data-stu-id="70940-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="70940-250">Vypuštění výsledků, které se nehodí pro podpis typu, by nemělo být obecně provedeno.</span><span class="sxs-lookup"><span data-stu-id="70940-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="70940-251">Async. metodu RunSynchronously nelze</span><span class="sxs-lookup"><span data-stu-id="70940-251">Async.RunSynchronously</span></span>

<span data-ttu-id="70940-252">Spustí asynchronní výpočet a počká na jeho výsledek na volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="70940-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="70940-253">Toto volání je blokováno.</span><span class="sxs-lookup"><span data-stu-id="70940-253">This call is blocking.</span></span>

<span data-ttu-id="70940-254">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="70940-255">Kdy ji použít:</span><span class="sxs-lookup"><span data-stu-id="70940-255">When to use it:</span></span>

- <span data-ttu-id="70940-256">Pokud ho potřebujete, používejte ho jenom jednou v aplikaci – v vstupním bodě pro spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="70940-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="70940-257">Pokud nezáleží na výkonu a chcete spustit sadu dalších asynchronních operací najednou.</span><span class="sxs-lookup"><span data-stu-id="70940-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="70940-258">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-258">What to watch out for:</span></span>

- <span data-ttu-id="70940-259">Volání `Async.RunSynchronously` blokuje volající vlákno, dokud se spuštění nedokončí.</span><span class="sxs-lookup"><span data-stu-id="70940-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="70940-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="70940-260">Async.Start</span></span>

<span data-ttu-id="70940-261">Spustí asynchronní výpočet ve fondu vláken, který vrací `unit`.</span><span class="sxs-lookup"><span data-stu-id="70940-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="70940-262">Nečeká na výsledek.</span><span class="sxs-lookup"><span data-stu-id="70940-262">Doesn't wait for its result.</span></span> <span data-ttu-id="70940-263">Vnořené výpočty zahájené s `Async.Start` jsou zcela spouštěny nezávisle na nadřazeném výpočtu, který je volal.</span><span class="sxs-lookup"><span data-stu-id="70940-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="70940-264">Jejich životnost není svázána s žádným nadřazeným výpočtem.</span><span class="sxs-lookup"><span data-stu-id="70940-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="70940-265">Pokud je nadřazený výpočet zrušený, žádné podřízené výpočty se neruší.</span><span class="sxs-lookup"><span data-stu-id="70940-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="70940-266">Podpis:</span><span class="sxs-lookup"><span data-stu-id="70940-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="70940-267">Použijte pouze v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="70940-267">Use only when:</span></span>

- <span data-ttu-id="70940-268">Máte asynchronní výpočet, který nepřinese výsledek nebo vyžaduje zpracování jednoho.</span><span class="sxs-lookup"><span data-stu-id="70940-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="70940-269">Po dokončení asynchronního výpočtu nemusíte znát.</span><span class="sxs-lookup"><span data-stu-id="70940-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="70940-270">Nezáleží na tom, na kterém vlákně běží asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="70940-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="70940-271">Nemusíte znát ani podávat informace o výjimkách vyplývajících z úkolu.</span><span class="sxs-lookup"><span data-stu-id="70940-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="70940-272">Co je potřeba sledovat:</span><span class="sxs-lookup"><span data-stu-id="70940-272">What to watch out for:</span></span>

- <span data-ttu-id="70940-273">Výjimky vyvolané výpočty zahájenými pomocí `Async.Start` nejsou šířeny volajícímu.</span><span class="sxs-lookup"><span data-stu-id="70940-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="70940-274">Zásobník volání bude zcela zrušeno.</span><span class="sxs-lookup"><span data-stu-id="70940-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="70940-275">Všechny ovlivněné práce (například volání `printfn`) spuštěné s `Async.Start` nezpůsobí, že se projeví v hlavním vlákně provádění programu.</span><span class="sxs-lookup"><span data-stu-id="70940-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperating-with-net"></a><span data-ttu-id="70940-276">Spolupráce s .NET</span><span class="sxs-lookup"><span data-stu-id="70940-276">Interoperating with .NET</span></span>

<span data-ttu-id="70940-277">Možná pracujete s knihovnou .NET nebo C# základem kódu, který používá asynchronní programování typu [Async/await](../../../standard/async.md).</span><span class="sxs-lookup"><span data-stu-id="70940-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="70940-278">Vzhledem C# k tomu, že většina knihoven .net používá <xref:System.Threading.Tasks.Task%601> a <xref:System.Threading.Tasks.Task> typy jako základní abstrakce namísto `Async<'T>`, je nutné překročit hranici mezi těmito dvěma přístupy do asynchronii.</span><span class="sxs-lookup"><span data-stu-id="70940-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="70940-279">Jak pracovat s .NET Async a `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="70940-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="70940-280">Práce s asynchronními knihovnami a základem kódu .NET, které používají <xref:System.Threading.Tasks.Task%601> (tj. asynchronní výpočty, které mají návratové hodnoty), jsou jednoduché a mají F#integrovanou podporu s.</span><span class="sxs-lookup"><span data-stu-id="70940-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="70940-281">Můžete použít funkci `Async.AwaitTask` pro čekání na asynchronní výpočet rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="70940-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="70940-282">Můžete použít funkci `Async.StartAsTask` k předání asynchronního výpočtu volajícímu .NET:</span><span class="sxs-lookup"><span data-stu-id="70940-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="70940-283">Jak pracovat s .NET Async a `Task`</span><span class="sxs-lookup"><span data-stu-id="70940-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="70940-284">Chcete-li pracovat s rozhraními API, která používají <xref:System.Threading.Tasks.Task> (tj. asynchronní výpočty .NET, které nevracejí hodnotu), bude pravděpodobně nutné přidat další funkci, která převede `Async<'T>` na <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="70940-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="70940-285">Již existuje `Async.AwaitTask`, který jako vstup přijímá <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="70940-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="70940-286">S tímto a dříve definovanou funkcí `startTaskFromAsyncUnit` můžete začít a očekávat <xref:System.Threading.Tasks.Task> typy z F# asynchronního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70940-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multithreading"></a><span data-ttu-id="70940-287">Vztah k multithreadingu</span><span class="sxs-lookup"><span data-stu-id="70940-287">Relationship to multithreading</span></span>

<span data-ttu-id="70940-288">I když je vlákno v rámci tohoto článku zmíněno, je třeba pamatovat si dva důležité věci:</span><span class="sxs-lookup"><span data-stu-id="70940-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="70940-289">Neexistuje žádné spřažení mezi asynchronním výpočtem a vláknem, pokud není explicitně spuštěno v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="70940-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="70940-290">Asynchronní programování v F# není abstrakce pro multithreading.</span><span class="sxs-lookup"><span data-stu-id="70940-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="70940-291">Například výpočet může být v závislosti na povaze práce spuštěn ve vlastním vlákně volajícího.</span><span class="sxs-lookup"><span data-stu-id="70940-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="70940-292">Výpočet může také "Přejít" mezi vlákny a jejich vypůjčení po krátkou dobu, aby bylo možné provádět užitečnou práci v obdobích "čekání" (například při přenosu síťového hovoru).</span><span class="sxs-lookup"><span data-stu-id="70940-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="70940-293">I F# když poskytuje některé možnosti, jak spustit asynchronní výpočet v aktuálním vlákně (nebo explicitně ne na aktuálním vlákně), asynchronii obecně není přidružená k určité strategii vláken.</span><span class="sxs-lookup"><span data-stu-id="70940-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="70940-294">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70940-294">See also</span></span>

- [<span data-ttu-id="70940-295">F# Asynchronní programovací model</span><span class="sxs-lookup"><span data-stu-id="70940-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="70940-296">F# Asynchronní Průvodce jet. com</span><span class="sxs-lookup"><span data-stu-id="70940-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="70940-297">F#Průvodce asynchronním programováním pro zábavu a zisk</span><span class="sxs-lookup"><span data-stu-id="70940-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="70940-298">Asynchronní v C# a F#: asynchronní možná úskalí vC#</span><span class="sxs-lookup"><span data-stu-id="70940-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
