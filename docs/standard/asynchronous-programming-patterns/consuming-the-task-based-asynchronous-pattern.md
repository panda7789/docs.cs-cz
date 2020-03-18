---
title: Použití asynchronního vzoru založeného na úloze
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139811"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="c24d1-102">Použití asynchronního vzoru založeného na úloze</span><span class="sxs-lookup"><span data-stu-id="c24d1-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="c24d1-103">Při použití task-based asynchronní vzor (TAP) pro práci s asynchronní operace, můžete použít zpětná volání k dosažení čekání bez blokování.</span><span class="sxs-lookup"><span data-stu-id="c24d1-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="c24d1-104">U úkolů je toho dosaženo <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>prostřednictvím metod, jako je například .</span><span class="sxs-lookup"><span data-stu-id="c24d1-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c24d1-105">Jazyková asynchronní podpora skryje zpětná volání tím, že umožňuje asynchronní operace, které mají být očekávány v rámci normálního toku řízení a kód generovaný kompilátorem poskytuje stejnou podporu na úrovni rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c24d1-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="c24d1-106">Pozastavení provádění s Čeká</span><span class="sxs-lookup"><span data-stu-id="c24d1-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="c24d1-107">Počínaje rozhraním .NET Framework 4.5 můžete použít klíčové slovo [await](../../csharp/language-reference/operators/await.md) v jazyce C# a operátor <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> [Await](../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic asynchronně await a objekty.</span><span class="sxs-lookup"><span data-stu-id="c24d1-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="c24d1-108">Pokud čekáte <xref:System.Threading.Tasks.Task>na , `await` výraz je `void`typu .</span><span class="sxs-lookup"><span data-stu-id="c24d1-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="c24d1-109">Pokud čekáte <xref:System.Threading.Tasks.Task%601>na , `await` výraz je `TResult`typu .</span><span class="sxs-lookup"><span data-stu-id="c24d1-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="c24d1-110">Výraz `await` musí dojít uvnitř těla asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="c24d1-111">Další informace o podpoře jazyka C# a visual basicv rozhraní .NET Framework 4.5 naleznete specifikace jazyka C# a visual basic.</span><span class="sxs-lookup"><span data-stu-id="c24d1-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="c24d1-112">Pod kryty await funkce nainstaluje zpětné volání na úlohu pomocí pokračování.</span><span class="sxs-lookup"><span data-stu-id="c24d1-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="c24d1-113">Toto zpětné volání obnoví asynchronní metodu v okamžiku pozastavení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="c24d1-114">Po obnovení asynchronní metody, pokud byla očekávaná operace úspěšně <xref:System.Threading.Tasks.Task%601>dokončena `TResult` a byla , je vrácena její.</span><span class="sxs-lookup"><span data-stu-id="c24d1-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="c24d1-115">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> které bylo očekáváno <xref:System.Threading.Tasks.TaskStatus.Canceled> skončil <xref:System.OperationCanceledException> ve stavu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c24d1-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="c24d1-116">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> které bylo očekáváno <xref:System.Threading.Tasks.TaskStatus.Faulted> skončil ve stavu, je vyvolána výjimka, která způsobila jeho chybu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="c24d1-117">Může `Task` chyba v důsledku více výjimek, ale pouze jedna z těchto výjimek je rozšířena.</span><span class="sxs-lookup"><span data-stu-id="c24d1-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="c24d1-118">Vlastnost však <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vrátí <xref:System.AggregateException> výjimku, která obsahuje všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="c24d1-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="c24d1-119">Pokud kontext synchronizace<xref:System.Threading.SynchronizationContext> ( objekt) je přidružen k podprocesu, který byl provádění asynchronní metody <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> v `null`době pozastavení (například pokud vlastnost není ), asynchronní metoda <xref:System.Threading.SynchronizationContext.Post%2A> pokračuje ve stejném kontextu synchronizace pomocí metody kontextu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="c24d1-120">V opačném případě se spoléhá na<xref:System.Threading.Tasks.TaskScheduler> plánovač úloh ( objekt), který byl aktuální v době pozastavení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="c24d1-121">Obvykle se jedná o výchozí plánovač<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>úloh ( ), který cílí na fond vláken.</span><span class="sxs-lookup"><span data-stu-id="c24d1-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="c24d1-122">Tento plánovač úloh určuje, zda by očekávaná asynchronní operace měla pokračovat tam, kde byla dokončena, nebo zda má být naplánována obnova.</span><span class="sxs-lookup"><span data-stu-id="c24d1-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="c24d1-123">Výchozí plánovač obvykle umožňuje pokračování spustit ve vlákně, které byla dokončena očekávaná operace.</span><span class="sxs-lookup"><span data-stu-id="c24d1-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="c24d1-124">Při volání asynchronní metoda synchronně provede tělo funkce až do první await výraz na čekat nouzi, která ještě nebyla dokončena, na kterém místě vyvolání vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="c24d1-125">Pokud asynchronní metoda nevrátí `void`, <xref:System.Threading.Tasks.Task> je <xref:System.Threading.Tasks.Task%601> vrácen a nebo objekt představující probíhající výpočtu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="c24d1-126">V nevoid asynchronní metody, pokud je zjištěn příkaz return nebo je dosaženo konce těla metody, úkol je dokončen v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečném stavu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="c24d1-127">Pokud neošetřená výjimka způsobí, že ovládací prvek opustit tělo asynchronní metody, úloha končí ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="c24d1-128">Pokud je tato <xref:System.OperationCanceledException>výjimka , úloha místo toho končí ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="c24d1-129">Tímto způsobem je nakonec publikován výsledek nebo výjimka.</span><span class="sxs-lookup"><span data-stu-id="c24d1-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="c24d1-130">Existuje několik důležitých variant tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="c24d1-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="c24d1-131">Z důvodů výkonu, pokud úkol již dokončena v době, kdy je úkol očekáván, ovládací prvek není výnosný a funkce pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="c24d1-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="c24d1-132">Kromě toho návrat do původního kontextu není vždy požadované chování a lze změnit; to je podrobněji popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="c24d1-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="c24d1-133">Konfigurace pozastavení a obnovení s yield a configureAwait</span><span class="sxs-lookup"><span data-stu-id="c24d1-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="c24d1-134">Několik metod poskytují větší kontrolu nad provádění asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="c24d1-135">Metodu <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> můžete například použít k zavedení bodu výnosu do asynchronní metody:</span><span class="sxs-lookup"><span data-stu-id="c24d1-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="c24d1-136">To je ekvivalentní asynchronně zaúčtování nebo plánování zpět do aktuálního kontextu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="c24d1-137">Můžete také použít <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a obnovení v asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="c24d1-138">Jak již bylo zmíněno dříve, ve výchozím nastavení aktuální kontext je zachycen v době pozastavení asynchronní metody a zachycené kontextu se používá k vyvolání pokračování asynchronní metody při obnovení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="c24d1-139">V mnoha případech je to přesně požadované chování.</span><span class="sxs-lookup"><span data-stu-id="c24d1-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="c24d1-140">V ostatních případech se nemusí starat o kontext pokračování a můžete dosáhnout lepšího výkonu tím, že se těmto příspěvkům vrátíte do původního kontextu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="c24d1-141">Chcete-li to <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> povolit, použijte metodu k informování operace await, která nemá zachytit a pokračovat v kontextu, ale pokračovat v provádění všude tam, kde byla dokončena asynchronní operace, která byla právě očekávána:</span><span class="sxs-lookup"><span data-stu-id="c24d1-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="c24d1-142">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="c24d1-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="c24d1-143">Počínaje rozhraním .NET Framework 4, metody TAP, které podporují zrušení poskytují<xref:System.Threading.CancellationToken> alespoň jedno přetížení, které přijímá token zrušení (objekt).</span><span class="sxs-lookup"><span data-stu-id="c24d1-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="c24d1-144">Token zrušení je vytvořen prostřednictvím<xref:System.Threading.CancellationTokenSource> zdroje tokenu zrušení (objektu).</span><span class="sxs-lookup"><span data-stu-id="c24d1-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="c24d1-145"><xref:System.Threading.CancellationTokenSource.Token%2A> Vlastnost zdroje vrátí token zrušení, který bude signalizován při <xref:System.Threading.CancellationTokenSource.Cancel%2A> volání metody zdroje.</span><span class="sxs-lookup"><span data-stu-id="c24d1-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="c24d1-146">Chcete-li například stáhnout jednu webovou stránku a chcete mít možnost <xref:System.Threading.CancellationTokenSource> operaci zrušit, vytvořte objekt, předajte jeho <xref:System.Threading.CancellationTokenSource.Cancel%2A> token metodě TAP a poté zavoláte metodu zdroje, až budete připraveni operaci zrušit:</span><span class="sxs-lookup"><span data-stu-id="c24d1-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="c24d1-147">Chcete-li zrušit více asynchronních vyvolání, můžete předat stejný token všem vyvoláním:</span><span class="sxs-lookup"><span data-stu-id="c24d1-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="c24d1-148">Nebo můžete předat stejný token selektivní podmnožině operací:</span><span class="sxs-lookup"><span data-stu-id="c24d1-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="c24d1-149">Žádosti o zrušení mohou být iniciovány z libovolného vlákna.</span><span class="sxs-lookup"><span data-stu-id="c24d1-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="c24d1-150">Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu libovolnou metodu, která přijímá token zrušení označující, že zrušení nikdy nebude požadováno.</span><span class="sxs-lookup"><span data-stu-id="c24d1-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="c24d1-151">To způsobí, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> že `false`vlastnost vrátit a volaná metoda můžete optimalizovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c24d1-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="c24d1-152">Pro účely testování můžete také předat předzrušený token zrušení, který je vytvořen pomocí konstruktoru, který přijímá logickou hodnotu k označení, zda by měl token spustit v již zrušeném nebo nezrušitelném stavu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="c24d1-153">Tento přístup ke zrušení má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="c24d1-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="c24d1-154">Můžete předat stejný token zrušení libovolný počet asynchronních a synchronních operací.</span><span class="sxs-lookup"><span data-stu-id="c24d1-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="c24d1-155">Stejný požadavek na zrušení může být množí libovolný počet posluchačů.</span><span class="sxs-lookup"><span data-stu-id="c24d1-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="c24d1-156">Vývojář asynchronní rozhraní API má úplnou kontrolu nad tím, zda může být požadováno zrušení a kdy se může projevit.</span><span class="sxs-lookup"><span data-stu-id="c24d1-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="c24d1-157">Kód, který spotřebovává rozhraní API může selektivně určit asynchronní vyvolání, které budou rozšířeny požadavky na zrušení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="c24d1-158">Sledování průběhu</span><span class="sxs-lookup"><span data-stu-id="c24d1-158">Monitoring Progress</span></span>
 <span data-ttu-id="c24d1-159">Některé asynchronní metody zveřejňují průběh prostřednictvím rozhraní průběhu předaných do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="c24d1-160">Zvažte například funkci, která asynchronně stáhne řetězec textu a cestou vyvolá aktualizace průběhu, které zahrnují procento stahování, které bylo dosud dokončeno.</span><span class="sxs-lookup"><span data-stu-id="c24d1-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="c24d1-161">Tato metoda by mohla být spotřebována v aplikaci WPF (Windows Presentation Foundation) takto:</span><span class="sxs-lookup"><span data-stu-id="c24d1-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="c24d1-162">Použití integrovaných kombinátorů založených na úlohách</span><span class="sxs-lookup"><span data-stu-id="c24d1-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="c24d1-163">Obor <xref:System.Threading.Tasks> názvů obsahuje několik metod pro skládání a práci s úkoly.</span><span class="sxs-lookup"><span data-stu-id="c24d1-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="c24d1-164">Úloha.Spustit</span><span class="sxs-lookup"><span data-stu-id="c24d1-164">Task.Run</span></span>
 <span data-ttu-id="c24d1-165">Třída <xref:System.Threading.Tasks.Task> obsahuje <xref:System.Threading.Tasks.Task.Run%2A> několik metod, které umožňují snadno <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> offload práce jako nebo do fondu vláken, například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="c24d1-166">Některé z <xref:System.Threading.Tasks.Task.Run%2A> těchto metod, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> jako je například <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> přetížení, existují jako zkratka pro metodu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="c24d1-167">Další přetížení, například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, umožňují použít await v rámci vyložené práce, například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="c24d1-168">Taková přetížení jsou logicky ekvivalentní <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> použití metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> ve spojení s metodou rozšíření v paralelní knihovně úloh.</span><span class="sxs-lookup"><span data-stu-id="c24d1-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="c24d1-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="c24d1-169">Task.FromResult</span></span>
 <span data-ttu-id="c24d1-170">Metodu <xref:System.Threading.Tasks.Task.FromResult%2A> použijte ve scénářích, kde data již mohou být k dispozici a je <xref:System.Threading.Tasks.Task%601>třeba je vrátit z metody vrácení úlohy, která byla zrušena do :</span><span class="sxs-lookup"><span data-stu-id="c24d1-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="c24d1-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="c24d1-171">Task.WhenAll</span></span>
 <span data-ttu-id="c24d1-172">Pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronně čekat na více asynchronních operací, které jsou reprezentovány jako úkoly.</span><span class="sxs-lookup"><span data-stu-id="c24d1-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="c24d1-173">Metoda má více přetížení, které podporují sadu neobecných úloh nebo nejednotné sady obecných úloh (například asynchronně čekání na více operací vrácení prázdnoty nebo asynchronně čekání na více metod vrácení hodnoty, kde každá hodnota může mít jiný `TResult`typ) a podporovat jednotnou sadu obecných úloh (například asynchronně čekání na více metod vrácení).</span><span class="sxs-lookup"><span data-stu-id="c24d1-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="c24d1-174">Řekněme, že chcete posílat e-mailové zprávy několika zákazníkům.</span><span class="sxs-lookup"><span data-stu-id="c24d1-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="c24d1-175">Odesílání zpráv můžete překrývat, takže před odesláním další zprávy nečekáte na dokončení jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="c24d1-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="c24d1-176">Můžete také zjistit, kdy byly operace odesílání dokončeny a zda došlo k chybám:</span><span class="sxs-lookup"><span data-stu-id="c24d1-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="c24d1-177">Tento kód explicitně nezpracovává výjimky, které mohou nastat, ale `await` umožňuje výjimky šířit <xref:System.Threading.Tasks.Task.WhenAll%2A>z na výsledné úlohy z .</span><span class="sxs-lookup"><span data-stu-id="c24d1-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="c24d1-178">Chcete-li zpracovat výjimky, můžete použít kód, jako je například následující:</span><span class="sxs-lookup"><span data-stu-id="c24d1-178">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="c24d1-179">V tomto případě pokud se nezdaří všechny asynchronní operace, všechny <xref:System.AggregateException> výjimky budou konsolidovány ve výjimce, která je uložena <xref:System.Threading.Tasks.Task> v tom, který je vrácen z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="c24d1-180">Klíčové `await` slovo je však šířena pouze jednou z těchto výjimek.</span><span class="sxs-lookup"><span data-stu-id="c24d1-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="c24d1-181">Pokud chcete prozkoumat všechny výjimky, můžete přepsat předchozí kód takto:</span><span class="sxs-lookup"><span data-stu-id="c24d1-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="c24d1-182">Podívejme se na příklad stahování více souborů z webu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c24d1-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="c24d1-183">V tomto případě všechny asynchronní operace mají homogenní typy výsledků a je snadný přístup k výsledkům:</span><span class="sxs-lookup"><span data-stu-id="c24d1-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="c24d1-184">Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vrácení prázdnoty:</span><span class="sxs-lookup"><span data-stu-id="c24d1-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="c24d1-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="c24d1-185">Task.WhenAny</span></span>
 <span data-ttu-id="c24d1-186">Metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete použít k asynchronnímu čekání pouze na jednu z více asynchronních operací reprezentované jako úkoly k dokončení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="c24d1-187">Tato metoda slouží čtyři případy primární použití:</span><span class="sxs-lookup"><span data-stu-id="c24d1-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="c24d1-188">Redundance: Provedení operace vícekrát a výběr té, která dokončí první (například kontaktování více webových služeb nabídky akcií, které vytvoří jeden výsledek a vybere ten, který dokončí nejrychlejší).</span><span class="sxs-lookup"><span data-stu-id="c24d1-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="c24d1-189">Prokládání: Spuštění více operací a čekání na dokončení všech, ale jejich zpracování po dokončení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="c24d1-190">Omezení: Povolení dalších operací začít jako ostatní dokončení.</span><span class="sxs-lookup"><span data-stu-id="c24d1-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="c24d1-191">Toto je rozšíření prokládání scénář.</span><span class="sxs-lookup"><span data-stu-id="c24d1-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="c24d1-192">Včasná výpomoc: Například operace reprezentovaná úkolem t1 může být seskupena do úkolu s jiným úkolem <xref:System.Threading.Tasks.Task.WhenAny%2A> t2 a můžete na <xref:System.Threading.Tasks.Task.WhenAny%2A> úkol počkat.</span><span class="sxs-lookup"><span data-stu-id="c24d1-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="c24d1-193">Úloha t2 může představovat časový čas nebo zrušení nebo <xref:System.Threading.Tasks.Task.WhenAny%2A> jiný signál, který způsobí dokončení úkolu před dokončením t1.</span><span class="sxs-lookup"><span data-stu-id="c24d1-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="c24d1-194">Redundance</span><span class="sxs-lookup"><span data-stu-id="c24d1-194">Redundancy</span></span>
 <span data-ttu-id="c24d1-195">Vezměme si případ, kdy chcete učinit rozhodnutí o tom, zda koupit akcie.</span><span class="sxs-lookup"><span data-stu-id="c24d1-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="c24d1-196">Existuje několik webových služeb doporučení akcií, kterým důvěřujete, ale v závislosti na každodenním zatížení může každá služba skončit v různých časech pomalá.</span><span class="sxs-lookup"><span data-stu-id="c24d1-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="c24d1-197">Tuto metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete použít k přijetí oznámení po dokončení jakékoli operace:</span><span class="sxs-lookup"><span data-stu-id="c24d1-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="c24d1-198">Na <xref:System.Threading.Tasks.Task.WhenAll%2A>rozdíl od , který vrátí nezabalené výsledky <xref:System.Threading.Tasks.Task.WhenAny%2A> všech úkolů, které byly úspěšně dokončeny, vrátí úkol, který byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="c24d1-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="c24d1-199">Pokud se úkol nezdaří, je důležité vědět, že se nezdařilo, a pokud je úkol úspěšný, je důležité vědět, ke kterému úkolu je vrácená hodnota přidružena.</span><span class="sxs-lookup"><span data-stu-id="c24d1-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="c24d1-200">Proto je třeba získat přístup k výsledku vrácené úlohy nebo dále čekat, jak ukazuje tento příklad.</span><span class="sxs-lookup"><span data-stu-id="c24d1-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="c24d1-201">Stejně <xref:System.Threading.Tasks.Task.WhenAll%2A>jako u , musíte být schopni vyhovět výjimkám.</span><span class="sxs-lookup"><span data-stu-id="c24d1-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="c24d1-202">Vzhledem k tomu, že obdržíte dokončený úkol zpět, můžete čekat `try/catch` vrácené úlohy mít chyby šířené a je odpovídajícím způsobem; například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="c24d1-203">Navíc i v případě, že první úkol úspěšně dokončí, následné úkoly může selhat.</span><span class="sxs-lookup"><span data-stu-id="c24d1-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="c24d1-204">V tomto okamžiku máte několik možností pro řešení výjimek: Můžete počkat, dokud nebudou dokončeny <xref:System.Threading.Tasks.Task.WhenAll%2A> všechny spuštěné úkoly, v takovém případě můžete použít metodu, nebo se můžete rozhodnout, že všechny výjimky jsou důležité a musí být zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="c24d1-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="c24d1-205">Za tímto účelem můžete použít pokračování přijímat oznámení po dokončení úlohami asynchronně:</span><span class="sxs-lookup"><span data-stu-id="c24d1-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="c24d1-206">nebo:</span><span class="sxs-lookup"><span data-stu-id="c24d1-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="c24d1-207">nebo dokonce:</span><span class="sxs-lookup"><span data-stu-id="c24d1-207">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="c24d1-208">Nakonec můžete chtít zrušit všechny zbývající operace:</span><span class="sxs-lookup"><span data-stu-id="c24d1-208">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="c24d1-209">Prokládání</span><span class="sxs-lookup"><span data-stu-id="c24d1-209">Interleaving</span></span>
 <span data-ttu-id="c24d1-210">Zvažte případ, kdy stahujete obrázky z webu a zpracováváte jednotlivé obrázky (například přidání obrázku do ovládacího prvku uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="c24d1-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="c24d1-211">Je třeba provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout obrázky co nejaktuálněji.</span><span class="sxs-lookup"><span data-stu-id="c24d1-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="c24d1-212">Také nechcete zdržovat přidávání obrázků do hlavního nastavení, dokud nejsou všechny stažené – chcete je přidat po dokončení:</span><span class="sxs-lookup"><span data-stu-id="c24d1-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="c24d1-213">Můžete také použít prokládání na scénář, který zahrnuje <xref:System.Threading.ThreadPool> výpočtově náročné zpracování na stažené obrázky; například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="c24d1-214">Throttling</span><span class="sxs-lookup"><span data-stu-id="c24d1-214">Throttling</span></span>
 <span data-ttu-id="c24d1-215">Vezměme si příklad prokládání, s tím rozdílem, že uživatel stahuje tolik obrázků, že stahování musí být omezen; například chcete, aby současně došlo pouze k určitému počtu stahování.</span><span class="sxs-lookup"><span data-stu-id="c24d1-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="c24d1-216">Chcete-li toho dosáhnout, můžete spustit podmnožinu asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="c24d1-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="c24d1-217">Po dokončení operací můžete zahájit další operace, které zaujmou jejich místo:</span><span class="sxs-lookup"><span data-stu-id="c24d1-217">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="c24d1-218">Včasná výpomoc</span><span class="sxs-lookup"><span data-stu-id="c24d1-218">Early Bailout</span></span>
 <span data-ttu-id="c24d1-219">Vezměte v úvahu, že asynchronně čekáte na dokončení operace a současně reagujete na požadavek na zrušení uživatele (například uživatel klepnul na tlačítko storno).</span><span class="sxs-lookup"><span data-stu-id="c24d1-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="c24d1-220">Následující kód ilustruje tento scénář:</span><span class="sxs-lookup"><span data-stu-id="c24d1-220">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="c24d1-221">Tato implementace znovu povolí uživatelské rozhraní, jakmile se rozhodnete provést vyřazení, ale nezruší základní asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c24d1-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="c24d1-222">Další alternativou by bylo zrušit čekající operace, když se rozhodnete provést kauci, ale neobnovit uživatelské rozhraní, dokud operace skutečně dokončeny, potenciálně z důvodu předčasného ukončení z důvodu žádosti o zrušení:</span><span class="sxs-lookup"><span data-stu-id="c24d1-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="c24d1-223">Dalším příkladem včasné horečné pomoci zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metody ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> metodou, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="c24d1-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="c24d1-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="c24d1-224">Task.Delay</span></span>
 <span data-ttu-id="c24d1-225">Metodu <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> můžete použít k zavedení pozastavení do spuštění asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c24d1-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="c24d1-226">To je užitečné pro mnoho druhů funkcí, včetně vytváření smyčk dotazování a zpoždění zpracování vstupu uživatele pro předem určené časové období.</span><span class="sxs-lookup"><span data-stu-id="c24d1-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="c24d1-227">Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> může být také užitečné <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci s pro implementaci časové odnože na čeká.</span><span class="sxs-lookup"><span data-stu-id="c24d1-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="c24d1-228">Pokud úkol, který je součástí větší asynchronní operace (například ASP.NET webové služby) trvá příliš dlouho na dokončení, celková operace může utrpět, zejména v případě, že se nezdaří někdy dokončit.</span><span class="sxs-lookup"><span data-stu-id="c24d1-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="c24d1-229">Z tohoto důvodu je důležité mít možnost časový režim při čekání na asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c24d1-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="c24d1-230"><xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Synchronní , <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnoty časového času, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ale odpovídající <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedené metody nikoli.</span><span class="sxs-lookup"><span data-stu-id="c24d1-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="c24d1-231">Místo toho můžete <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> použít a v kombinaci k implementaci časového odčasového času.</span><span class="sxs-lookup"><span data-stu-id="c24d1-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="c24d1-232">Například v aplikaci ui řekněme, že chcete stáhnout obrázek a zakázat ui při stahování obrázku.</span><span class="sxs-lookup"><span data-stu-id="c24d1-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="c24d1-233">Pokud však stahování trvá příliš dlouho, chcete znovu povolit ui a zahodit stahování:</span><span class="sxs-lookup"><span data-stu-id="c24d1-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="c24d1-234">Totéž platí pro více stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úkol:</span><span class="sxs-lookup"><span data-stu-id="c24d1-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="c24d1-235">Vytváření kombinátorů založených na úlohách</span><span class="sxs-lookup"><span data-stu-id="c24d1-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="c24d1-236">Vzhledem k tomu, že úloha je schopna zcela reprezentovat asynchronní operaci a poskytovat synchronní a asynchronní funkce pro připojení k operaci, načítání jejích výsledků a tak dále, můžete vytvořit užitečné knihovny kombinátorů, které vytvářejí úkoly vytvářet větší vzory.</span><span class="sxs-lookup"><span data-stu-id="c24d1-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="c24d1-237">Jak je popsáno v předchozí části rozhraní .NET Framework obsahuje několik předdefinovaných kombinátorů, ale můžete také vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="c24d1-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="c24d1-238">Následující části obsahují několik příkladů možných metod a typů kombinátoru.</span><span class="sxs-lookup"><span data-stu-id="c24d1-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="c24d1-239">Opakováníon-fault</span><span class="sxs-lookup"><span data-stu-id="c24d1-239">RetryOnFault</span></span>
 <span data-ttu-id="c24d1-240">V mnoha situacích můžete chtít opakovat operaci, pokud předchozí pokus selže.</span><span class="sxs-lookup"><span data-stu-id="c24d1-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="c24d1-241">Pro synchronní kód můžete vytvořit pomocnou metodu, například `RetryOnFault` v následujícím příkladu k dosažení tohoto cíle:</span><span class="sxs-lookup"><span data-stu-id="c24d1-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="c24d1-242">Můžete vytvořit téměř identickou pomocnou metodu pro asynchronní operace, které jsou implementovány pomocí tap a tím vrátit úkoly:</span><span class="sxs-lookup"><span data-stu-id="c24d1-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="c24d1-243">Potom můžete použít tento kombinátor ke kódování opakování do logiky aplikace; například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="c24d1-244">Můžete rozšířit `RetryOnFault` funkci dále.</span><span class="sxs-lookup"><span data-stu-id="c24d1-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="c24d1-245">Funkce může například přijmout `Func<Task>` jinou, která bude vyvolána mezi opakovanými pokusy o určení, kdy chcete operaci zkusit znovu; například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="c24d1-246">Funkci pak můžete použít následujícím způsobem a počkat na chvíli před opakováním operace:</span><span class="sxs-lookup"><span data-stu-id="c24d1-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="c24d1-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="c24d1-247">NeedOnlyOne</span></span>
 <span data-ttu-id="c24d1-248">V některých proto můžete využít redundance ke zlepšení latence operace a šancí na úspěch.</span><span class="sxs-lookup"><span data-stu-id="c24d1-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="c24d1-249">Zvažte více webových služeb, které poskytují kurzy akcií, ale v různých denních dobách může každá služba poskytovat různé úrovně kvality a doby odezvy.</span><span class="sxs-lookup"><span data-stu-id="c24d1-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="c24d1-250">Chcete-li se vypořádat s těmito výkyvy, můžete vydávat žádosti na všechny webové služby, a jakmile dostanete odpověď od jednoho, zrušit zbývající požadavky.</span><span class="sxs-lookup"><span data-stu-id="c24d1-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="c24d1-251">Můžete implementovat pomocnou funkci, která usnadňuje implementaci tohoto společného vzoru spuštění více operací, čekání na všechny a následné zrušení ostatních.</span><span class="sxs-lookup"><span data-stu-id="c24d1-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="c24d1-252">Funkce `NeedOnlyOne` v následujícím příkladu ilustruje tento scénář:</span><span class="sxs-lookup"><span data-stu-id="c24d1-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="c24d1-253">Tuto funkci pak můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c24d1-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="c24d1-254">Prokládaná operace</span><span class="sxs-lookup"><span data-stu-id="c24d1-254">Interleaved Operations</span></span>
 <span data-ttu-id="c24d1-255">Při práci s velmi velkými <xref:System.Threading.Tasks.Task.WhenAny%2A> sadami úkolů je potenciální problém s výkonem pomocí metody pro podporu prokládání.</span><span class="sxs-lookup"><span data-stu-id="c24d1-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span> <span data-ttu-id="c24d1-256">Každé volání <xref:System.Threading.Tasks.Task.WhenAny%2A> má za následek pokračování je registrována u každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="c24d1-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="c24d1-257">Pro N počet úkolů, to má za následek O(N<sup>2</sup>) pokračování vytvořené po dobu životnosti operace prokládání.</span><span class="sxs-lookup"><span data-stu-id="c24d1-257">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="c24d1-258">Pokud pracujete s velkou sadou úkolů, můžete k`Interleaved` řešení problému s výkonem použít kombinátor (v následujícím příkladu):</span><span class="sxs-lookup"><span data-stu-id="c24d1-258">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="c24d1-259">Kombinátor pak můžete použít ke zpracování výsledků úkolů při jejich dokončení; například:</span><span class="sxs-lookup"><span data-stu-id="c24d1-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="c24d1-260">Když AllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="c24d1-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="c24d1-261">V některých scénářích scatter/gather můžete chtít počkat na všechny úkoly v sadě, pokud jeden z nich chyby, v takovém případě chcete přestat čekat, jakmile dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c24d1-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="c24d1-262">Můžete to provést metodou kombinátoru, například `WhenAllOrFirstException` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c24d1-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="c24d1-263">Vytváření datových struktur založených na úlohách</span><span class="sxs-lookup"><span data-stu-id="c24d1-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="c24d1-264">Kromě schopnosti vytvářet vlastní kombinátory založené na úlohách, které mají datovou strukturu a <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> která představuje výsledky asynchronní operace a nezbytné synchronizace pro připojení s ním je velmi výkonný typ, na kterém chcete vytvořit vlastní datové struktury, které mají být použity v asynchronních scénářích.</span><span class="sxs-lookup"><span data-stu-id="c24d1-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="c24d1-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="c24d1-265">AsyncCache</span></span>
 <span data-ttu-id="c24d1-266">Jedním z důležitých aspektů úkolu je, že může být rozdán více spotřebitelům, z nichž všichni mohou čekat, zaregistrovat pokračování s ním, získat jeho výsledek nebo výjimky (v případě <xref:System.Threading.Tasks.Task%601>) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c24d1-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="c24d1-267">Díky <xref:System.Threading.Tasks.Task> tomu <xref:System.Threading.Tasks.Task%601> se dokonale hodí pro použití v asynchronní infrastruktuře ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c24d1-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="c24d1-268">Zde je příklad malé, ale výkonné asynchronní mezipaměti <xref:System.Threading.Tasks.Task%601>postavené nad :</span><span class="sxs-lookup"><span data-stu-id="c24d1-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="c24d1-269">[Třída AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) přijímá jako delegáta svému konstruktoru funkci, která přebírá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c24d1-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="c24d1-270">Všechny dříve přístupné hodnoty z mezipaměti jsou uloženy `AsyncCache` ve vnitřním slovníku a zajišťuje, že je generována pouze jedna úloha na klíč, i v případě, že je ke mezipaměti přistupovat souběžně.</span><span class="sxs-lookup"><span data-stu-id="c24d1-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="c24d1-271">Můžete například vytvořit mezipaměť pro stažené webové stránky:</span><span class="sxs-lookup"><span data-stu-id="c24d1-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="c24d1-272">Tuto mezipaměť pak můžete použít v asynchronních metodách, kdykoli budete potřebovat obsah webové stránky.</span><span class="sxs-lookup"><span data-stu-id="c24d1-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="c24d1-273">Třída `AsyncCache` zajišťuje, že stahujete co nejméně stránek a ukládá výsledky do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c24d1-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="c24d1-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="c24d1-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="c24d1-275">Úkoly můžete také použít k vytváření datových struktur pro koordinaci asynchronních aktivit.</span><span class="sxs-lookup"><span data-stu-id="c24d1-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="c24d1-276">Vezměme si jeden z klasických paralelních vzorů návrhu: výrobce / spotřebitel.</span><span class="sxs-lookup"><span data-stu-id="c24d1-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="c24d1-277">V tomto modelu výrobci generují údaje, které spotřebovávají spotřebitelé, a výrobci a spotřebitelé mohou probíhat souběžně.</span><span class="sxs-lookup"><span data-stu-id="c24d1-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="c24d1-278">Například spotřebitel zpracovává položku 1, která byla dříve generována výrobcem, který nyní vyrábí položku 2.</span><span class="sxs-lookup"><span data-stu-id="c24d1-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="c24d1-279">Pro výrobce / spotřebitele vzor, vždy potřebujete nějakou strukturu dat pro ukládání práce vytvořené výrobci tak, aby spotřebitelé mohou být informováni o nových údajů a najít je, když je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c24d1-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="c24d1-280">Zde je jednoduchá datová struktura postavená na úlohách, které umožňují použití asynchronních metod jako výrobců a spotřebitelů:</span><span class="sxs-lookup"><span data-stu-id="c24d1-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="c24d1-281">S touto datovou strukturou na místě můžete napsat kód, například následující:</span><span class="sxs-lookup"><span data-stu-id="c24d1-281">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="c24d1-282">Obor <xref:System.Threading.Tasks.Dataflow> názvů obsahuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, který můžete použít podobným způsobem, ale bez nutnosti vytvářet vlastní typ kolekce:</span><span class="sxs-lookup"><span data-stu-id="c24d1-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="c24d1-283">Obor <xref:System.Threading.Tasks.Dataflow> názvů je k dispozici v rozhraní .NET Framework 4.5 až **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c24d1-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="c24d1-284">Chcete-li nainstalovat sestavení, které obsahuje obor <xref:System.Threading.Tasks.Dataflow> názvů, otevřete projekt v sadě Visual Studio, zvolte Spravovat **balíčky NuGet** z nabídky Project a vyhledejte balíček Microsoft.Tpl.Dataflow online.</span><span class="sxs-lookup"><span data-stu-id="c24d1-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="c24d1-285">Viz také</span><span class="sxs-lookup"><span data-stu-id="c24d1-285">See also</span></span>

- [<span data-ttu-id="c24d1-286">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="c24d1-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="c24d1-287">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="c24d1-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="c24d1-288">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="c24d1-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
