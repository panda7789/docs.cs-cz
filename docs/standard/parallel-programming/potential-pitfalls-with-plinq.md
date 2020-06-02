---
title: Potenciální nástrah s PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: b4d58734fba4b834d5f5819a6bf19da0b7b7e8db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285310"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="56b43-102">Potenciální nástrah s PLINQ</span><span class="sxs-lookup"><span data-stu-id="56b43-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="56b43-103">V mnoha případech může PLINQ poskytnout významné zlepšení výkonu při sekvenčních dotazech LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="56b43-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="56b43-104">Práce virtuálního provádění dotazů však zavádí složitost, která může vést k problémům, které se v sekvenčním kódu nevyskytují jako běžné nebo nejsou vůbec k dispozici.</span><span class="sxs-lookup"><span data-stu-id="56b43-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="56b43-105">Toto téma uvádí některé postupy, které se vyhnete při psaní dotazů PLINQ.</span><span class="sxs-lookup"><span data-stu-id="56b43-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="56b43-106">Nepředpokládat, že paralelní je vždycky rychlejší</span><span class="sxs-lookup"><span data-stu-id="56b43-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="56b43-107">Paralelismus někdy způsobí, že se PLINQ dotaz spustí pomaleji, než je jeho ekvivalent LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="56b43-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="56b43-108">Základní pravidlo pro palec je, že dotazy, které mají málo zdrojových elementů a rychlé delegáty uživatele, jsou pravděpodobně zrychlení mnohem nepravděpodobné.</span><span class="sxs-lookup"><span data-stu-id="56b43-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="56b43-109">Vzhledem k tomu, že je v výkonu mnoho faktorů, doporučujeme změřit skutečné výsledky před rozhodnutím, jestli chcete použít PLINQ.</span><span class="sxs-lookup"><span data-stu-id="56b43-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="56b43-110">Další informace naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="56b43-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="56b43-111">Vyhněte se zápisu do sdílených umístění paměti</span><span class="sxs-lookup"><span data-stu-id="56b43-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="56b43-112">V sekvenčním kódu není běžné číst z nebo zapisovat do statických proměnných nebo polí třídy.</span><span class="sxs-lookup"><span data-stu-id="56b43-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="56b43-113">Kdykoli však více vláken přistupuje k těmto proměnným současně, existuje velký potenciál pro konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="56b43-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="56b43-114">I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci můžou snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="56b43-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="56b43-115">Proto doporučujeme, abyste se vyhnuli nebo alespoň omezili přístup ke sdílenému stavu v dotazu PLINQ co nejvíce.</span><span class="sxs-lookup"><span data-stu-id="56b43-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="56b43-116">Vyhnout se paralelnímu využití</span><span class="sxs-lookup"><span data-stu-id="56b43-116">Avoid over-parallelization</span></span>

