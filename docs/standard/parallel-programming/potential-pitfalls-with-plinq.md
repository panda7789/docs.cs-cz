---
title: Potenciální nástrahy PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e44fd3e6f806eef3805416dafd90a4855e79b3c7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638831"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="05409-102">Potenciální nástrahy PLINQ</span><span class="sxs-lookup"><span data-stu-id="05409-102">Potential Pitfalls with PLINQ</span></span>
<span data-ttu-id="05409-103">V mnoha případech se může poskytnout PLINQ výrazné zlepšení výkonu přes sekvenčních LINQ to Objects dotazů.</span><span class="sxs-lookup"><span data-stu-id="05409-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="05409-104">Paralelní provádění provádění dotazu však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou jako běžné nebo nejsou vůbec došlo k.</span><span class="sxs-lookup"><span data-stu-id="05409-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="05409-105">Toto téma uvádí některé nedoporučované postupy při psaní dotazy PLINQ.</span><span class="sxs-lookup"><span data-stu-id="05409-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="05409-106">Nepředpokládejte, že paralelní je vždy rychlejší</span><span class="sxs-lookup"><span data-stu-id="05409-106">Do Not Assume That Parallel Is Always Faster</span></span>  
 <span data-ttu-id="05409-107">Někdy paralelizace způsobí, že PLINQ dotaz poběží pomaleji než jeho LINQ na ekvivalentní objekty.</span><span class="sxs-lookup"><span data-stu-id="05409-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="05409-108">Základním pravidlem je, že jsou dotazy, které mají několik zdrojové elementy a rychlé uživatelské delegáty velmi nepravděpodobné, že by zrychlení.</span><span class="sxs-lookup"><span data-stu-id="05409-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="05409-109">Ale vzhledem k tomu výkon ovlivňuje mnoho faktorů, doporučujeme měření skutečné výsledky, než se rozhodnete, jestli se má použít PLINQ.</span><span class="sxs-lookup"><span data-stu-id="05409-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="05409-110">Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="05409-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="05409-111">Vyhněte se zápis do umístění sdílené paměti</span><span class="sxs-lookup"><span data-stu-id="05409-111">Avoid Writing to Shared Memory Locations</span></span>  
 <span data-ttu-id="05409-112">V sekvenčním kódu není nic neobvyklého, čtení nebo zápis do statické proměnné nebo pole třídy.</span><span class="sxs-lookup"><span data-stu-id="05409-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="05409-113">Pokaždé, když přistupuje více podprocesů tyto proměnné souběžně, existuje však velké objemy potenciální konflikty časování.</span><span class="sxs-lookup"><span data-stu-id="05409-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="05409-114">I když zámky můžete použít k synchronizaci přístupu k proměnné, náklady na synchronizaci může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="05409-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="05409-115">Proto doporučujeme vám vyhnout, nebo aspoň omezit přístup ke sdílenému stavu v dotazu PLINQ co největší míře.</span><span class="sxs-lookup"><span data-stu-id="05409-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>  
  
## <a name="avoid-over-parallelization"></a><span data-ttu-id="05409-116">Vyhněte se nadbytečnému</span><span class="sxs-lookup"><span data-stu-id="05409-116">Avoid Over-Parallelization</span></span>  
 <span data-ttu-id="05409-117">S použitím `AsParallel` operátoru, se vám účtovat režijní náklady na vytváření oddílů zdrojové kolekce a synchronizace pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="05409-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="05409-118">Výhody paralelizace jsou dále omezeny počtem procesorů v počítači.</span><span class="sxs-lookup"><span data-stu-id="05409-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="05409-119">Neexistuje žádné zrychlení k získané spuštěním více vláken výpočetní na právě jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="05409-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="05409-120">Proto musí být pozor, abyste nadbytečně dotazu.</span><span class="sxs-lookup"><span data-stu-id="05409-120">Therefore, you must be careful not to over-parallelize a query.</span></span>  
  
 <span data-ttu-id="05409-121">Nejběžnější scénář, ve které nadbytečnému může dojít, je ve vnořené dotazy, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="05409-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 <span data-ttu-id="05409-122">V takovém případě je nejlepší paralelizovat pouze na vnější zdroj dat (zákazníci), pokud jedna nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="05409-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>  
  
