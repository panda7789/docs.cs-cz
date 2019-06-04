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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d5798b8067bde8b711982bfe4f78d66fe1521c6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490834"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="980da-102">Použití asynchronního vzoru založeného na úloze</span><span class="sxs-lookup"><span data-stu-id="980da-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="980da-103">Použijete-li založený na úlohách asynchronního vzoru (TAP) pro práci s asynchronní operace, můžete použít zpětná volání k dosažení čekání bez blokování.</span><span class="sxs-lookup"><span data-stu-id="980da-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="980da-104">Pro úlohy, toho je dosaženo pomocí metod, jako <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="980da-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="980da-105">Založený na jazyce asynchronní podporu skryje zpětná volání tím, že asynchronní operace do ní použít operátor await v rámci normálního toku řízení a kód generovaný kompilátorem podporuje tento stejnou úroveň rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="980da-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="980da-106">Pozastavení provádění s Await</span><span class="sxs-lookup"><span data-stu-id="980da-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="980da-107">Od verze rozhraní .NET Framework 4.5, můžete použít [await](~/docs/csharp/language-reference/keywords/await.md) – klíčové slovo v C# a [operátor Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic asynchronně await pro čekání <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty.</span><span class="sxs-lookup"><span data-stu-id="980da-107">Starting with the .NET Framework 4.5, you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="980da-108">Když se čeká na <xref:System.Threading.Tasks.Task>, `await` výraz je typu `void`.</span><span class="sxs-lookup"><span data-stu-id="980da-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="980da-109">Když se čeká na <xref:System.Threading.Tasks.Task%601>, `await` výraz je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="980da-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="980da-110">`await` Výraz se musí vyskytovat uvnitř těla asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="980da-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="980da-111">Další informace o C# a podpora jazyka Visual Basic v rozhraní .NET Framework 4.5, podívejte se C# a specifikace jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="980da-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="980da-112">Pod pokličkou nainstaluje funkci await pomocí pokračování na úkolu zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="980da-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="980da-113">Toto zpětné volání pokračuje v okamžiku pozastavení asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="980da-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="980da-114">Když se obnoví asynchronní metody, pokud očekávané operace byla úspěšně dokončena a byla <xref:System.Threading.Tasks.Task%601>, jeho `TResult` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="980da-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="980da-115">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , která byla očekávána skončila v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, <xref:System.OperationCanceledException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="980da-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="980da-116">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , která byla očekávána skončila v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu, je vyvolána výjimka, která způsobila selhání.</span><span class="sxs-lookup"><span data-stu-id="980da-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="980da-117">A `Task` můžete selhání v důsledku více výjimek, ale pouze jeden z těchto výjimek je rozšířena.</span><span class="sxs-lookup"><span data-stu-id="980da-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="980da-118">Ale <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.AggregateException> výjimku, která obsahuje všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="980da-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="980da-119">Pokud kontext synchronizace (<xref:System.Threading.SynchronizationContext> objektu) souvisí s vláknem, které v okamžiku pozastavení provádění asynchronní metody (např. Pokud <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> jedná o vlastnost neumožňující `null`), asynchronní metody pokračuje na, který stejný kontext synchronizace s využitím daného kontextu <xref:System.Threading.SynchronizationContext.Post%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="980da-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="980da-120">V opačném případě spoléhá na Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler> objektu), který byl aktuální v okamžiku pozastavení.</span><span class="sxs-lookup"><span data-stu-id="980da-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="980da-121">Obvykle je to výchozí Plánovač úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), který se zaměřuje na fond vláken.</span><span class="sxs-lookup"><span data-stu-id="980da-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="980da-122">Tento Plánovač úloh Určuje, zda očekávaná asynchronní operace měla pokračovat, kde dokončena nebo zda má být naplánováno opětovné.</span><span class="sxs-lookup"><span data-stu-id="980da-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="980da-123">Výchozí plánovač obvykle umožňuje pokračování spuštěno ve vlákně, očekávané operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="980da-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="980da-124">Při volání asynchronní metody, je tělo funkce synchronně spustí, až do první await výraz v očekávatelný instanci, která zatím není dokončený, v tomto okamžiku volání vrátí řízení volajícímu.</span><span class="sxs-lookup"><span data-stu-id="980da-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="980da-125">Pokud asynchronní metoda nevrací `void`, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> je vrácen objekt představující probíhající výpočtu.</span><span class="sxs-lookup"><span data-stu-id="980da-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="980da-126">V asynchronní metodě není void, pokud se zjistila návratový příkaz nebo je dosaženo konce tělo metody, dokončení úlohy v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> koncový stav.</span><span class="sxs-lookup"><span data-stu-id="980da-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="980da-127">Pokud k neošetřené výjimce způsobí, že ovládací prvek opustit tělo asynchronní metody, skončí tento úkol ve <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu.</span><span class="sxs-lookup"><span data-stu-id="980da-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="980da-128">Pokud tuto výjimku <xref:System.OperationCanceledException>, místo toho skončí tento úkol ve <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.</span><span class="sxs-lookup"><span data-stu-id="980da-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="980da-129">Tímto způsobem výsledek nebo výjimku nakonec publikování.</span><span class="sxs-lookup"><span data-stu-id="980da-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="980da-130">Existuje několik důležitých variant tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="980da-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="980da-131">Z důvodů výkonu Pokud úloha již byla dokončena v čase je na úkol čekáno není poskytuje ovládací prvek a pokračuje v provádění funkce.</span><span class="sxs-lookup"><span data-stu-id="980da-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="980da-132">Kromě toho vrátí do původního kontextu není vždy požadované chování a je možné změnit; To je popsáno v následující části podrobněji.</span><span class="sxs-lookup"><span data-stu-id="980da-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="980da-133">Konfigurace pozastavení a obnovení pomocí Yield a ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="980da-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="980da-134">Několik metody poskytují větší kontrolu nad spouštěním asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="980da-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="980da-135">Například můžete použít <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metoda zavést bod yield do asynchronní metody:</span><span class="sxs-lookup"><span data-stu-id="980da-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="980da-136">Jde o ekvivalent asynchronně účtování nebo plánování zpět do aktuálního kontextu.</span><span class="sxs-lookup"><span data-stu-id="980da-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="980da-137">Můžete také použít <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a pokračování v asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="980da-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="980da-138">Jak už bylo zmíněno dříve, ve výchozím nastavení, je aktuální kontext zaznamenané v době, kterou metodu je pozastavený, a že zachyceném kontextu se používá k volání asynchronní metody pokračování po obnovení.</span><span class="sxs-lookup"><span data-stu-id="980da-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="980da-139">V mnoha případech jde přesnou chování, které chcete.</span><span class="sxs-lookup"><span data-stu-id="980da-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="980da-140">V jiných případech nemusí starat o kontext pokračování a můžou dosahovat lepšího výkonu zabráněním takových příspěvků zpět do původního kontextu.</span><span class="sxs-lookup"><span data-stu-id="980da-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="980da-141">Chcete-li povolit, použijte <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metoda informovat operace await zaznamenat a obnovit v kontextu, ale chcete-li pokračovat v provádění bez ohledu na to, který se očekávaná asynchronní operace dokončena:</span><span class="sxs-lookup"><span data-stu-id="980da-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="980da-142">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="980da-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="980da-143">Od verze rozhraní .NET Framework 4, poskytuje metody TAP, které podporují zrušení alespoň jedním přetížením, která přijímá token zrušení (<xref:System.Threading.CancellationToken> objekt).</span><span class="sxs-lookup"><span data-stu-id="980da-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="980da-144">Token zrušení je vytvořená prostřednictvím zdroj token zrušení (<xref:System.Threading.CancellationTokenSource> objekt).</span><span class="sxs-lookup"><span data-stu-id="980da-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="980da-145">Zdroje na <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost vrátí token zrušení, který bude signál při zdroje <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="980da-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="980da-146">Pokud chcete stáhnout jediné webové stránky a chcete být schopni zrušit operaci, můžete vytvořit <xref:System.Threading.CancellationTokenSource> objektu, předejte svůj token metody TAP a následně zavolat zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda až budete připraveni na zrušení operace:</span><span class="sxs-lookup"><span data-stu-id="980da-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="980da-147">Pokud chcete zrušit více asynchronní vyvolání, můžete předat stejný token všechna volání:</span><span class="sxs-lookup"><span data-stu-id="980da-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="980da-148">Nebo můžete předat stejný token selektivní podmnožinu operace:</span><span class="sxs-lookup"><span data-stu-id="980da-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="980da-149">Žádosti o zrušení, může být vyvoláno z libovolného vlákna.</span><span class="sxs-lookup"><span data-stu-id="980da-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="980da-150">Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu na jakoukoli metodu, která přijímá token zrušení pro označení, že se nikdy být požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="980da-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="980da-151">To způsobí, že <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> vlastnost vrátit `false`, a volané metody můžete optimalizovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="980da-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="980da-152">Pro účely testování můžete také předat token zrušení předem zrušené, jehož instance je vytvořena pomocí konstruktoru, který přijímá hodnotu typu Boolean označující, zda token, který by měl spustit ve stavu už zrušená nebo není zrušitelný.</span><span class="sxs-lookup"><span data-stu-id="980da-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="980da-153">Tento přístup k zrušení má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="980da-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="980da-154">Můžete předat stejný token zrušení do libovolného počtu synchronní a asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="980da-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="980da-155">Stejný požadavek na zrušení může proliferated do libovolného počtu naslouchacích procesů.</span><span class="sxs-lookup"><span data-stu-id="980da-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="980da-156">Vývojář asynchronní rozhraní API je plně pod kontrolou, jestli může být požadováno zrušení a kdy ji může platit.</span><span class="sxs-lookup"><span data-stu-id="980da-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="980da-157">Kód, který využívá rozhraní API může určit selektivně asynchronní vyvolání, které požadavky zrušení se rozšíří do.</span><span class="sxs-lookup"><span data-stu-id="980da-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="980da-158">Sledování průběhu</span><span class="sxs-lookup"><span data-stu-id="980da-158">Monitoring Progress</span></span>
 <span data-ttu-id="980da-159">Některé asynchronní metody vystavit průběh prostřednictvím rozhraní postupu předané do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="980da-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="980da-160">Představte si třeba, že funkce, která asynchronně stáhne řetězec textu a na cestě vyvolává průběh aktualizace, které zahrnují procentuální stažení, které doposud dokončeno.</span><span class="sxs-lookup"><span data-stu-id="980da-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="980da-161">Tato metoda může spotřebovat v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="980da-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="980da-162">Pomocí předdefinovaných Combinators založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="980da-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="980da-163"><xref:System.Threading.Tasks> Obor názvů obsahuje několik metod pro vytváření a práci s úkoly.</span><span class="sxs-lookup"><span data-stu-id="980da-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="980da-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="980da-164">Task.Run</span></span>
 <span data-ttu-id="980da-165"><xref:System.Threading.Tasks.Task> Třída obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metody, které vám umožní snadno snižování zátěže fungovat stejně jako <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> s fondem vláken, například:</span><span class="sxs-lookup"><span data-stu-id="980da-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="980da-166">Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metody, například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> přetížení, existují jako zkratka pro <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="980da-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="980da-167">Druhé přetížení, jako například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, povolit použití operátoru await sníženou zátěží díla, například:</span><span class="sxs-lookup"><span data-stu-id="980da-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="980da-168">Takovými přetíženími jsou logicky ekvivalentní k použití <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda ve spojení s <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metoda v knihovně Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="980da-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="980da-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="980da-169">Task.FromResult</span></span>
 <span data-ttu-id="980da-170">Použití <xref:System.Threading.Tasks.Task.FromResult%2A> metoda ve scénářích, kde data může už být k dispozici a jenom je potřeba vrátil z metody vracející úlohy do zrušeno <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="980da-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="980da-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="980da-171">Task.WhenAll</span></span>
 <span data-ttu-id="980da-172">Použití <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronně čekat na více asynchronních operací, které jsou reprezentovány ve formě úlohy.</span><span class="sxs-lookup"><span data-stu-id="980da-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="980da-173">Tato metoda má několik přetížení, které podporují sadu neobecnou úloh nebo nerovnoměrné sady úloh obecný (například asynchronně čeká na více operací vracející hodnotu void, nebo asynchronně čeká na několik metod vrací hodnotu kde Každá hodnota může mít jiný typ) a podporovat jednotné sadu obecných úloh (jako je například asynchronně čeká na více `TResult`-metody vracející).</span><span class="sxs-lookup"><span data-stu-id="980da-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="980da-174">Řekněme, že chcete odeslat e-mailové zprávy pro několik zákazníků.</span><span class="sxs-lookup"><span data-stu-id="980da-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="980da-175">Můžete se může překrývat odesílání zprávy, proto nejsou čekání dokončit před odesláním dalších zpráv.</span><span class="sxs-lookup"><span data-stu-id="980da-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="980da-176">Můžete také získat informace při dokončení operace odesílání a určuje, zda nedošlo k chybám:</span><span class="sxs-lookup"><span data-stu-id="980da-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="980da-177">Tento kód nezpracuje explicitně výjimky, které může dojít, ale umožní výjimky nešířily z celkového počtu `await` na výsledný úkol z <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="980da-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="980da-178">Zpracování výjimek, můžete použít například následující kód:</span><span class="sxs-lookup"><span data-stu-id="980da-178">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="980da-179">V takovém případě pokud libovolné asynchronní operace selže, všechny výjimky začlení do <xref:System.AggregateException> výjimku, která je uložena v <xref:System.Threading.Tasks.Task> , který je vrácen z <xref:System.Threading.Tasks.Task.WhenAll%2A> – metoda.</span><span class="sxs-lookup"><span data-stu-id="980da-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="980da-180">Ale pouze jeden z těchto výjimek distribuovány `await` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="980da-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="980da-181">Pokud chcete prozkoumat všechny výjimky, můžete předchozí kód přepsat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="980da-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="980da-182">Zvažte následující příklad asynchronní stahování více souborů z webu.</span><span class="sxs-lookup"><span data-stu-id="980da-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="980da-183">V tomto případě mají typy homogenní výsledků asynchronních operací a snadno přistupovat k výsledkům:</span><span class="sxs-lookup"><span data-stu-id="980da-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="980da-184">Můžete použít stejné techniky zpracování výjimek, které jsme probrali v předchozím scénáři vracející typ void:</span><span class="sxs-lookup"><span data-stu-id="980da-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

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

