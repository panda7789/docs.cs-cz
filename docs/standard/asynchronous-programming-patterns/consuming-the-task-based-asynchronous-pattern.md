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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139811"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="44d77-102">Použití asynchronního vzoru založeného na úloze</span><span class="sxs-lookup"><span data-stu-id="44d77-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="44d77-103">Při použití asynchronního vzoru založeného na úlohách (klepnutím) pro práci s asynchronními operacemi můžete pomocí zpětných volání dosáhnout čekání bez blokování.</span><span class="sxs-lookup"><span data-stu-id="44d77-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="44d77-104">Pro úlohy se to dosáhne prostřednictvím metod, jako je <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44d77-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44d77-105">Jazyková asynchronní podpora skrývá zpětná volání tím, že umožňuje v normálním toku řízení očekávat asynchronní operace a kód generovaný kompilátorem poskytuje stejnou podporu na úrovni API.</span><span class="sxs-lookup"><span data-stu-id="44d77-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="44d77-106">Pozastavení provádění s operátorem await</span><span class="sxs-lookup"><span data-stu-id="44d77-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="44d77-107">Počínaje .NET Framework 4,5 můžete použít klíčové slovo [await](../../csharp/language-reference/operators/await.md) v C# a [operátor await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic k asynchronnímu očekávání <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objektů.</span><span class="sxs-lookup"><span data-stu-id="44d77-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="44d77-108">Když očekáváte <xref:System.Threading.Tasks.Task>, je výraz `await` typu `void`.</span><span class="sxs-lookup"><span data-stu-id="44d77-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="44d77-109">Když očekáváte <xref:System.Threading.Tasks.Task%601>, je výraz `await` typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="44d77-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="44d77-110">Výraz `await` musí být uvnitř těla asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="44d77-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="44d77-111">Další informace o C# a Visual Basic podpoře jazyků v .NET Framework 4,5 naleznete v tématu Specifikace jazyka C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="44d77-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="44d77-112">V rámci pokrývá funkce await nainstaluje zpětné volání na úkol pomocí pokračování.</span><span class="sxs-lookup"><span data-stu-id="44d77-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="44d77-113">Toto zpětné volání pokračuje asynchronní metodou v okamžiku pozastavení.</span><span class="sxs-lookup"><span data-stu-id="44d77-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="44d77-114">Pokud je asynchronní metoda obnovena, pokud se očekávaná operace úspěšně dokončila a byla <xref:System.Threading.Tasks.Task%601>, vrátí se `TResult`.</span><span class="sxs-lookup"><span data-stu-id="44d77-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="44d77-115">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, která byla očekávána jako ukončená ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>, je vyvolána výjimka <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="44d77-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="44d77-116">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, které byly očekávány ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted>, je vyvolána výjimka, která způsobila chybu.</span><span class="sxs-lookup"><span data-stu-id="44d77-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="44d77-117">`Task` může způsobit chybu v důsledku několika výjimek, ale šíří se jenom jedna z těchto výjimek.</span><span class="sxs-lookup"><span data-stu-id="44d77-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="44d77-118">Nicméně vlastnost <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vrací výjimku <xref:System.AggregateException>, která obsahuje všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="44d77-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="44d77-119">Pokud je kontext synchronizace (objekt<xref:System.Threading.SynchronizationContext>) spojen s vláknem, které provádělo asynchronní metodu v době pozastavení (například pokud vlastnost <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> není `null`), asynchronní metoda pokračuje na stejném místě. kontext synchronizace pomocí metody <xref:System.Threading.SynchronizationContext.Post%2A> kontextu.</span><span class="sxs-lookup"><span data-stu-id="44d77-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="44d77-120">V opačném případě se spoléhá na Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler> objekt), který byl aktuální v době pozastavení.</span><span class="sxs-lookup"><span data-stu-id="44d77-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="44d77-121">Obvykle se jedná o výchozí Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), který cílí na fond vláken.</span><span class="sxs-lookup"><span data-stu-id="44d77-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="44d77-122">Tento Plánovač úloh určuje, zda má očekávaná asynchronní operace pokračovat v místě, kde byla dokončena, nebo zda má být obnovení plánováno.</span><span class="sxs-lookup"><span data-stu-id="44d77-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="44d77-123">Výchozí Plánovač obvykle umožňuje spuštění pokračování ve vlákně, které čekalé operace dokončila.</span><span class="sxs-lookup"><span data-stu-id="44d77-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="44d77-124">Když je volána asynchronní metoda, synchronně spustí tělo funkce až do prvního výrazu await v neočekávané instanci, která ještě nebyla dokončena, v tomto okamžiku se volání vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="44d77-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="44d77-125">Pokud asynchronní metoda nevrací `void`, je vrácen objekt <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, který představuje průběžné výpočty.</span><span class="sxs-lookup"><span data-stu-id="44d77-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="44d77-126">V asynchronní metodě, která není typu void, je-li k disřádku návratový příkaz nebo je dosaženo konce textu metody, je úloha dokončena v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečném stavu.</span><span class="sxs-lookup"><span data-stu-id="44d77-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="44d77-127">Pokud Neošetřená výjimka způsobí, že ovládací prvek opustí tělo asynchronní metody, úloha skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted>.</span><span class="sxs-lookup"><span data-stu-id="44d77-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="44d77-128">Pokud je tato výjimka <xref:System.OperationCanceledException>, úloha se místo toho ukončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>.</span><span class="sxs-lookup"><span data-stu-id="44d77-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="44d77-129">Tímto způsobem je výsledek nebo výjimka nakonec publikována.</span><span class="sxs-lookup"><span data-stu-id="44d77-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="44d77-130">Existuje několik důležitých variant tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="44d77-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="44d77-131">Z důvodu výkonu, pokud úloha již byla dokončena v době, kdy je úkol očekáván, řízení není získáno a funkce bude pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="44d77-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="44d77-132">Navíc návrat do původního kontextu není vždy požadovaným chováním a lze jej změnit. Tato informace je podrobněji popsána v následující části.</span><span class="sxs-lookup"><span data-stu-id="44d77-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="44d77-133">Konfigurace pozastavení a obnovení s využitím yield a ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="44d77-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="44d77-134">Několik metod poskytuje větší kontrolu nad prováděním asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="44d77-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="44d77-135">Například můžete použít metodu <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> k zavedení bodu kluzu do asynchronní metody:</span><span class="sxs-lookup"><span data-stu-id="44d77-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="44d77-136">Jedná se o ekvivalent asynchronního účtování nebo plánování zpět do aktuálního kontextu.</span><span class="sxs-lookup"><span data-stu-id="44d77-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="44d77-137">Můžete také použít metodu <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pro lepší kontrolu nad přerušením a pokračováním v asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="44d77-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="44d77-138">Jak bylo zmíněno dříve, aktuální kontext je zachycen v době pozastavení asynchronní metody a tento zachycený kontext slouží k vyvolání pokračování asynchronní metody při obnovení.</span><span class="sxs-lookup"><span data-stu-id="44d77-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="44d77-139">V mnoha případech se jedná o přesné chování, které požadujete.</span><span class="sxs-lookup"><span data-stu-id="44d77-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="44d77-140">V jiných případech se může stát, že nebudete mít pozor na kontext pokračování a můžete dosáhnout lepšího výkonu tím, že tyto příspěvky vyloučíte zpět do původního kontextu.</span><span class="sxs-lookup"><span data-stu-id="44d77-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="44d77-141">Chcete-li to povolit, použijte metodu <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> k informování operace await, která nezachycuje a obnovila kontext, ale pro pokračování v provádění bez ohledu na asynchronní operaci, která byla očekávána:</span><span class="sxs-lookup"><span data-stu-id="44d77-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="44d77-142">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="44d77-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="44d77-143">Počínaje .NET Framework 4 klepněte na metody, které podporují zrušení, poskytují alespoň jedno přetížení, které přijímá token zrušení (objekt<xref:System.Threading.CancellationToken>).</span><span class="sxs-lookup"><span data-stu-id="44d77-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="44d77-144">Token zrušení se vytvoří prostřednictvím zdroje tokenu zrušení (<xref:System.Threading.CancellationTokenSource> objekt).</span><span class="sxs-lookup"><span data-stu-id="44d77-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="44d77-145">Vlastnost <xref:System.Threading.CancellationTokenSource.Token%2A> zdroje vrátí token zrušení, který bude signalizovaná při volání metody zdroje <xref:System.Threading.CancellationTokenSource.Cancel%2A>.</span><span class="sxs-lookup"><span data-stu-id="44d77-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="44d77-146">Například pokud chcete stáhnout jednu webovou stránku a chcete mít možnost operaci zrušit, vytvoříte objekt <xref:System.Threading.CancellationTokenSource>, předáte jeho token do metody klepnutí a potom zavoláte metodu zdrojového <xref:System.Threading.CancellationTokenSource.Cancel%2A>, až budete připraveni operaci zrušit. :</span><span class="sxs-lookup"><span data-stu-id="44d77-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="44d77-147">Chcete-li zrušit více asynchronních volání, můžete stejný token předat všem voláním:</span><span class="sxs-lookup"><span data-stu-id="44d77-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="44d77-148">Nebo můžete stejný token předat do selektivní podmnožiny operací:</span><span class="sxs-lookup"><span data-stu-id="44d77-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="44d77-149">Žádosti o zrušení můžou být iniciované z libovolného vlákna.</span><span class="sxs-lookup"><span data-stu-id="44d77-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="44d77-150">Hodnotu <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> můžete předat libovolné metodě, která přijímá token zrušení, což znamená, že zrušení nebude nikdy požadováno.</span><span class="sxs-lookup"><span data-stu-id="44d77-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="44d77-151">Tím dojde k tomu, že vlastnost <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> vrátí `false`a volaná metoda je odpovídajícím způsobem optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="44d77-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="44d77-152">Pro účely testování můžete také předat předem zrušený token zrušení, jehož instance je vytvořena pomocí konstruktoru, který přijímá logickou hodnotu, k určení, zda má být token začínat již zrušeným nebo nestornovaným stavem.</span><span class="sxs-lookup"><span data-stu-id="44d77-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="44d77-153">Tento přístup k zrušení má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="44d77-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="44d77-154">Stejný token zrušení můžete předat libovolnému počtu asynchronních a synchronních operací.</span><span class="sxs-lookup"><span data-stu-id="44d77-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="44d77-155">Stejná žádost o zrušení může být předaná na libovolný počet posluchačů.</span><span class="sxs-lookup"><span data-stu-id="44d77-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="44d77-156">Vývojář asynchronního rozhraní API má úplnou kontrolu nad tím, zda může být zrušení požadováno a kdy se může projevit.</span><span class="sxs-lookup"><span data-stu-id="44d77-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="44d77-157">Kód, který využívá rozhraní API, může selektivně určit asynchronní vyvolání, na které se požadavky na zrušení rozšíří.</span><span class="sxs-lookup"><span data-stu-id="44d77-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="44d77-158">Sledování průběhu</span><span class="sxs-lookup"><span data-stu-id="44d77-158">Monitoring Progress</span></span>
 <span data-ttu-id="44d77-159">Některé asynchronní metody zpřístupňují průběh prostřednictvím rozhraní průběhu předaného do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="44d77-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="44d77-160">Představte si například funkci, která asynchronně stáhne textový řetězec a společně způsob vyvolává aktualizace průběhu, které zahrnují procento stahování, které bylo doposud dokončeno.</span><span class="sxs-lookup"><span data-stu-id="44d77-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="44d77-161">Taková metoda by mohla být spotřebována v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="44d77-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="44d77-162">Použití integrovaného kombinátory založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="44d77-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="44d77-163">Obor názvů <xref:System.Threading.Tasks> obsahuje několik metod pro vytváření a práci s úkoly.</span><span class="sxs-lookup"><span data-stu-id="44d77-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="44d77-164">Task. Run</span><span class="sxs-lookup"><span data-stu-id="44d77-164">Task.Run</span></span>
 <span data-ttu-id="44d77-165">Třída <xref:System.Threading.Tasks.Task> obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metod, které umožňují snadno přesměrovat práci jako <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> do fondu vláken, například:</span><span class="sxs-lookup"><span data-stu-id="44d77-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="44d77-166">Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metod, jako je například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> přetížení, existují jako zkratky pro metodu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44d77-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="44d77-167">Další přetížení, jako je například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, umožňují použití operátoru await v rámci práce s převedenou zátěží, například:</span><span class="sxs-lookup"><span data-stu-id="44d77-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="44d77-168">Taková přetížení jsou logicky ekvivalentní použití metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> ve spojení s metodou rozšíření <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> v Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="44d77-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="44d77-169">Task. FromResult</span><span class="sxs-lookup"><span data-stu-id="44d77-169">Task.FromResult</span></span>
 <span data-ttu-id="44d77-170">Použijte metodu <xref:System.Threading.Tasks.Task.FromResult%2A> ve scénářích, kde již mohou být data k dispozici a stačí je vrátit z metody vracené úlohou do <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="44d77-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="44d77-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="44d77-171">Task.WhenAll</span></span>
 <span data-ttu-id="44d77-172">Použijte metodu <xref:System.Threading.Tasks.Task.WhenAll%2A> k asynchronnímu čekání na více asynchronních operací, které jsou reprezentovány jako úkoly.</span><span class="sxs-lookup"><span data-stu-id="44d77-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="44d77-173">Metoda má více přetížení, které podporují sadu neobecných úkolů nebo nejednotnou sadu obecných úloh (například asynchronní čekání na více operací vracejících anulování nebo asynchronní čekání na více metod vracejících hodnoty, kde Každá hodnota může mít jiný typ a podporovat jednotnou sadu obecných úloh (například asynchronní čekání na více metod vracejícících se `TResult`).</span><span class="sxs-lookup"><span data-stu-id="44d77-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="44d77-174">Řekněme, že chcete odesílat e-mailové zprávy několika zákazníkům.</span><span class="sxs-lookup"><span data-stu-id="44d77-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="44d77-175">Posílání zpráv se můžete překrývat, takže nečekáte na dokončení jedné zprávy, než odešlete další.</span><span class="sxs-lookup"><span data-stu-id="44d77-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="44d77-176">Můžete také zjistit, kdy byly operace odeslání dokončeny a zda došlo k chybám:</span><span class="sxs-lookup"><span data-stu-id="44d77-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="44d77-177">Tento kód explicitně nezpracovává výjimky, ke kterým může dojít, ale umožňuje výjimky šířit z `await` na výsledný úkol z <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="44d77-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="44d77-178">Chcete-li zpracovat výjimky, můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="44d77-178">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="44d77-179">V takovém případě, pokud dojde k chybě jakékoli asynchronní operace, všechny výjimky budou konsolidovány v <xref:System.AggregateException> výjimce, která je uložena v <xref:System.Threading.Tasks.Task>, který je vrácen z metody <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="44d77-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="44d77-180">Avšak pouze jedna z těchto výjimek je šířena klíčovým slovem `await`.</span><span class="sxs-lookup"><span data-stu-id="44d77-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="44d77-181">Pokud chcete kontrolovat všechny výjimky, můžete přepsat předchozí kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="44d77-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="44d77-182">Podívejme se na příklad asynchronního stahování více souborů z webu.</span><span class="sxs-lookup"><span data-stu-id="44d77-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="44d77-183">V tomto případě mají všechny asynchronní operace homogenní typy výsledků a je snadné získat přístup k výsledkům:</span><span class="sxs-lookup"><span data-stu-id="44d77-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="44d77-184">Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vracejícím anulování:</span><span class="sxs-lookup"><span data-stu-id="44d77-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

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