<span data-ttu-id="56b43-117">Pomocí metody se `AsParallel` účtují režijní náklady na rozdělení zdrojové kolekce a synchronizaci pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="56b43-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="56b43-118">Výhody paralelismu jsou dále omezeny počtem procesorů v počítači.</span><span class="sxs-lookup"><span data-stu-id="56b43-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="56b43-119">Neexistují žádné zrychlení, které by bylo možné vymezit spuštěním více výpočetních vláken vázaných na pouze jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="56b43-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="56b43-120">Proto musíte mít pozor, abyste paralelizovat dotaz.</span><span class="sxs-lookup"><span data-stu-id="56b43-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="56b43-121">Nejběžnější scénář, ve kterém může dojít k paralelnímu navýšení, je ve vnořených dotazech, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="56b43-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="56b43-122">V takovém případě je nejlepší paralelizovat jenom vnější zdroj dat (Customers), pokud neplatí jedna nebo víc z těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="56b43-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="56b43-123">Vnitřní zdroj dat (zák. Objednávky) se označují jako velmi dlouhé.</span><span class="sxs-lookup"><span data-stu-id="56b43-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="56b43-124">V každé objednávce provádíte nákladný výpočet.</span><span class="sxs-lookup"><span data-stu-id="56b43-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="56b43-125">(Operace uvedená v příkladu není nákladná.)</span><span class="sxs-lookup"><span data-stu-id="56b43-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="56b43-126">Pro cílový systém je známo, že má dostatek procesorů pro zpracování počtu vláken, která budou vytvořena virtuálního dotazem `cust.Orders` .</span><span class="sxs-lookup"><span data-stu-id="56b43-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="56b43-127">Ve všech případech je nejlepším způsobem, jak určit optimální obrazec dotazu, testování a měření.</span><span class="sxs-lookup"><span data-stu-id="56b43-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="56b43-128">Další informace najdete v tématu [Postupy: měření výkonu dotazu PLINQ](how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="56b43-128">For more information, see [How to: Measure PLINQ Query Performance](how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="56b43-129">Nepoužívejte volání metod, které nejsou bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="56b43-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="56b43-130">Zápis na metody instancí bez bezpečného přístupu z více vláken může vést k poškození dat, které může nebo nemusí být v programu nedetekováno.</span><span class="sxs-lookup"><span data-stu-id="56b43-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="56b43-131">Může také vést k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="56b43-131">It can also lead to exceptions.</span></span> <span data-ttu-id="56b43-132">V následujícím příkladu by se více vláken pokoušelo zavolat `FileStream.Write` metodu současně, což není podporováno třídou.</span><span class="sxs-lookup"><span data-stu-id="56b43-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="56b43-133">Omezení volání metod bezpečných pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="56b43-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="56b43-134">Většina statických metod v .NET Framework je bezpečná pro přístup z více vláken a je možné ji volat z více vláken současně.</span><span class="sxs-lookup"><span data-stu-id="56b43-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="56b43-135">Nicméně i v těchto případech může synchronizace vést k významnému zpomalení dotazu.</span><span class="sxs-lookup"><span data-stu-id="56b43-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="56b43-136">Můžete to otestovat sami vložením některých volání do <xref:System.Console.WriteLine%2A> v dotazech.</span><span class="sxs-lookup"><span data-stu-id="56b43-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="56b43-137">I když se tato metoda používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v dotazech PLINQ.</span><span class="sxs-lookup"><span data-stu-id="56b43-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="56b43-138">Vyhnout se zbytečným operacím řazení</span><span class="sxs-lookup"><span data-stu-id="56b43-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="56b43-139">Když PLINQ spustí dotaz paralelně, rozdělí zdrojovou sekvenci na oddíly, které lze provozovat souběžně ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="56b43-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="56b43-140">Ve výchozím nastavení je pořadí, ve kterém jsou zpracovány oddíly, a výsledky jsou dodány (s výjimkou operátorů, jako je `OrderBy` ).</span><span class="sxs-lookup"><span data-stu-id="56b43-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="56b43-141">Můžete určit, aby PLINQ zachoval řazení libovolné zdrojové sekvence, ale má negativní vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="56b43-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="56b43-142">Nejlepší postup, kdykoli je to možné, je strukturování dotazů, které nespoléhají na zachování pořadí.</span><span class="sxs-lookup"><span data-stu-id="56b43-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="56b43-143">Další informace naleznete v tématu [pořadí zachování v PLINQ](order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="56b43-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="56b43-144">Preferovat ForAll na ForEach, pokud je to možné</span><span class="sxs-lookup"><span data-stu-id="56b43-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="56b43-145">I když PLINQ spustí dotaz na více vláknech, pokud výsledky využijete ve `foreach` smyčce ( `For Each` v Visual Basic), musí být výsledky dotazu sloučeny zpět do jednoho vlákna a k sériovému přístupu je zajištěny enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="56b43-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="56b43-146">V některých případech to není nevyhnutelné; kdykoli je to možné, použijte `ForAll` metodu, která umožní každému vláknu výstupovat vlastní výsledky, například zapsáním do kolekce bezpečné pro přístup z více vláken, jako je například <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="56b43-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="56b43-147">Stejný problém se týká <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="56b43-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="56b43-148">Jinými slovy, `source.AsParallel().Where().ForAll(...)` by mělo být důrazně upřednostňováno na `Parallel.ForEach(source.AsParallel().Where(), ...)` .</span><span class="sxs-lookup"><span data-stu-id="56b43-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="56b43-149">Informace o problémech spřažení vláken</span><span class="sxs-lookup"><span data-stu-id="56b43-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="56b43-150">Některé technologie, například interoperabilita modelu COM pro součásti s jedním vláknem (STA), model Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spouštění kódu v konkrétním vlákně.</span><span class="sxs-lookup"><span data-stu-id="56b43-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="56b43-151">Například v model Windows Forms i WPF může být ovládací prvek k dispozici pouze ve vlákně, ve kterém byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="56b43-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="56b43-152">Pokud se pokusíte o přístup ke sdílenému stavu ovládacího prvku model Windows Forms v PLINQ dotazu, je vyvolána výjimka, pokud je spuštěn v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="56b43-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="56b43-153">(Toto nastavení se dá vypnout.) Nicméně pokud je váš dotaz použit ve vlákně uživatelského rozhraní, pak můžete získat přístup k ovládacímu prvku ze `foreach` smyčky, která vytvoří výčet výsledků dotazu, protože tento kód je spuštěn pouze v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="56b43-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="56b43-154">Nepředpokládá se, že iterace ForEach, for a ForAll se vždy spouštějí paralelně.</span><span class="sxs-lookup"><span data-stu-id="56b43-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="56b43-155">Je důležité mít na paměti, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> , <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčka nemusí být spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="56b43-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="56b43-156">Proto byste se měli vyhnout psaní kódu, který závisí na správnosti paralelního provádění iterací nebo při provádění iterací v jakémkoli konkrétním pořadí.</span><span class="sxs-lookup"><span data-stu-id="56b43-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="56b43-157">Například tento kód může zablokovat:</span><span class="sxs-lookup"><span data-stu-id="56b43-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="56b43-158">V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace na událost čekají.</span><span class="sxs-lookup"><span data-stu-id="56b43-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="56b43-159">Žádná z čekacích iterací nemůže být dokončena, dokud se nedokončí iterace nastavení události.</span><span class="sxs-lookup"><span data-stu-id="56b43-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="56b43-160">Je však možné, že čekající iterace zablokují všechna vlákna, která se používají ke spuštění paralelní smyčky, před tím, než bude iterace nastavení událostí vykonána.</span><span class="sxs-lookup"><span data-stu-id="56b43-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="56b43-161">Výsledkem je zablokování – iterace nastavení události se nikdy nespustí a čekací iterace se nikdy neprobudí.</span><span class="sxs-lookup"><span data-stu-id="56b43-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="56b43-162">Konkrétně jedna iterace paralelní smyčky by nikdy neměla čekat na další iteraci smyčky, aby bylo možné postupovat.</span><span class="sxs-lookup"><span data-stu-id="56b43-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="56b43-163">Pokud se paralelní smyčka rozhodne naplánovat iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.</span><span class="sxs-lookup"><span data-stu-id="56b43-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="56b43-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="56b43-164">See also</span></span>

- [<span data-ttu-id="56b43-165">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="56b43-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