### <a name="taskwhenany"></a><span data-ttu-id="980da-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="980da-185">Task.WhenAny</span></span>
 <span data-ttu-id="980da-186">Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metody asynchronně čekat pouze jedna z více asynchronních operací reprezentovaná jako úkoly k dokončení.</span><span class="sxs-lookup"><span data-stu-id="980da-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="980da-187">Tato metoda má čtyři hlavní případy použití:</span><span class="sxs-lookup"><span data-stu-id="980da-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="980da-188">Redundance:  Provedení operace, více než jednou a vyberte ten, který dokončí první (například kontaktování více akcií webové služby, které vytvoří jeden výsledek a vybere, která se dokončí nejrychlejší z nich).</span><span class="sxs-lookup"><span data-stu-id="980da-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="980da-189">Prokládání:  Spuštění více operací a čeká na všechny z nich k dokončení, ale jejich zpracování po dokončení.</span><span class="sxs-lookup"><span data-stu-id="980da-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="980da-190">Omezení šířky pásma:  Povolení zahájíte ostatní dokončení dalších operací.</span><span class="sxs-lookup"><span data-stu-id="980da-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="980da-191">Toto je rozšíření interleaving scénáře.</span><span class="sxs-lookup"><span data-stu-id="980da-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="980da-192">Časná bailout:  Například operace reprezentována t1 úlohy mohou být seskupeny do <xref:System.Threading.Tasks.Task.WhenAny%2A> úloha s jinou t2 úloh a může čekat <xref:System.Threading.Tasks.Task.WhenAny%2A> úloh.</span><span class="sxs-lookup"><span data-stu-id="980da-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="980da-193">Úloha t2 by mohly představovat vypršení časového limitu nebo zrušení nebo některé jiné signál, který způsobí, že <xref:System.Threading.Tasks.Task.WhenAny%2A> úlohy dokončení před dokončením t1.</span><span class="sxs-lookup"><span data-stu-id="980da-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="980da-194">Redundance</span><span class="sxs-lookup"><span data-stu-id="980da-194">Redundancy</span></span>
 <span data-ttu-id="980da-195">Představte si případ, ve které chcete rozhodnutí o tom, jestli si chcete koupit stejných akcií.</span><span class="sxs-lookup"><span data-stu-id="980da-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="980da-196">Existuje několik doporučení základní webové služby, kterým důvěřujete, ale v závislosti na denní zatížení, každá služba skončit se pomalé v různých časech.</span><span class="sxs-lookup"><span data-stu-id="980da-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="980da-197">Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metodu pro příjem oznámení po dokončení všechny operace:</span><span class="sxs-lookup"><span data-stu-id="980da-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="980da-198">Na rozdíl od <xref:System.Threading.Tasks.Task.WhenAll%2A>, která vrací rozbalení výsledcích všechny úlohy, které se nedokončil úspěšně, <xref:System.Threading.Tasks.Task.WhenAny%2A> vrátí úkol, který byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="980da-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="980da-199">Pokud se úkol nezdaří, je důležité vědět, že se nepovedlo, a pokud úkol proběhne úspěšně, je důležité vědět, který úkol vrácená hodnota je přidružena.</span><span class="sxs-lookup"><span data-stu-id="980da-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="980da-200">Proto potřebujete přístup k výsledku vrácené úlohy nebo další await, jak ukazuje tento příklad.</span><span class="sxs-lookup"><span data-stu-id="980da-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="980da-201">Stejně jako u <xref:System.Threading.Tasks.Task.WhenAll%2A>, budete muset být schopni nastavit výjimky.</span><span class="sxs-lookup"><span data-stu-id="980da-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="980da-202">Vzhledem k tomu, že se zobrazí dokončené úlohy, můžete očekávat Vrácená úloha šíří, chyby se a `try/catch` je odpovídajícím způsobem; například:</span><span class="sxs-lookup"><span data-stu-id="980da-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="980da-203">Kromě toho i v případě, že první úloha úspěšně dokončí, následné úlohy může selhat.</span><span class="sxs-lookup"><span data-stu-id="980da-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="980da-204">V tomto okamžiku máte několik možností pro nakládání s výjimkami:  Můžete počkat, dokud nebyly dokončeny všechny spuštěné úlohy, v takovém případě můžete použít <xref:System.Threading.Tasks.Task.WhenAll%2A> metodu, nebo můžete rozhodnout, že všechny výjimky jsou důležité a musíte být přihlášeni.</span><span class="sxs-lookup"><span data-stu-id="980da-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="980da-205">V takovém případě můžete použít pokračování pro příjem oznámení po dokončení asynchronní úlohy:</span><span class="sxs-lookup"><span data-stu-id="980da-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="980da-206">nebo:</span><span class="sxs-lookup"><span data-stu-id="980da-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="980da-207">nebo dokonce:</span><span class="sxs-lookup"><span data-stu-id="980da-207">or even:</span></span>

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

 <span data-ttu-id="980da-208">Nakonec můžete chtít zrušení zbývajících operací:</span><span class="sxs-lookup"><span data-stu-id="980da-208">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="980da-209">Prokládání</span><span class="sxs-lookup"><span data-stu-id="980da-209">Interleaving</span></span>
 <span data-ttu-id="980da-210">Představte si případ, ve kterém jste stahování imagí z webu a zpracování každé bitové kopie (například přidání image do ovládacího prvku uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="980da-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="980da-211">Je nutné provést zpracování postupně ve vlákně uživatelského rozhraní, ale chcete stáhnout Image jako současně.</span><span class="sxs-lookup"><span data-stu-id="980da-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="980da-212">Navíc není nutné zdržet přidávání obrázků na uživatelské rozhraní, dokud se všechny stáhnou, které chcete přidat, je po dokončení:</span><span class="sxs-lookup"><span data-stu-id="980da-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

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

 <span data-ttu-id="980da-213">Můžete také použít prokládání scénář, který zahrnuje výpočetně náročné na zpracování na <xref:System.Threading.ThreadPool> stažený imagí, třeba:</span><span class="sxs-lookup"><span data-stu-id="980da-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="980da-214">Omezování</span><span class="sxs-lookup"><span data-stu-id="980da-214">Throttling</span></span>
 <span data-ttu-id="980da-215">Podívejte se na příklad interleaving s tím rozdílem, že uživatel stahuje tolik obrázky, soubory ke stažení jsou potřeba k omezení; například chcete jenom určitý počet stažení probíhají souběžně.</span><span class="sxs-lookup"><span data-stu-id="980da-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="980da-216">Za tím účelem můžete spustit podmnožinu asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="980da-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="980da-217">Dokončení operace, můžete spustit další operace k provedení jejich:</span><span class="sxs-lookup"><span data-stu-id="980da-217">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="980da-218">Časná Bailout</span><span class="sxs-lookup"><span data-stu-id="980da-218">Early Bailout</span></span>
 <span data-ttu-id="980da-219">Vezměte v úvahu, že čekáte asynchronní operaci dokončit během současně reakce na žádosti o zrušení uživatele (například uživatel klikl na tlačítko Storno).</span><span class="sxs-lookup"><span data-stu-id="980da-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="980da-220">Následující kód ukazuje tento scénář:</span><span class="sxs-lookup"><span data-stu-id="980da-220">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="980da-221">Tato implementace znovu povolí uživatelského rozhraní, co nejdříve, rozhodněte, do nichž navýšení kapacity, ale nezruší základní asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="980da-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="980da-222">Jinou alternativou by také bylo zrušení čekající operace při rozhodování, na nichž navýšení kapacity, ale ne znovu vytvořit uživatelské rozhraní až dokončíte, potenciálně z důvodu ukončení již v rané fázi kvůli žádost o zrušení operace:</span><span class="sxs-lookup"><span data-stu-id="980da-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="980da-223">Další příklad předčasné bailout zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> způsob, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="980da-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="980da-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="980da-224">Task.Delay</span></span>
 <span data-ttu-id="980da-225">Můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda zavést pozastaví do spuštění asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="980da-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="980da-226">To je užitečné pro různé druhy funkce, včetně vytváření smyčky cyklického dotazování a zpracování vstupu uživatele na předem určenou dobu zpoždění.</span><span class="sxs-lookup"><span data-stu-id="980da-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="980da-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda může být také užitečné v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementace vypršení časových limitů pro čeká.</span><span class="sxs-lookup"><span data-stu-id="980da-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="980da-228">Pokud úloha, která je součástí větší asynchronní operace (například webovou službu ASP.NET) trvá moc dlouho, může celkovou operaci dochází, zejména v případě, že ji nebude možné nikdy dokončení.</span><span class="sxs-lookup"><span data-stu-id="980da-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="980da-229">Z tohoto důvodu je důležité mít možnost vypršení časového limitu při čekání na asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="980da-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="980da-230">Synchronní <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnot časového limitu, ale odpovídající <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedených <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>metody tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="980da-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="980da-231">Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> společně k implementaci vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="980da-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="980da-232">Například v uživatelském rozhraní aplikace, Řekněme, že chcete stáhnout bitovou kopii a zakázat uživatelské rozhraní během stahování image.</span><span class="sxs-lookup"><span data-stu-id="980da-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="980da-233">Nicméně pokud stahování trvá příliš dlouho, chcete znovu povolit uživatelské rozhraní a zrušit stahování:</span><span class="sxs-lookup"><span data-stu-id="980da-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="980da-234">Totéž platí i pro více souborů ke stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úlohu:</span><span class="sxs-lookup"><span data-stu-id="980da-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="980da-235">Vytváření Combinators založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="980da-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="980da-236">Protože úloha je zcela představuje asynchronní operaci a zadejte synchronní a asynchronní funkce pro propojení s operací, načítání jeho výsledky a tak dále, můžete vytvářet užitečné knihovny combinators, které tvoří úkoly Vytvářejte větší vzory.</span><span class="sxs-lookup"><span data-stu-id="980da-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="980da-237">Jak je popsáno v předchozí části, rozhraní .NET Framework obsahuje několik předdefinovaných combinators, ale můžete také vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="980da-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="980da-238">Následující části obsahují několik příkladů potenciální Startup v rámci combinatoru metody a typy.</span><span class="sxs-lookup"><span data-stu-id="980da-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="980da-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="980da-239">RetryOnFault</span></span>
 <span data-ttu-id="980da-240">V mnoha případech můžete chtít opakovat operace, pokud se předchozí pokus nezdaří.</span><span class="sxs-lookup"><span data-stu-id="980da-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="980da-241">Pro synchronní kód může vytvářet Pomocná metoda, jako `RetryOnFault` v následujícím příkladu, jak toho dosáhnout:</span><span class="sxs-lookup"><span data-stu-id="980da-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="980da-242">Můžete vytvořit metodu téměř identické pomocné rutiny pro asynchronní operace, které jsou implementovány klepnutím a proto vrací úlohy:</span><span class="sxs-lookup"><span data-stu-id="980da-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="980da-243">Potom můžete tento Startup v rámci combinatoru má kódovat do vaší aplikace logiky; opakovaných pokusů Příklad:</span><span class="sxs-lookup"><span data-stu-id="980da-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="980da-244">Můžete rozšířit `RetryOnFault` dále fungovat.</span><span class="sxs-lookup"><span data-stu-id="980da-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="980da-245">Například funkce by mohl přijmout jiný `Func<Task>` , který bude vyvolán mezi opakovanými pokusy o určení toho, kdy to zkuste znovu; například:</span><span class="sxs-lookup"><span data-stu-id="980da-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="980da-246">Můžete pak použít funkci následujícím způsobem čekat před opakováním operace sekundy:</span><span class="sxs-lookup"><span data-stu-id="980da-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="980da-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="980da-247">NeedOnlyOne</span></span>
 <span data-ttu-id="980da-248">V některých případech můžete využít redundance zvýšit pravděpodobnost úspěchu a latence operace.</span><span class="sxs-lookup"><span data-stu-id="980da-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="980da-249">Vezměte v úvahu několik webových služeb, které poskytují akcií, ale v různých časech dne, každá služba může poskytovat různé úrovně kvality a doby odezvy.</span><span class="sxs-lookup"><span data-stu-id="980da-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="980da-250">Výkyvy řešit, můžete vydávání požadavků na webové služby a co nejdříve získat odpověď z jednoho, zrušení zbývajících požadavků.</span><span class="sxs-lookup"><span data-stu-id="980da-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="980da-251">Pomocná funkce, aby bylo snazší implementace tohoto společného modelu spuštění více operací, čeká na všechny a pak zrušení zbývajících můžete implementovat.</span><span class="sxs-lookup"><span data-stu-id="980da-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="980da-252">`NeedOnlyOne` Tento scénář znázorňuje funkce v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="980da-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="980da-253">Potom můžete tuto funkci použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="980da-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="980da-254">Prokládané operace</span><span class="sxs-lookup"><span data-stu-id="980da-254">Interleaved Operations</span></span>
 <span data-ttu-id="980da-255">Není možný problém s výkonem s použitím <xref:System.Threading.Tasks.Task.WhenAny%2A> metody pro podporu interleaving scénáře, když pracujete s velmi velké sady úloh.</span><span class="sxs-lookup"><span data-stu-id="980da-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="980da-256">Všechna volání <xref:System.Threading.Tasks.Task.WhenAny%2A> výsledkem byla registrovaná u každého úkolu pokračování.</span><span class="sxs-lookup"><span data-stu-id="980da-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="980da-257">N počet úloh v důsledku O(N2) pokračování vytvořené během životního cyklu interleaving operace.</span><span class="sxs-lookup"><span data-stu-id="980da-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="980da-258">Pokud pracujete s rozsáhlou sadou úkolů, můžete použít kombinátorem (`Interleaved` v následujícím příkladu) Chcete-li vyřešit tyto problémy s výkonem:</span><span class="sxs-lookup"><span data-stu-id="980da-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="980da-259">Startup v rámci combinatoru pak můžete použít ke zpracování výsledků úloh po dokončení; Příklad:</span><span class="sxs-lookup"><span data-stu-id="980da-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="980da-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="980da-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="980da-261">V některých scénářích bodový/shromažďování může být vhodné čekat pro všechny úkoly v sadě, pokud jeden z těchto chyb, v takovém případě chcete ukončit čekání, jakmile dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="980da-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="980da-262">Můžete provést, která pomocí metody Startup v rámci combinatoru například `WhenAllOrFirstException` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="980da-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="980da-263">Vytváření založené na úlohách datové struktury</span><span class="sxs-lookup"><span data-stu-id="980da-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="980da-264">Kromě možnosti vytvářet combinators vlastních založené na úlohách, že máte datové struktury v <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> , která představuje výsledky asynchronní operace a nezbytné synchronizace k připojení s ním umožňuje velmi efektivní Zadejte, na kterém můžete vytvořit vlastní datové struktury pro použití v asynchronní scénáře.</span><span class="sxs-lookup"><span data-stu-id="980da-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="980da-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="980da-265">AsyncCache</span></span>
 <span data-ttu-id="980da-266">Jeden důležitý aspekt jazyka úkolu je, že může být předat pro několik příjemců, které může await jeho pokračování registr s ním, získat její výsledek nebo výjimky (v případě třídy <xref:System.Threading.Tasks.Task%601>), a tak dále.</span><span class="sxs-lookup"><span data-stu-id="980da-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="980da-267">Díky tomu <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> dokonale hodí pro použití v asynchronním infrastrukturu ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="980da-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="980da-268">Tady je příklad malé, ale výkonné asynchronní mezipaměť postavený na <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="980da-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="980da-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) třídy přijímá jako konstruktoru delegáta funkce, která přijímá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="980da-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="980da-270">Všechny dříve využívaných hodnoty z mezipaměti jsou uloženy v interní slovník a `AsyncCache` zajišťuje, aby pouze jeden úkol, je vygenerována pro klíč, i v případě, že mezipaměť je k ní přistupovat zároveň.</span><span class="sxs-lookup"><span data-stu-id="980da-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="980da-271">Můžete například vytvořit mezipaměť pro stažené webové stránky:</span><span class="sxs-lookup"><span data-stu-id="980da-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="980da-272">Potom můžete tuto mezipaměť v asynchronních metodách pokaždé, když je třeba obsah na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="980da-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="980da-273">`AsyncCache` Třídy zajistí, že při stahování co nejméně stránky jako možné a mezipamětí výsledky.</span><span class="sxs-lookup"><span data-stu-id="980da-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

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

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="980da-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="980da-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="980da-275">Úlohy můžete použít také k vytváření datových struktur pro koordinaci asynchronních aktivitách.</span><span class="sxs-lookup"><span data-stu-id="980da-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="980da-276">Vezměte v úvahu jednomu ze vzorů návrhu classic paralelní: producenta/konzumenta.</span><span class="sxs-lookup"><span data-stu-id="980da-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="980da-277">V tomto vzoru výrobci generují data, která je využívána spotřebitelů a producenti a spotřebitelé můžou běžet paralelně.</span><span class="sxs-lookup"><span data-stu-id="980da-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="980da-278">Například příjemce zpracovává položka 1, který byl dříve vytvořen výrobce, který je teď vytváření položka 2.</span><span class="sxs-lookup"><span data-stu-id="980da-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="980da-279">Pro producenta/konzumenta najdete vzorek musíte vždy některé struktura dat pro uložení práce vytvořené výrobců tak, aby spotřebitelé být upozorněni na nová data a najít, když je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="980da-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="980da-280">Tady je jednoduchý datová struktura postavené na úlohy, která umožňuje asynchronní metody, které se použijí jako producenti a spotřebitelé:</span><span class="sxs-lookup"><span data-stu-id="980da-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="980da-281">Pomocí této datové struktury v místě můžete napsat kód například následující:</span><span class="sxs-lookup"><span data-stu-id="980da-281">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="980da-282"><xref:System.Threading.Tasks.Dataflow> Obor názvů obsahuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, který můžete použít podobným způsobem, aniž by bylo potřeba vytvářet vlastní typ kolekce:</span><span class="sxs-lookup"><span data-stu-id="980da-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="980da-283"><xref:System.Threading.Tasks.Dataflow> Obor názvů je k dispozici v rozhraní .NET Framework 4.5 prostřednictvím **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="980da-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="980da-284">Chcete-li nainstalovat sestavení, které obsahuje <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v sadě Visual Studio, zvolte **spravovat balíčky NuGet** z nabídky projekt a vyhledejte online balíček Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="980da-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="980da-285">Viz také:</span><span class="sxs-lookup"><span data-stu-id="980da-285">See also</span></span>

- [<span data-ttu-id="980da-286">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="980da-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="980da-287">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="980da-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="980da-288">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="980da-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