### <a name="taskwhenany"></a><span data-ttu-id="44d77-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="44d77-185">Task.WhenAny</span></span>
 <span data-ttu-id="44d77-186">Metodu <xref:System.Threading.Tasks.Task.WhenAny%2A> lze použít k asynchronnímu čekání pouze na jednu z několika asynchronních operací reprezentovaných jako úlohy, které mají být dokončeny.</span><span class="sxs-lookup"><span data-stu-id="44d77-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="44d77-187">Tato metoda slouží ke čtyřem primárním případům použití:</span><span class="sxs-lookup"><span data-stu-id="44d77-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="44d77-188">Redundance: operace provede několikrát a vybere tu, která se dokončí jako první (například kontaktování více webových služeb na základě akcií, které vytvoří jeden výsledek a výběr toho, který dokončí nejrychlejší).</span><span class="sxs-lookup"><span data-stu-id="44d77-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="44d77-189">Prokládání: spouštění více operací a čekání na jejich dokončení, ale jejich zpracování po dokončení.</span><span class="sxs-lookup"><span data-stu-id="44d77-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="44d77-190">Omezování: povolení dalších operací, které se začnou provádět jako ostatní.</span><span class="sxs-lookup"><span data-stu-id="44d77-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="44d77-191">Toto je rozšíření scénáře pro proplutí.</span><span class="sxs-lookup"><span data-stu-id="44d77-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="44d77-192">Předčasné Bailout: například operace reprezentovaná úlohou T1 se dá seskupit do úlohy <xref:System.Threading.Tasks.Task.WhenAny%2A> s jiným úkolem T2 a můžete počkat na <xref:System.Threading.Tasks.Task.WhenAny%2A> úlohu.</span><span class="sxs-lookup"><span data-stu-id="44d77-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="44d77-193">Úloha T2 by mohla představovat časový limit nebo zrušení nebo nějaký jiný signál, který způsobí dokončení úlohy <xref:System.Threading.Tasks.Task.WhenAny%2A> před dokončením T1.</span><span class="sxs-lookup"><span data-stu-id="44d77-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="44d77-194">Redundance</span><span class="sxs-lookup"><span data-stu-id="44d77-194">Redundancy</span></span>
 <span data-ttu-id="44d77-195">Vezměte v úvahu případ, kdy si přejete rozhodnout, jestli chcete koupit zásobu.</span><span class="sxs-lookup"><span data-stu-id="44d77-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="44d77-196">K dispozici je několik webových služeb s doporučeními pro základní zdroje, ale v závislosti na denním zatížení může být každá služba v různou dobu pomalejší.</span><span class="sxs-lookup"><span data-stu-id="44d77-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="44d77-197">Pomocí metody <xref:System.Threading.Tasks.Task.WhenAny%2A> můžete obdržet oznámení, když se dokončí nějaká operace:</span><span class="sxs-lookup"><span data-stu-id="44d77-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="44d77-198">Na rozdíl od <xref:System.Threading.Tasks.Task.WhenAll%2A>, která vrací nezabalené výsledky všech úloh, které byly úspěšně dokončeny, <xref:System.Threading.Tasks.Task.WhenAny%2A> vrátí dokončenou úlohu.</span><span class="sxs-lookup"><span data-stu-id="44d77-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="44d77-199">Pokud úloha selže, je důležité, abyste věděli, že se nezdařila, a pokud je úloha úspěšná, je důležité znát, ke které úloze je vrácená hodnota přidružená.</span><span class="sxs-lookup"><span data-stu-id="44d77-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="44d77-200">Proto potřebujete získat přístup k výsledku vráceného úkolu nebo ho očekávat více, jak ukazuje tento příklad.</span><span class="sxs-lookup"><span data-stu-id="44d77-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="44d77-201">Stejně jako u <xref:System.Threading.Tasks.Task.WhenAll%2A>musí být možné vyhovět výjimkám.</span><span class="sxs-lookup"><span data-stu-id="44d77-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="44d77-202">Vzhledem k tomu, že obdržíte dokončenou úlohu zpět, můžete očekávat, že vrácená úloha bude mít přenesené chyby a patřičně je `try/catch`. například:</span><span class="sxs-lookup"><span data-stu-id="44d77-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="44d77-203">Kromě toho, i když se první úkol úspěšně dokončí, můžou následné úkoly selhat.</span><span class="sxs-lookup"><span data-stu-id="44d77-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="44d77-204">V tomto okamžiku máte k dispozici několik možností pro práci s výjimkami: můžete počkat, až se všechny spuštěné úlohy dokončí, a v takovém případě můžete použít metodu <xref:System.Threading.Tasks.Task.WhenAll%2A>, nebo se můžete rozhodnout, že jsou všechny výjimky důležité a musí být zaprotokolovány.</span><span class="sxs-lookup"><span data-stu-id="44d77-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="44d77-205">K tomu můžete použít pokračování pro příjem oznámení, když se úkoly asynchronně dokončují:</span><span class="sxs-lookup"><span data-stu-id="44d77-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="44d77-206">nebo:</span><span class="sxs-lookup"><span data-stu-id="44d77-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="44d77-207">nebo dokonce:</span><span class="sxs-lookup"><span data-stu-id="44d77-207">or even:</span></span>

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

 <span data-ttu-id="44d77-208">Nakonec můžete chtít zrušit všechny zbývající operace:</span><span class="sxs-lookup"><span data-stu-id="44d77-208">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="44d77-209">Potřeba prokládání</span><span class="sxs-lookup"><span data-stu-id="44d77-209">Interleaving</span></span>
 <span data-ttu-id="44d77-210">Vezměte v úvahu případ, kdy stahujete obrázky z webu a zpracováváte jednotlivé Image (například přidáním obrázku do ovládacího prvku uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="44d77-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="44d77-211">Je nutné provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout obrázky jako souběžně.</span><span class="sxs-lookup"><span data-stu-id="44d77-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="44d77-212">Nechcete také přidržet obrázky do uživatelského rozhraní, dokud se všechny nestáhnou – chcete je přidat po dokončení:</span><span class="sxs-lookup"><span data-stu-id="44d77-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

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

 <span data-ttu-id="44d77-213">Můžete také použít přejezd na scénář, který zahrnuje výpočetně náročné zpracování na <xref:System.Threading.ThreadPool> stažených imagí. například:</span><span class="sxs-lookup"><span data-stu-id="44d77-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="44d77-214">Omezování</span><span class="sxs-lookup"><span data-stu-id="44d77-214">Throttling</span></span>
 <span data-ttu-id="44d77-215">Vezměte v úvahu příklad prokládání s tím rozdílem, že uživatel je stahuje, takže mnoho imagí, které je potřeba stáhnout, je nutné omezit. například chcete, aby bylo možné současně provést pouze určitý počet souborů ke stažení.</span><span class="sxs-lookup"><span data-stu-id="44d77-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="44d77-216">K tomuto účelu můžete spustit podmnožinu asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="44d77-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="44d77-217">Po dokončení operací můžete spustit další operace, které zabírají místo:</span><span class="sxs-lookup"><span data-stu-id="44d77-217">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="44d77-218">Předčasné Bailout</span><span class="sxs-lookup"><span data-stu-id="44d77-218">Early Bailout</span></span>
 <span data-ttu-id="44d77-219">Vezměte v úvahu, že budete čekat asynchronně, než se operace dokončí, a současně reagovat na požadavek na zrušení uživatele (například uživatel kliknul na tlačítko Storno).</span><span class="sxs-lookup"><span data-stu-id="44d77-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="44d77-220">Tento scénář je znázorněný v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="44d77-220">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="44d77-221">Tato implementace znovu povolí uživatelské rozhraní hned po rozhodnutí Bail, ale neruší základní asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="44d77-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="44d77-222">Další možností je zrušit nedokončené operace, když se rozhodnete Bail, ale nebudete moci znovu vytvořit uživatelské rozhraní, dokud se operace neprojeví, potenciálně v důsledku ukončení v důsledku žádosti o zrušení:</span><span class="sxs-lookup"><span data-stu-id="44d77-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="44d77-223">Dalším příkladem předčasného bailoutu je použití metody <xref:System.Threading.Tasks.Task.WhenAny%2A> ve spojení s metodou <xref:System.Threading.Tasks.Task.Delay%2A>, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="44d77-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="44d77-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="44d77-224">Task.Delay</span></span>
 <span data-ttu-id="44d77-225">Můžete použít metodu <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> k zavedení pozastavení do provádění asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="44d77-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="44d77-226">To je užitečné pro mnoho druhů funkcí, včetně vytváření smyček cyklického dotazování a zpoždění manipulace s uživatelským vstupem pro předem stanovenou dobu.</span><span class="sxs-lookup"><span data-stu-id="44d77-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="44d77-227">Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> může být také užitečná v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementaci časových limitů při čekání.</span><span class="sxs-lookup"><span data-stu-id="44d77-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="44d77-228">Pokud úkol, který je součástí větší asynchronní operace (například webové služby ASP.NET), trvá příliš dlouho, může to být způsobeno tím, že by celková operace byla neúspěšná, zejména v případě, že se nepovede dřív.</span><span class="sxs-lookup"><span data-stu-id="44d77-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="44d77-229">Z tohoto důvodu je důležité mít při čekání na asynchronní operaci časový limit.</span><span class="sxs-lookup"><span data-stu-id="44d77-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="44d77-230">Synchronní metody <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> přijímají hodnoty časového limitu, ale odpovídající <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše zmíněné <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/metody ne.</span><span class="sxs-lookup"><span data-stu-id="44d77-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="44d77-231">Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci k implementaci časového limitu.</span><span class="sxs-lookup"><span data-stu-id="44d77-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="44d77-232">Například v aplikaci uživatelského rozhraní řekněme, že chcete stáhnout image a zakázat uživatelské rozhraní při stahování image.</span><span class="sxs-lookup"><span data-stu-id="44d77-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="44d77-233">Pokud ale stahování trvá příliš dlouho, budete chtít znovu povolit uživatelské rozhraní a zahodit stahování:</span><span class="sxs-lookup"><span data-stu-id="44d77-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="44d77-234">Totéž platí pro více souborů ke stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úlohu:</span><span class="sxs-lookup"><span data-stu-id="44d77-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="44d77-235">Sestavování kombinátory založených na úlohách</span><span class="sxs-lookup"><span data-stu-id="44d77-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="44d77-236">Vzhledem k tomu, že úloha může zcela představovat asynchronní operaci a poskytovat synchronní a asynchronní možnosti pro připojení k operaci, načítání výsledků a tak dále, můžete vytvářet užitečné knihovny kombinátory, které vytvářejí úkoly. Sestavujte větší vzory.</span><span class="sxs-lookup"><span data-stu-id="44d77-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="44d77-237">Jak je popsáno v předchozí části, .NET Framework obsahuje několik integrovaných kombinátory, ale můžete si také vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="44d77-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="44d77-238">Následující části obsahují několik příkladů potenciálních metod a typů kombinátorem.</span><span class="sxs-lookup"><span data-stu-id="44d77-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="44d77-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="44d77-239">RetryOnFault</span></span>
 <span data-ttu-id="44d77-240">V mnoha situacích můžete zkusit operaci zopakovat, pokud se předchozí pokus nezdaří.</span><span class="sxs-lookup"><span data-stu-id="44d77-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="44d77-241">V případě synchronního kódu můžete vytvořit pomocnou metodu, například `RetryOnFault` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="44d77-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="44d77-242">Můžete vytvořit téměř identickou pomocnou metodu pro asynchronní operace, které jsou implementovány klepnutím a následně vracet úlohy:</span><span class="sxs-lookup"><span data-stu-id="44d77-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="44d77-243">Pak můžete použít tuto kombinátorem ke kódování opakovaných pokusů do logiky aplikace. například:</span><span class="sxs-lookup"><span data-stu-id="44d77-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="44d77-244">Dále můžete rozšířit funkci `RetryOnFault`.</span><span class="sxs-lookup"><span data-stu-id="44d77-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="44d77-245">Funkce například může přijmout další `Func<Task>`, který bude vyvolán mezi opakovanými pokusy, aby bylo možné určit, kdy se má operace opakovat. například:</span><span class="sxs-lookup"><span data-stu-id="44d77-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="44d77-246">Potom můžete funkci použít následujícím způsobem, aby před opakováním operace čekala na sekundu:</span><span class="sxs-lookup"><span data-stu-id="44d77-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="44d77-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="44d77-247">NeedOnlyOne</span></span>
 <span data-ttu-id="44d77-248">V některých případech můžete využít redundanci a zlepšit latenci operace a šance na úspěch.</span><span class="sxs-lookup"><span data-stu-id="44d77-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="44d77-249">Vezměte v úvahu více webových služeb, které poskytují nabídky, ale v různou dobu může každá služba poskytovat různé úrovně kvality a doby odezvy.</span><span class="sxs-lookup"><span data-stu-id="44d77-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="44d77-250">Pokud chcete řešit tyto výkyvy, můžete vydávat požadavky na všechny webové služby a hned po obdržení odpovědi zrušit zbývající požadavky.</span><span class="sxs-lookup"><span data-stu-id="44d77-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="44d77-251">Můžete implementovat pomocnou funkci, která usnadňuje implementaci tohoto běžného vzoru spouštění více operací, čekání na jakékoli a následné zrušení zbytku.</span><span class="sxs-lookup"><span data-stu-id="44d77-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="44d77-252">Funkce `NeedOnlyOne` v následujícím příkladu znázorňuje tento scénář:</span><span class="sxs-lookup"><span data-stu-id="44d77-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="44d77-253">Tuto funkci pak můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="44d77-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="44d77-254">Prokládané operace</span><span class="sxs-lookup"><span data-stu-id="44d77-254">Interleaved Operations</span></span>
 <span data-ttu-id="44d77-255">Při práci s velmi velkým počtem úloh je možné využít potenciální potíže s výkonem při použití metody <xref:System.Threading.Tasks.Task.WhenAny%2A> k podpoře scénáře prokládaných dat.</span><span class="sxs-lookup"><span data-stu-id="44d77-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span> <span data-ttu-id="44d77-256">Každé volání <xref:System.Threading.Tasks.Task.WhenAny%2A> má za následek pokračování zaregistrované u každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="44d77-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="44d77-257">Pro N počet úkolů to vede k pokračování v počtu (N<sup>2</sup>), které bylo vytvořeno během doby trvání prokládání operací.</span><span class="sxs-lookup"><span data-stu-id="44d77-257">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="44d77-258">Pokud pracujete s velkou sadou úkolů, můžete k vyřešení problému s výkonem použít kombinátorem (`Interleaved` v následujícím příkladu):</span><span class="sxs-lookup"><span data-stu-id="44d77-258">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="44d77-259">Pak můžete použít kombinátorem ke zpracování výsledků úloh po jejich dokončení. například:</span><span class="sxs-lookup"><span data-stu-id="44d77-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="44d77-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="44d77-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="44d77-261">V určitých bodových nebo sběrných scénářích můžete chtít počkat na všechny úlohy v sadě, pokud jedna z nich selže, a v takovém případě se chcete přestat čekat, jakmile dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="44d77-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="44d77-262">To lze provést pomocí metody kombinátorem, jako je například `WhenAllOrFirstException` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="44d77-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="44d77-263">Vytváření datových struktur založených na úlohách</span><span class="sxs-lookup"><span data-stu-id="44d77-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="44d77-264">Kromě možnosti vytvářet vlastní kombinátory založený na úlohách, které mají datovou strukturu v <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601>, která představuje jak výsledky asynchronní operace, tak i nutná synchronizace pro připojení, díky tomu má velmi účinný typ který umožňuje vytvářet vlastní datové struktury, které se mají použít v asynchronních scénářích.</span><span class="sxs-lookup"><span data-stu-id="44d77-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="44d77-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="44d77-265">AsyncCache</span></span>
 <span data-ttu-id="44d77-266">Jedním z důležitých aspektů úkolu je, že může být předána více příjemcům, a to vše, co může očekávat, zaregistrovat pokračování s ním, získat výsledek nebo výjimky (v případě <xref:System.Threading.Tasks.Task%601>) atd.</span><span class="sxs-lookup"><span data-stu-id="44d77-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="44d77-267">Díky tomu jsou <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> naprosto vhodné k použití v asynchronní infrastruktuře ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44d77-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="44d77-268">Tady je příklad malé, ale výkonné asynchronní mezipaměti postavené nad <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="44d77-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="44d77-269">[AsyncCache\<TKey třída TValue >](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) přijímá jako delegáta funkci, která přijímá `TKey` a vrací <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="44d77-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="44d77-270">Všechny dříve použité hodnoty z mezipaměti se ukládají do interního slovníku a `AsyncCache` zajistí, že se pro každý klíč vygeneruje jenom jeden úkol, i když se k mezipaměti přistupoval souběžně.</span><span class="sxs-lookup"><span data-stu-id="44d77-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="44d77-271">Můžete například sestavit mezipaměť pro stažené webové stránky:</span><span class="sxs-lookup"><span data-stu-id="44d77-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="44d77-272">Tuto mezipaměť pak můžete použít v asynchronních metodách vždy, když potřebujete obsah webové stránky.</span><span class="sxs-lookup"><span data-stu-id="44d77-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="44d77-273">Třída `AsyncCache` zajišťuje, že budete stahovat co nejvíce stránek a ukládá výsledky do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44d77-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

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

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="44d77-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="44d77-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="44d77-275">Úkoly můžete použít také k vytváření datových struktur pro koordinaci asynchronních aktivit.</span><span class="sxs-lookup"><span data-stu-id="44d77-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="44d77-276">Vezměte v úvahu jeden z klasických paralelních vzorů návrhu: producent/příjemce.</span><span class="sxs-lookup"><span data-stu-id="44d77-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="44d77-277">V tomto vzoru producenti generují data, která jsou využívána příjemci, a producenti a spotřebitelé můžou běžet paralelně.</span><span class="sxs-lookup"><span data-stu-id="44d77-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="44d77-278">Například příjemce zpracuje položku 1, která byla dříve vygenerována výrobcem, který nyní vyrábí položku 2.</span><span class="sxs-lookup"><span data-stu-id="44d77-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="44d77-279">Pro vzorek producent/příjemce invariably potřebovat určitou datovou strukturu pro ukládání práce vytvořené producenty, aby se příjemci mohli dostat k oznámením o nových datech a najít je, když jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="44d77-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="44d77-280">Tady je jednoduchá datová struktura postavená na úkolech, která umožňuje použití asynchronních metod jako výrobců a spotřebitelů:</span><span class="sxs-lookup"><span data-stu-id="44d77-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="44d77-281">Pomocí této struktury dat můžete napsat kód, například následující:</span><span class="sxs-lookup"><span data-stu-id="44d77-281">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="44d77-282">Obor názvů <xref:System.Threading.Tasks.Dataflow> zahrnuje typ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, který lze použít podobným způsobem, ale bez nutnosti sestavení vlastního typu kolekce:</span><span class="sxs-lookup"><span data-stu-id="44d77-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="44d77-283">Obor názvů <xref:System.Threading.Tasks.Dataflow> je k dispozici v .NET Framework 4,5 až **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="44d77-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="44d77-284">Chcete-li nainstalovat sestavení, které obsahuje obor názvů <xref:System.Threading.Tasks.Dataflow>, otevřete projekt v aplikaci Visual Studio, v nabídce projekt vyberte možnost **Spravovat balíčky NuGet** a vyhledejte balíček Microsoft. tpl. Dataflow v online režimu.</span><span class="sxs-lookup"><span data-stu-id="44d77-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="44d77-285">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44d77-285">See also</span></span>

- [<span data-ttu-id="44d77-286">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="44d77-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="44d77-287">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="44d77-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="44d77-288">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="44d77-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
