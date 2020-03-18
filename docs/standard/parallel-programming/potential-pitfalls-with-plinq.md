---
title: Potenciální úskalí s PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 3ddc0c013335e6a7b4708a5dd8be0b2247b2f60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74716257"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="49d16-102">Potenciální úskalí s PLINQ</span><span class="sxs-lookup"><span data-stu-id="49d16-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="49d16-103">V mnoha případech PLINQ může poskytnout významné zlepšení výkonu oproti sekvenční LINQ na objekty dotazy.</span><span class="sxs-lookup"><span data-stu-id="49d16-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="49d16-104">Práce paralelizace spuštění dotazu však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou tak běžné nebo se vůbec nevyskytují.</span><span class="sxs-lookup"><span data-stu-id="49d16-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="49d16-105">Toto téma uvádí některé postupy, kterým je třeba se vyhnout při psaní dotazů PLINQ.</span><span class="sxs-lookup"><span data-stu-id="49d16-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="49d16-106">Nepředpokládejte, že paralelní je vždy rychlejší</span><span class="sxs-lookup"><span data-stu-id="49d16-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="49d16-107">Paralelizace někdy způsobí, že dotaz PLINQ spustit pomaleji než jeho LINQ na objekty ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="49d16-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="49d16-108">Základní pravidlo je, že dotazy, které mají málo zdrojových prvků a rychlé uživatelské delegáty je nepravděpodobné, že urychlit hodně.</span><span class="sxs-lookup"><span data-stu-id="49d16-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="49d16-109">Však vzhledem k tomu, že mnoho faktorů jsou zapojeny do výkonu, doporučujeme měřit skutečné výsledky před se rozhodnete, zda použít PLINQ.</span><span class="sxs-lookup"><span data-stu-id="49d16-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="49d16-110">Další informace naleznete [v tématu Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="49d16-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="49d16-111">Vyhněte se zápisu do sdílených umístění paměti</span><span class="sxs-lookup"><span data-stu-id="49d16-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="49d16-112">V sekvenčním kódu není neobvyklé číst nebo zapisovat do statických proměnných nebo polí tříd.</span><span class="sxs-lookup"><span data-stu-id="49d16-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="49d16-113">Však vždy, když více vláken přístup k těmto proměnným současně, je velký potenciál pro podmínky závodu.</span><span class="sxs-lookup"><span data-stu-id="49d16-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="49d16-114">I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci může poškodit výkon.</span><span class="sxs-lookup"><span data-stu-id="49d16-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="49d16-115">Proto doporučujeme vyhnout nebo alespoň omezit přístup ke sdílenému stavu v dotazu PLINQ co nejvíce.</span><span class="sxs-lookup"><span data-stu-id="49d16-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="49d16-116">Vyhněte se nadměrné paralelizaci</span><span class="sxs-lookup"><span data-stu-id="49d16-116">Avoid over-parallelization</span></span>