-   <span data-ttu-id="05409-123">Zdroj dat vnitřní (zákazníka. Objednávky) je známo, že trvat velmi dlouho.</span><span class="sxs-lookup"><span data-stu-id="05409-123">The inner data source (cust.Orders) is known to be very long.</span></span>  
  
-   <span data-ttu-id="05409-124">Provádíte náročné výpočty na jednotlivé objednávky.</span><span class="sxs-lookup"><span data-stu-id="05409-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="05409-125">(Operace je znázorněno v příkladu není nákladné.)</span><span class="sxs-lookup"><span data-stu-id="05409-125">(The operation shown in the example is not expensive.)</span></span>  
  
-   <span data-ttu-id="05409-126">Cílový systém jsou známy dostatek procesorů pro zpracování počet vláken, které budou vytvořeny paralelní provádění dotazu na `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="05409-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>  
  
 <span data-ttu-id="05409-127">Ve všech případech je nejlepší způsob, jak určit optimální tvar dotazu pro testování a měření.</span><span class="sxs-lookup"><span data-stu-id="05409-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="05409-128">Další informace najdete v tématu [postupy: měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="05409-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="05409-129">Vyhněte se volání metody není bezpečné pro vlákna</span><span class="sxs-lookup"><span data-stu-id="05409-129">Avoid Calls to Non-Thread-Safe Methods</span></span>  
 <span data-ttu-id="05409-130">Zápis do metody instance vláknově bezpečné PLINQ dotazu může vést k poškození dat, který může nebo nemusí pokračovat nezjištěné po ve svém programu.</span><span class="sxs-lookup"><span data-stu-id="05409-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="05409-131">Může také vést k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="05409-131">It can also lead to exceptions.</span></span> <span data-ttu-id="05409-132">V následujícím příkladu by se pokoušet více vláken k volání `Filestream.Write` metoda současně, což není podporována třídou.</span><span class="sxs-lookup"><span data-stu-id="05409-132">In the following example, multiple threads would be attempting to call the `Filestream.Write` method simultaneously, which is not supported by the class.</span></span>  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="05409-133">Omezení volání metod bezpečným pro vlákno</span><span class="sxs-lookup"><span data-stu-id="05409-133">Limit Calls to Thread-Safe Methods</span></span>  
 <span data-ttu-id="05409-134">Většina statických metod v rozhraní .NET Framework jsou bezpečné pro vlákna a může být volána z více vláken současně.</span><span class="sxs-lookup"><span data-stu-id="05409-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="05409-135">I v těchto případech se však zapojení synchronizace může vést k výrazné mohou zpomalit zpracování dotazu.</span><span class="sxs-lookup"><span data-stu-id="05409-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05409-136">Můžete vyzkoušet to sami vložením volání některých <xref:System.Console.WriteLine%2A> v dotazech.</span><span class="sxs-lookup"><span data-stu-id="05409-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="05409-137">I když tato metoda se používá v příkladech dokumentaci pro demonstrační účely, nepoužívejte ji v PLINQ dotazy.</span><span class="sxs-lookup"><span data-stu-id="05409-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>  
  
## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="05409-138">Vyhněte se zbytečným operace řazení</span><span class="sxs-lookup"><span data-stu-id="05409-138">Avoid Unnecessary Ordering Operations</span></span>  
 <span data-ttu-id="05409-139">Při PLINQ dotaz spuštěn paralelně, rozdělí zdrojovou sekvenci na oddíly, které mohou být provozována současně z více vláken.</span><span class="sxs-lookup"><span data-stu-id="05409-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="05409-140">Ve výchozím nastavení, není předvídatelný pořadí, ve které se zpracovávají oddíly a jsou doručeny výsledky (s výjimkou operátory, jako například `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="05409-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="05409-141">Můžete určit, aby PLINQ zachovávaní řazení jakékoli zdrojové sekvence, ale tato akce nemá negativní dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="05409-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="05409-142">Osvědčeným postupem, kdykoli je to možné, je struktura dotazy tak, aby jejich nespoléhejte na zachování pořadí.</span><span class="sxs-lookup"><span data-stu-id="05409-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="05409-143">Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="05409-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="05409-144">V případě ForEach je možné raději ForAll</span><span class="sxs-lookup"><span data-stu-id="05409-144">Prefer ForAll to ForEach When It Is Possible</span></span>  
 <span data-ttu-id="05409-145">I když PLINQ provede dotaz z více vláken, je-li využívají výsledky v `foreach` smyčky (`For Each` v jazyce Visual Basic), pak výsledky dotazu musí být sloučeny zpět do jednoho vlákna a sériově přistupuje enumerátor.</span><span class="sxs-lookup"><span data-stu-id="05409-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="05409-146">V některých případech je to nevyhnutelné; však kdykoli je to možné, použijte `ForAll` metoda umožňuje každému vláknu vlastní výsledky, například výstup například zapsáním do kolekce bezpečné pro vlákna <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05409-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="05409-147">Stejný problém se vztahuje na <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jinými slovy, `source.AsParallel().Where().ForAll(...)` by měl být důrazně upřednostňován do</span><span class="sxs-lookup"><span data-stu-id="05409-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>  
  
 <span data-ttu-id="05409-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="05409-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>  
  
## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="05409-149">Mějte na paměti problémů, spřažení vláken</span><span class="sxs-lookup"><span data-stu-id="05409-149">Be Aware of Thread Affinity Issues</span></span>  
 <span data-ttu-id="05409-150">Některé technologie, například interoperabilita modelů COM pro jedno vláknové objekty Apartment (STA) součásti Windows Forms a Windows Presentation Foundation (WPF), omezení vlákno vztahů, které vyžadují spuštění kódu na konkrétním vlákně.</span><span class="sxs-lookup"><span data-stu-id="05409-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="05409-151">Například ve Windows Forms a WPF, ovládací prvek je přístupný pouze na vlákně, na kterém byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="05409-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="05409-152">Při pokusu o přístup ke sdílenému stavu ovládacího prvku Windows Forms v PLINQ dotaz, je vyvolána výjimka, pokud používáte v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="05409-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="05409-153">(Toto nastavení vypnete.) Ale pokud váš dotaz využívá ve vlákně uživatelského rozhraní, pak dostanete ovládacího prvku z `foreach` smyčku, která se zobrazí dotaz výsledky vzhledem k tomu, že kód je prováděn pouze jedno vlákno.</span><span class="sxs-lookup"><span data-stu-id="05409-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="05409-154">Nepředpokládejte, že iterace ForEach, pro a ForAll vždy spustit paralelně</span><span class="sxs-lookup"><span data-stu-id="05409-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>  
 <span data-ttu-id="05409-155">Je důležité mít na paměti, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčky může, ale není nutné spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="05409-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="05409-156">Proto byste se měli vyhnout psaní kódu, který správnost závisí na paralelní zpracování iterace nebo spuštění iterace v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="05409-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>  
  
 <span data-ttu-id="05409-157">Například tento kód je pravděpodobně dojde k zablokování:</span><span class="sxs-lookup"><span data-stu-id="05409-157">For example, this code is likely to deadlock:</span></span>  
  
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
  
 <span data-ttu-id="05409-158">V tomto příkladu jednu iteraci nastaví událost a všech dalších iterací čekání na událost.</span><span class="sxs-lookup"><span data-stu-id="05409-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="05409-159">Žádné čekající iterace můžete dokončit až do dokončení iterace nastavení události.</span><span class="sxs-lookup"><span data-stu-id="05409-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="05409-160">Je však možné, že čekajících iterací blokovat všechna vlákna, které se používají ke spouštění paralelní smyčky před událostí iterace dostala příležitost k provedení.</span><span class="sxs-lookup"><span data-stu-id="05409-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="05409-161">Výsledkem zablokování – událost iterace se nikdy neprovede a iterace čekání se nikdy probuzení.</span><span class="sxs-lookup"><span data-stu-id="05409-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>  
  
 <span data-ttu-id="05409-162">Zejména jedné iterace paralelní smyčky by nikdy čekat na další iteraci smyčky pokroku.</span><span class="sxs-lookup"><span data-stu-id="05409-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="05409-163">Pokud se rozhodne paralelní smyčky naplánování iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.</span><span class="sxs-lookup"><span data-stu-id="05409-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05409-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05409-164">See also</span></span>

- [<span data-ttu-id="05409-165">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="05409-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