<span data-ttu-id="49d16-117">Pomocí `AsParallel` metody vzniknou režijní náklady na rozdělení zdrojové kolekce a synchronizaci pracovních podprocesů.</span><span class="sxs-lookup"><span data-stu-id="49d16-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="49d16-118">Výhody paralelizace jsou dále omezeny počtem procesorů v počítači.</span><span class="sxs-lookup"><span data-stu-id="49d16-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="49d16-119">Neexistuje žádné zrychlení, které lze získat spuštěním více vláken vázaných na výpočetní výkon pouze na jednom procesoru.</span><span class="sxs-lookup"><span data-stu-id="49d16-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="49d16-120">Proto je třeba dbát na to, aby příliš paralelizovat dotaz.</span><span class="sxs-lookup"><span data-stu-id="49d16-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="49d16-121">Nejběžnější scénář, ve kterém může dojít k nadměrné paralelizaci, je v nosných dotazech, jak je znázorněno v následujícím fragmentu.</span><span class="sxs-lookup"><span data-stu-id="49d16-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="49d16-122">V tomto případě je nejlepší paralelizovat pouze vnější zdroj dat (zákazníky), pokud neplatí jedna nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="49d16-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="49d16-123">Vnitřní zdroj dat (cust. Objednávky) je známo, že je velmi dlouhá.</span><span class="sxs-lookup"><span data-stu-id="49d16-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="49d16-124">Provádíte nákladné výpočty na každé objednávce.</span><span class="sxs-lookup"><span data-stu-id="49d16-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="49d16-125">(Operace zobrazená v příkladu není nákladná.)</span><span class="sxs-lookup"><span data-stu-id="49d16-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="49d16-126">Cílový systém je známo, že mají dostatek procesorů pro zpracování počtu podprocesů, `cust.Orders`které budou vytvořeny paralelizace dotazu na .</span><span class="sxs-lookup"><span data-stu-id="49d16-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="49d16-127">Ve všech případech je nejlepším způsobem, jak určit optimální tvar dotazu, testování a měření.</span><span class="sxs-lookup"><span data-stu-id="49d16-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="49d16-128">Další informace naleznete v [tématu How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="49d16-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="49d16-129">Vyhněte se volání metod, které nejsou bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="49d16-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="49d16-130">Zápis do metod instancí, které nejsou bezpečné pro přístup z více vláken z dotazu PLINQ, může vést k poškození dat, které může nebo nemusí zůstat v programu neodhaleno.</span><span class="sxs-lookup"><span data-stu-id="49d16-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="49d16-131">To může také vést k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="49d16-131">It can also lead to exceptions.</span></span> <span data-ttu-id="49d16-132">V následujícím příkladu by se více vláken `FileStream.Write` pokoušelo volat metodu současně, což není podporováno třídou.</span><span class="sxs-lookup"><span data-stu-id="49d16-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="49d16-133">Omezit volání na metody bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="49d16-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="49d16-134">Většina statických metod v rozhraní .NET Framework je bezpečná pro přístup z více vláken a lze je volat z více vláken současně.</span><span class="sxs-lookup"><span data-stu-id="49d16-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="49d16-135">Však i v těchto případech synchronizace účastní může vést k významné zpomalení v dotazu.</span><span class="sxs-lookup"><span data-stu-id="49d16-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="49d16-136">Můžete otestovat sami vložením některé <xref:System.Console.WriteLine%2A> volání do dotazů.</span><span class="sxs-lookup"><span data-stu-id="49d16-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="49d16-137">Přestože tato metoda se používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v plinq dotazy.</span><span class="sxs-lookup"><span data-stu-id="49d16-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="49d16-138">Vyhněte se zbytečným operacím objednávání</span><span class="sxs-lookup"><span data-stu-id="49d16-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="49d16-139">Když PLINQ spustí dotaz paralelně, rozdělí zdrojové sekvence do oddílů, které mohou být provozovány současně na více vláken.</span><span class="sxs-lookup"><span data-stu-id="49d16-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="49d16-140">Ve výchozím nastavení pořadí, ve kterém jsou zpracovány oddíly a výsledky jsou dodávány není předvídatelné (s výjimkou operátorů, jako je například `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="49d16-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="49d16-141">Můžete pokyn PLINQ zachovat řazení libovolné zdrojové sekvence, ale to má negativní vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="49d16-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="49d16-142">Osvědčeným postupem, kdykoli je to možné, je strukturovat dotazy tak, aby se nespoléhaly na zachování pořadí.</span><span class="sxs-lookup"><span data-stu-id="49d16-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="49d16-143">Další informace naleznete [v tématu Order Preservation in PLINQ](order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="49d16-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="49d16-144">Preferujte forall na ForEach, když je to možné</span><span class="sxs-lookup"><span data-stu-id="49d16-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="49d16-145">Přestože PLINQ spustí dotaz na více vláken, pokud `foreach` spotřebováváte`For Each` výsledky ve smyčce (v jazyce Visual Basic), pak výsledky dotazu musí být sloučeny zpět do jednoho vlákna a přistupovat sériově čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="49d16-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="49d16-146">V některých případech je to nevyhnutelné; pokud je to však možné, použijte metodu, `ForAll` která umožní každému vláknu vytvořit vlastní <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>výsledky, například zápisem do kolekce bezpečné pro přístup z více vláken, například .</span><span class="sxs-lookup"><span data-stu-id="49d16-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="49d16-147">Stejný problém platí <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>pro .</span><span class="sxs-lookup"><span data-stu-id="49d16-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49d16-148">Jinými slovy, `source.AsParallel().Where().ForAll(...)` by měla `Parallel.ForEach(source.AsParallel().Where(), ...)`být silně upřednostňována .</span><span class="sxs-lookup"><span data-stu-id="49d16-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="49d16-149">Mějte na paměti problémy se spřažením vláken</span><span class="sxs-lookup"><span data-stu-id="49d16-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="49d16-150">Některé technologie, například interoperabilita modelu COM pro součásti sta (Single Threaded Apartment), Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spuštění kódu v určitém vlákně.</span><span class="sxs-lookup"><span data-stu-id="49d16-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="49d16-151">Například ve formulářích systému Windows a WPF ovládací prvek lze přistupovat pouze ve vlákně, ve kterém byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="49d16-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="49d16-152">Pokud se pokusíte o přístup ke sdílenému stavu ovládacího prvku Windows Forms v dotazu PLINQ, je vyvolána výjimka, pokud používáte v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="49d16-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="49d16-153">(Toto nastavení lze vypnout.) Pokud je však dotaz spotřebován ve vlákně uživatelského `foreach` rozhraní, můžete získat přístup k ovládacímu prvku ze smyčky, která obsahuje enumerates výsledky dotazu, protože tento kód se spustí pouze v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="49d16-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="49d16-154">Nepředpokládejte, že iterace ForEach, For a ForAll vždy spustit paralelně</span><span class="sxs-lookup"><span data-stu-id="49d16-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="49d16-155">Je důležité mít na paměti, že <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>jednotlivé <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>iterace v , , nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčky může, ale nemusí provádět paralelně.</span><span class="sxs-lookup"><span data-stu-id="49d16-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="49d16-156">Proto byste se měli vyhnout psaní kódu, který závisí na správnosti na paralelní provádění iterací nebo na provádění iterací v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="49d16-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="49d16-157">Například tento kód je pravděpodobně zablokování:</span><span class="sxs-lookup"><span data-stu-id="49d16-157">For example, this code is likely to deadlock:</span></span>

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

<span data-ttu-id="49d16-158">V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace čekat na událost.</span><span class="sxs-lookup"><span data-stu-id="49d16-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="49d16-159">Žádná z čekajících iterací nemůže být dokončena, dokud nebude dokončena iterace nastavení události.</span><span class="sxs-lookup"><span data-stu-id="49d16-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="49d16-160">Je však možné, že čekající iterace blokují všechna vlákna, která se používají ke spuštění paralelní smyčky, než má iterace nastavení události šanci provést.</span><span class="sxs-lookup"><span data-stu-id="49d16-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="49d16-161">To má za následek zablokování – iterace nastavení událostí se nikdy nespustí a čekající iterace se nikdy neprobudí.</span><span class="sxs-lookup"><span data-stu-id="49d16-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="49d16-162">Zejména jedna iterace paralelní smyčky by nikdy neměla čekat na jinou iteraci smyčky, aby se pokročilo.</span><span class="sxs-lookup"><span data-stu-id="49d16-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="49d16-163">Pokud paralelní smyčka rozhodne naplánovat iterací postupně, ale v opačném pořadí, dojde k zablokování.</span><span class="sxs-lookup"><span data-stu-id="49d16-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="49d16-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="49d16-164">See also</span></span>

- [<span data-ttu-id="49d16-165">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="49d16-165">Parallel LINQ (PLINQ)</span></span>](parallel-linq-plinq.md)
