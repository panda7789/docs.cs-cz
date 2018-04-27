---
title: Použití asynchronního vzoru založeného na úloze
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb1b73af4ccdc22e811988450824123c0055d9e6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="2d580-102">Použití asynchronního vzoru založeného na úloze</span><span class="sxs-lookup"><span data-stu-id="2d580-102">Consuming the Task-based Asynchronous Pattern</span></span>
<span data-ttu-id="2d580-103">Použijete-li pracovat s asynchronních operací založený na úlohách asynchronní vzor (TAP), můžete dosáhnout čekání bez blokování zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="2d580-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="2d580-104">Pro úlohy, můžete toho dosáhnout pomocí metody, jako <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d580-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d580-105">Na základě jazyka asynchronní podpora skryje tím, že asynchronních operací, která se v rámci normálního toku řízení očekávaná zpětná volání a generované kompilátorem kódu poskytuje tato podpora stejnou úroveň rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="2d580-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>  
  
## <a name="suspending-execution-with-await"></a><span data-ttu-id="2d580-106">Pozastavení provádění s Await</span><span class="sxs-lookup"><span data-stu-id="2d580-106">Suspending Execution with Await</span></span>  
 <span data-ttu-id="2d580-107">Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete použít [await](~/docs/csharp/language-reference/keywords/await.md) – klíčové slovo v jazyce C# a [Await – operátor](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic pro asynchronně await <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty.</span><span class="sxs-lookup"><span data-stu-id="2d580-107">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="2d580-108">Když se čeká na <xref:System.Threading.Tasks.Task>, `await` výraz je typu `void`.</span><span class="sxs-lookup"><span data-stu-id="2d580-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="2d580-109">Když se čeká na <xref:System.Threading.Tasks.Task%601>, `await` výraz je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="2d580-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="2d580-110">`await` Výraz musí dojít k uvnitř těla asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d580-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="2d580-111">Další informace o jazyka C# a Visual Basic podporují v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], najdete v části specifikace jazyka C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d580-111">For more information about C# and Visual Basic language support in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see the C# and Visual Basic language specifications.</span></span>  
  
 <span data-ttu-id="2d580-112">V pozadí nainstaluje funkci await pomocí pokračování v úloze zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="2d580-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="2d580-113">Tato zpětného volání obnoví asynchronní metody v místě pozastavení.</span><span class="sxs-lookup"><span data-stu-id="2d580-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="2d580-114">Když je obnoveno asynchronní metody, pokud awaited operace byla úspěšně dokončena a byla <xref:System.Threading.Tasks.Task%601>, jeho `TResult` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="2d580-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="2d580-115">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , očekávaná skončila v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, <xref:System.OperationCanceledException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2d580-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="2d580-116">Pokud <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , očekávaná skončila v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu, je vyvolána výjimka, který způsobuje její poruch.</span><span class="sxs-lookup"><span data-stu-id="2d580-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="2d580-117">A `Task` můžete selhání v důsledku několik výjimek, ale pouze jeden z těchto výjimek rozšířena.</span><span class="sxs-lookup"><span data-stu-id="2d580-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="2d580-118">Ale <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.AggregateException> výjimka, která obsahuje všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="2d580-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>  
  
 <span data-ttu-id="2d580-119">Pokud kontext synchronizace (<xref:System.Threading.SynchronizationContext> objektu) souvisí s podproces, který byl v době pozastavení provádění asynchronní metody (například pokud <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> vlastnost není `null`), asynchronní metoda obnoví na který stejný kontext synchronizace pomocí podle kontextu <xref:System.Threading.SynchronizationContext.Post%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2d580-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="2d580-120">Jinak je závislé na plánovače úloh (<xref:System.Threading.Tasks.TaskScheduler> objektu), který byl aktuální v době pozastavení.</span><span class="sxs-lookup"><span data-stu-id="2d580-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="2d580-121">Obvykle je to výchozí plánovače úloh (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), které cílí fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="2d580-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="2d580-122">Tato služba Plánovač úloh Určuje, zda by měl awaited asynchronní operace pokračovat, kde byla dokončena nebo jestli má být naplánováno obnovení.</span><span class="sxs-lookup"><span data-stu-id="2d580-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="2d580-123">Scheduler výchozí obvykle umožní pokračování ke spuštění na vlákno, které awaited operaci dokončit.</span><span class="sxs-lookup"><span data-stu-id="2d580-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>  
  
 <span data-ttu-id="2d580-124">Při volání asynchronní metody, se tělo funkce synchronně provede, dokud první await výrazu v případě může používat await instance, který ještě nebyl dokončen, v tomto okamžiku se volání vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2d580-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="2d580-125">Pokud lze asynchronní metodu nevrátí `void`, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> se vrátí objekt představující probíhající výpočet.</span><span class="sxs-lookup"><span data-stu-id="2d580-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="2d580-126">V jiných void asynchronní metody, pokud je příkaz return zaznamenána nebo je dosaženo konce metoda textu, dokončení úlohy v <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> konečného stavu.</span><span class="sxs-lookup"><span data-stu-id="2d580-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="2d580-127">Pokud k neošetřené výjimce způsobí, že ovládací prvek chcete nechat těla asynchronní metody, úloha končí v <xref:System.Threading.Tasks.TaskStatus.Faulted> stavu.</span><span class="sxs-lookup"><span data-stu-id="2d580-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="2d580-128">Pokud je této výjimky <xref:System.OperationCanceledException>, úloha místo končí v <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.</span><span class="sxs-lookup"><span data-stu-id="2d580-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="2d580-129">Tímto způsobem výsledek nebo výjimky se nakonec publikuje.</span><span class="sxs-lookup"><span data-stu-id="2d580-129">In this manner, the result or exception is eventually published.</span></span>  
  
 <span data-ttu-id="2d580-130">Existuje několik důležitých variant toto chování.</span><span class="sxs-lookup"><span data-stu-id="2d580-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="2d580-131">Z důvodů výkonu Pokud úloha již byla dokončena v čase je očekáváno úlohu, není poskytuje ovládací prvek a funkce bude pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="2d580-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="2d580-132">Kromě toho vrácením původní kontextu není vždy požadované chování a může být změněn; To je podrobně popsaná v další v další části.</span><span class="sxs-lookup"><span data-stu-id="2d580-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="2d580-133">Pozastavení a obnovení nakonfigurování Yield a ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="2d580-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>  
 <span data-ttu-id="2d580-134">Existuje několik metod poskytuje větší kontrolu nad spuštění asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d580-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="2d580-135">Například můžete použít <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metoda zavést bod yield do asynchronní metody:</span><span class="sxs-lookup"><span data-stu-id="2d580-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 <span data-ttu-id="2d580-136">Jde o ekvivalent asynchronně publikování nebo plánování zpět do aktuálního kontextu.</span><span class="sxs-lookup"><span data-stu-id="2d580-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>  
  
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
  
 <span data-ttu-id="2d580-137">Můžete také <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodu pro lepší kontrolu nad pozastavení a obnovení v asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="2d580-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="2d580-138">Jak je uvedeno nahoře, ve výchozím nastavení, je aktuální kontext zachycen v době, kdy je pozastaveno asynchronní metodu a že zaznamenané kontextu je použito k volání asynchronní metody pokračování po obnovení.</span><span class="sxs-lookup"><span data-stu-id="2d580-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="2d580-139">V mnoha případech je to přesné chování, které chcete.</span><span class="sxs-lookup"><span data-stu-id="2d580-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="2d580-140">V ostatních případech nemusí se zajímáte o pokračování kontextu a lepšího výkonu můžete dosáhnout vyhnout těchto příspěvcích zpět do původní kontextu.</span><span class="sxs-lookup"><span data-stu-id="2d580-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="2d580-141">Chcete-li povolit, použijte <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metoda informovat await operaci není k zaznamenání a obnovení v kontextu, ale pro pokračování v provádění bez ohledu na dokončení asynchronní operaci, která se očekávaná:</span><span class="sxs-lookup"><span data-stu-id="2d580-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="2d580-142">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="2d580-142">Canceling an Asynchronous Operation</span></span>  
 <span data-ttu-id="2d580-143">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], klepněte na metody, které podporují zrušení zadejte alespoň jeden přetížení, která přijímá token zrušení (<xref:System.Threading.CancellationToken> objekt).</span><span class="sxs-lookup"><span data-stu-id="2d580-143">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>  
  
 <span data-ttu-id="2d580-144">Token zrušení je vytvořena prostřednictvím zdroj tokenu zrušení (<xref:System.Threading.CancellationTokenSource> objekt).</span><span class="sxs-lookup"><span data-stu-id="2d580-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="2d580-145">Zdrojovém <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost vrací token zrušení, který bude signál při zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="2d580-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="2d580-146">Například pokud chcete stáhnout jedné webové stránky a chcete být schopni zrušte operaci, vytvoříte <xref:System.Threading.CancellationTokenSource> objektu, předat klepněte na metoda jeho token a pak zavolají zdroj <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda až budete připraveni na tlačítko Storno:</span><span class="sxs-lookup"><span data-stu-id="2d580-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 <span data-ttu-id="2d580-147">Pokud chcete zrušit více asynchronní volání, můžete předat stejný token do všech volání:</span><span class="sxs-lookup"><span data-stu-id="2d580-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 <span data-ttu-id="2d580-148">Nebo můžete předat stejný token do podmnožinu selektivní operací:</span><span class="sxs-lookup"><span data-stu-id="2d580-148">Or, you can pass the same token to a selective subset of operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 <span data-ttu-id="2d580-149">Zrušení žádosti může být zahájen z libovolného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d580-149">Cancellation requests may be initiated from any thread.</span></span>  
  
 <span data-ttu-id="2d580-150">Můžete předat <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> hodnotu libovolné metody, která přijímá token zrušení pro znamenat, že bude nikdy vyžádána zrušení.</span><span class="sxs-lookup"><span data-stu-id="2d580-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="2d580-151">To způsobí, že <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> vlastnost vrátit `false`, a zavolat metodu můžete optimalizovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="2d580-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="2d580-152">Pro účely testování můžete předat také v předem zrušené zrušení token, který je vytvořena instance pomocí konstruktor, který přijímá logickou hodnotu označující, zda je token by se měl spustit ve stavu již zrušena nebo možné zrušit není.</span><span class="sxs-lookup"><span data-stu-id="2d580-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>  
  
 <span data-ttu-id="2d580-153">Tento přístup k zrušení má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="2d580-153">This approach to cancellation has several advantages:</span></span>  
  
-   <span data-ttu-id="2d580-154">Stejný token zrušení můžete předat libovolný počet synchronní a asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="2d580-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>  
  
-   <span data-ttu-id="2d580-155">Stejné žádost o zrušení může být proliferated na libovolný počet naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="2d580-155">The same cancellation request may be proliferated to any number of listeners.</span></span>  
  
-   <span data-ttu-id="2d580-156">Vývojář asynchronní rozhraní API je v úplnou kontrolu, zda mohou být vyžádány zrušení a kdy může trvat vliv.</span><span class="sxs-lookup"><span data-stu-id="2d580-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>  
  
-   <span data-ttu-id="2d580-157">Kód, který využívá rozhraní API může určit selektivně asynchronní volání, které požadavky zrušení se rozšíří do.</span><span class="sxs-lookup"><span data-stu-id="2d580-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>  
  
## <a name="monitoring-progress"></a><span data-ttu-id="2d580-158">Sledování průběhu</span><span class="sxs-lookup"><span data-stu-id="2d580-158">Monitoring Progress</span></span>  
 <span data-ttu-id="2d580-159">Některé asynchronní metody vystavit probíhá přes rozhraní průběh předané do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d580-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="2d580-160">Zvažte například, že funkci, která asynchronně stáhne řetězec textu a cestou se vyvolá průběh aktualizace, které zahrnují procento ke stažení, které doposud dokončeno.</span><span class="sxs-lookup"><span data-stu-id="2d580-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="2d580-161">Tato metoda by mohly spotřebovat v aplikaci Windows Presentation Foundation (WPF) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2d580-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>  
  
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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="2d580-162">Pomocí předdefinovaných Combinators založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="2d580-162">Using the Built-in Task-based Combinators</span></span>  
 <span data-ttu-id="2d580-163"><xref:System.Threading.Tasks> Obor názvů obsahuje několik metod pro vytváření a práci s úlohami.</span><span class="sxs-lookup"><span data-stu-id="2d580-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>  
  
### <a name="taskrun"></a><span data-ttu-id="2d580-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="2d580-164">Task.Run</span></span>  
 <span data-ttu-id="2d580-165"><xref:System.Threading.Tasks.Task> Třída obsahuje několik <xref:System.Threading.Tasks.Task.Run%2A> metody, které vám umožní snadno snižování zátěže work jako <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> fond vláken, např.:</span><span class="sxs-lookup"><span data-stu-id="2d580-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>  
  
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
  
 <span data-ttu-id="2d580-166">Některé z těchto <xref:System.Threading.Tasks.Task.Run%2A> metody, jako <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> přetížení, existovat jako sdružená vlastnost <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="2d580-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="2d580-167">Jiné přetížení, jako například <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, povolit použití await v rámci sníženou zátěží práce, například:</span><span class="sxs-lookup"><span data-stu-id="2d580-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>  
  
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
  
 <span data-ttu-id="2d580-168">Takové přetížení jsou logicky ekvivalentní použití <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda ve spojení s <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metoda rozšíření v knihovně Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="2d580-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>  
  
### <a name="taskfromresult"></a><span data-ttu-id="2d580-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="2d580-169">Task.FromResult</span></span>  
 <span data-ttu-id="2d580-170">Použití <xref:System.Threading.Tasks.Task.FromResult%2A> musí být vrácená metodou vracející úloh zrušeno do metoda ve scénářích, kde data mohou již být k dispozici, jenom <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="2d580-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
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
  
### <a name="taskwhenall"></a><span data-ttu-id="2d580-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="2d580-171">Task.WhenAll</span></span>  
 <span data-ttu-id="2d580-172">Použití <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda asynchronně čekání na více asynchronních operací, které jsou reprezentovány jako úlohy.</span><span class="sxs-lookup"><span data-stu-id="2d580-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="2d580-173">Metoda má několik přetížení, která podporují sadu neobecnou úloh nebo neuniformní sadu obecné úlohy (například asynchronně čekání pro více operací void vrácení, nebo asynchronně čekání na více metod vrací hodnotu kde Každá hodnota může mít jiný typ) a k podpoře uniform sadu obecné úloh (například asynchronně čekání na více `TResult`-vrácení metody).</span><span class="sxs-lookup"><span data-stu-id="2d580-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>  
  
 <span data-ttu-id="2d580-174">Řekněme, že chcete poslat e-mailové zprávy několik zákazníků.</span><span class="sxs-lookup"><span data-stu-id="2d580-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="2d580-175">Můžete se překrývají, odesílání zpráv, takže nejsou čeká jednu zprávu dokončit před odesláním Další.</span><span class="sxs-lookup"><span data-stu-id="2d580-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="2d580-176">Můžete taky zjistit když byly dokončeny operace odesílání a jestli nedošlo k chybám:</span><span class="sxs-lookup"><span data-stu-id="2d580-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 <span data-ttu-id="2d580-177">Tento kód není explicitně zpracování výjimek, které může dojít, ale umožní šířit z výjimky `await` na výsledný úlohy ze <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d580-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="2d580-178">Pro zpracování výjimky, můžete použít například následující kód:</span><span class="sxs-lookup"><span data-stu-id="2d580-178">To handle the exceptions, you can use code such as the following:</span></span>  
  
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
  
 <span data-ttu-id="2d580-179">V takovém případě pokud všechny asynchronní operace selže, všechny výjimky se mají konsolidovat v <xref:System.AggregateException> výjimka, která je uložena v <xref:System.Threading.Tasks.Task> , je vrácena z <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2d580-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="2d580-180">Ale pouze jeden z těchto výjimek rozšířit pomocí `await` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2d580-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="2d580-181">Pokud chcete prozkoumejte všechny výjimky, je možné přepsat předchozí kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2d580-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>  
  
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
  
 <span data-ttu-id="2d580-182">Zvažte příklad asynchronně stahování více souborů z webu.</span><span class="sxs-lookup"><span data-stu-id="2d580-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="2d580-183">V takovém případě všechny asynchronní operace mají typy homogenní výsledků a je snadno dostupné výsledky:</span><span class="sxs-lookup"><span data-stu-id="2d580-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 <span data-ttu-id="2d580-184">Můžete použít stejné techniky zpracování výjimek, kterou jsme probírali v předchozím scénáři vrácení void:</span><span class="sxs-lookup"><span data-stu-id="2d580-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>  
  
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
  
### <a name="taskwhenany"></a><span data-ttu-id="2d580-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="2d580-185">Task.WhenAny</span></span>  
 <span data-ttu-id="2d580-186">Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda asynchronně čekání pouze jedním z několika asynchronních operací vyjádřené úlohy k dokončení.</span><span class="sxs-lookup"><span data-stu-id="2d580-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="2d580-187">Tato metoda slouží čtyři primární použití případech:</span><span class="sxs-lookup"><span data-stu-id="2d580-187">This method serves four primary use cases:</span></span>  
  
-   <span data-ttu-id="2d580-188">Redundance: Provádění operace několikrát a vyberte ten, který dokončí první (například kontaktování více akcií webové služby, které vytvoří jeden výsledek a vyberte ten, který dokončí nejrychlejší).</span><span class="sxs-lookup"><span data-stu-id="2d580-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>  
  
-   <span data-ttu-id="2d580-189">Prokládání: Spouštění více operací čekajících na jejich dokončení, ale jejich zpracování po dokončení.</span><span class="sxs-lookup"><span data-stu-id="2d580-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>  
  
-   <span data-ttu-id="2d580-190">Omezení šířky pásma: Povolení zahájíte ostatní dokončení dalších operací.</span><span class="sxs-lookup"><span data-stu-id="2d580-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="2d580-191">Toto je rozšíření interleaving scénáře.</span><span class="sxs-lookup"><span data-stu-id="2d580-191">This is an extension of the interleaving scenario.</span></span>  
  
-   <span data-ttu-id="2d580-192">Časná bailout: například operace reprezentována t1 úloh mohou být seskupeny do <xref:System.Threading.Tasks.Task.WhenAny%2A> úlohy s jinou t2 úloh a může čekat <xref:System.Threading.Tasks.Task.WhenAny%2A> úloh.</span><span class="sxs-lookup"><span data-stu-id="2d580-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="2d580-193">Úloha t2 by mohl představovat vypršení časového limitu nebo zrušení nebo jiných signál, který způsobuje, že <xref:System.Threading.Tasks.Task.WhenAny%2A> na dokončení před dokončením t1 úlohy.</span><span class="sxs-lookup"><span data-stu-id="2d580-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>  
  
#### <a name="redundancy"></a><span data-ttu-id="2d580-194">Redundance</span><span class="sxs-lookup"><span data-stu-id="2d580-194">Redundancy</span></span>  
 <span data-ttu-id="2d580-195">Představte si případ, kam chcete učinit rozhodnutí o tom, jestli koupit populace.</span><span class="sxs-lookup"><span data-stu-id="2d580-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="2d580-196">Existuje několik webových služeb uložených doporučení, kterým důvěřujete, avšak v závislosti na denní zatížení, můžou skončit se pomalé v různou dobu jednotlivých služeb.</span><span class="sxs-lookup"><span data-stu-id="2d580-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="2d580-197">Můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda pro příjem oznámení po dokončení všechny operace:</span><span class="sxs-lookup"><span data-stu-id="2d580-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>  
  
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
  
 <span data-ttu-id="2d580-198">Na rozdíl od <xref:System.Threading.Tasks.Task.WhenAll%2A>, která vrací všechny úkoly, které úspěšně dokončit, rozbalenou výsledky <xref:System.Threading.Tasks.Task.WhenAny%2A> vrátí úlohu, která byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="2d580-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="2d580-199">Pokud se úloha nezdaří, je důležité vědět, že se nezdařilo, a pokud úloha úspěšná, je důležité vědět, jaké úlohu vrácená hodnota je přidružen.</span><span class="sxs-lookup"><span data-stu-id="2d580-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="2d580-200">Proto musíte získat přístup výsledek vrácený úlohy, nebo další await, jak ukazuje tento příklad.</span><span class="sxs-lookup"><span data-stu-id="2d580-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>  
  
 <span data-ttu-id="2d580-201">Stejně jako u <xref:System.Threading.Tasks.Task.WhenAll%2A>, budete muset být schopni nastavit výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d580-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="2d580-202">Vzhledem k tomu, že se zobrazí zpět dokončené úlohy, můžete await vrácený úlohy chyby rozšíří, a `try/catch` je správně; například:</span><span class="sxs-lookup"><span data-stu-id="2d580-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>  
  
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
  
 <span data-ttu-id="2d580-203">Kromě toho i v případě, že první úloha skončí úspěšně, může selhat úlohy.</span><span class="sxs-lookup"><span data-stu-id="2d580-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="2d580-204">V tuto chvíli máte několik možností pro práci s výjimkami: můžete počkat, dokud všechny spuštěného úkoly dokončí, v takovém případě můžete použít <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda, nebo můžete rozhodnout, že všechny výjimky jsou důležité a musí být zaprotokolovány.</span><span class="sxs-lookup"><span data-stu-id="2d580-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="2d580-205">V takovém případě můžete použít pokračování pro příjem oznámení po dokončení úlohy asynchronně:</span><span class="sxs-lookup"><span data-stu-id="2d580-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 <span data-ttu-id="2d580-206">nebo:</span><span class="sxs-lookup"><span data-stu-id="2d580-206">or:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 <span data-ttu-id="2d580-207">nebo dokonce:</span><span class="sxs-lookup"><span data-stu-id="2d580-207">or even:</span></span>  
  
```  
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
  
 <span data-ttu-id="2d580-208">Nakonec můžete zrušit všechny zbývající operace:</span><span class="sxs-lookup"><span data-stu-id="2d580-208">Finally, you may want to cancel all the remaining operations:</span></span>  
  
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
  
#### <a name="interleaving"></a><span data-ttu-id="2d580-209">Prokládání</span><span class="sxs-lookup"><span data-stu-id="2d580-209">Interleaving</span></span>  
 <span data-ttu-id="2d580-210">Představte si případ, kdy jste z webu stažení bitové kopie a zpracování každé bitové kopie (například přidání bitovou kopii do ovládacího prvku uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="2d580-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="2d580-211">Je nutné provést zpracování postupně ve vlákně UI, ale chcete stáhnout bitové kopie jako současně.</span><span class="sxs-lookup"><span data-stu-id="2d580-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="2d580-212">Navíc nechcete pojmout až Přidání bitové kopie do uživatelského rozhraní, dokud se všechny stáhnou – chcete přidat, je po dokončení:</span><span class="sxs-lookup"><span data-stu-id="2d580-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>  
  
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
  
 <span data-ttu-id="2d580-213">Můžete taky použít prokládání pro scénář, který zahrnuje výpočetně intenzivní zpracování na <xref:System.Threading.ThreadPool> stažené bitových kopií; například:</span><span class="sxs-lookup"><span data-stu-id="2d580-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>  
  
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
  
#### <a name="throttling"></a><span data-ttu-id="2d580-214">Omezování</span><span class="sxs-lookup"><span data-stu-id="2d580-214">Throttling</span></span>  
 <span data-ttu-id="2d580-215">Podívejte se na příklad interleaving, s tím rozdílem, že uživatel stahuje mnoho bitové kopie, stahování jsou potřeba k omezeny; například, že chcete pouze konkrétní počet souborů ke stažení provést současně.</span><span class="sxs-lookup"><span data-stu-id="2d580-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="2d580-216">Jak toho docílit, můžete začít podmnožinu asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="2d580-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="2d580-217">Dokončení operace, můžete spustit další operace jejich proběhla:</span><span class="sxs-lookup"><span data-stu-id="2d580-217">As operations complete, you can start additional operations to take their place:</span></span>  
  
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
  
#### <a name="early-bailout"></a><span data-ttu-id="2d580-218">Časná Bailout</span><span class="sxs-lookup"><span data-stu-id="2d580-218">Early Bailout</span></span>  
 <span data-ttu-id="2d580-219">Zvažte, že čekáte asynchronně na dokončení při současně reakci na žádost uživatele zrušení operace (například uživatel kliknutí na tlačítko Storno).</span><span class="sxs-lookup"><span data-stu-id="2d580-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="2d580-220">Následující kód ukazuje tento scénář:</span><span class="sxs-lookup"><span data-stu-id="2d580-220">The following code illustrates this scenario:</span></span>  
  
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
  
 <span data-ttu-id="2d580-221">Tato implementace znovu povolí uživatelské rozhraní, při nichž rozhodnete, ale není zrušte základní asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="2d580-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="2d580-222">Další alternativou by zrušit čekající operace, pokud se rozhodnete nichž, ale není znovu vytvořit uživatelské rozhraní až ve skutečnosti dokončení potenciálně kvůli ukončuje již v rané fázi kvůli žádost o zrušení operace:</span><span class="sxs-lookup"><span data-stu-id="2d580-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>  
  
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
  
 <span data-ttu-id="2d580-223">Další příklad časná bailout zahrnuje použití <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda ve spojení s <xref:System.Threading.Tasks.Task.Delay%2A> metoda, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="2d580-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>  
  
### <a name="taskdelay"></a><span data-ttu-id="2d580-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="2d580-224">Task.Delay</span></span>  
 <span data-ttu-id="2d580-225">Můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda zavádět pozastaví do asynchronní metody spouštění.</span><span class="sxs-lookup"><span data-stu-id="2d580-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="2d580-226">To je užitečné pro různé druhy funkce, včetně vytváření dotazování smyčky a zpozdit zpracování vstupu uživatele předem určenou dobu.</span><span class="sxs-lookup"><span data-stu-id="2d580-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="2d580-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda také může být užitečná v kombinaci s <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pro implementace vypršení časových limitů na čeká.</span><span class="sxs-lookup"><span data-stu-id="2d580-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>  
  
 <span data-ttu-id="2d580-228">Pokud úloha, která je součástí větší asynchronní operace (například webové služby ASP.NET) trvá příliš dlouho dokončení, může celkové operace sníží, obzvláště pokud se nepodaří někdy dokončit.</span><span class="sxs-lookup"><span data-stu-id="2d580-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="2d580-229">Z tohoto důvodu je důležité, abyste mohli vypršení časového limitu při čekání na asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="2d580-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="2d580-230">Synchronní <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody přijímají hodnoty časového limitu, ale odpovídající <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> a výše uvedených <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>metody nepodporují.</span><span class="sxs-lookup"><span data-stu-id="2d580-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="2d580-231">Místo toho můžete použít <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> v kombinaci implementovat vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="2d580-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>  
  
 <span data-ttu-id="2d580-232">Například v aplikaci uživatelského rozhraní Řekněme, že chcete stáhnout bitovou kopii a zakázat uživatelské rozhraní během stahuje bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="2d580-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="2d580-233">Ale pokud stahování trvá příliš dlouho, chcete znovu zapnout uživatelského rozhraní a zrušení stahování:</span><span class="sxs-lookup"><span data-stu-id="2d580-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>  
  
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
  
 <span data-ttu-id="2d580-234">Totéž platí i pro více souborů ke stažení, protože <xref:System.Threading.Tasks.Task.WhenAll%2A> vrátí úlohu:</span><span class="sxs-lookup"><span data-stu-id="2d580-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>  
  
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
  
## <a name="building-task-based-combinators"></a><span data-ttu-id="2d580-235">Vytváření Combinators založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="2d580-235">Building Task-based Combinators</span></span>  
 <span data-ttu-id="2d580-236">Protože úloha je schopen úplně představují asynchronní operaci a zadejte možnosti synchronní a asynchronní pro připojení v operaci, načítání jeho výsledky a tak dále, můžete vytvořit užitečné knihovny combinators, které tvoří úloh sestavení větší vzory.</span><span class="sxs-lookup"><span data-stu-id="2d580-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="2d580-237">Jak je popsáno v předchozí části, rozhraní .NET Framework zahrnuje několik předdefinovaných combinators, ale můžete také vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="2d580-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="2d580-238">Následující části obsahují několik příkladů, potenciální kombinátorem metody a typy.</span><span class="sxs-lookup"><span data-stu-id="2d580-238">The following sections provide several examples of potential combinator methods and types.</span></span>  
  
### <a name="retryonfault"></a><span data-ttu-id="2d580-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="2d580-239">RetryOnFault</span></span>  
 <span data-ttu-id="2d580-240">V mnoha situacích můžete opakovat operace, pokud se předchozí pokus selže.</span><span class="sxs-lookup"><span data-stu-id="2d580-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="2d580-241">Pro synchronní kód, může sestavování Pomocná metoda, jako `RetryOnFault` v následujícím příkladu se:</span><span class="sxs-lookup"><span data-stu-id="2d580-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>  
  
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
  
 <span data-ttu-id="2d580-242">Můžete vytvořit téměř identický pomocnou metodu pro asynchronní operace, které jsou implementovány pomocí klepněte na a proto vrátí úlohy:</span><span class="sxs-lookup"><span data-stu-id="2d580-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>  
  
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
  
 <span data-ttu-id="2d580-243">Pak můžete toto kombinátorem ke kódování opakování do aplikace logiky; například:</span><span class="sxs-lookup"><span data-stu-id="2d580-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 <span data-ttu-id="2d580-244">Můžete rozšířit `RetryOnFault` další funkce.</span><span class="sxs-lookup"><span data-stu-id="2d580-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="2d580-245">Například funkce může přijímat jiné `Func<Task>` , který bude vyvolán mezi opakovanými pokusy k určení, kdy k akci znovu; například:</span><span class="sxs-lookup"><span data-stu-id="2d580-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>  
  
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
  
 <span data-ttu-id="2d580-246">Můžete potom použít funkci takto čekat před opakováním operace druhý:</span><span class="sxs-lookup"><span data-stu-id="2d580-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a><span data-ttu-id="2d580-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="2d580-247">NeedOnlyOne</span></span>  
 <span data-ttu-id="2d580-248">V některých případech můžete využít výhod redundance, aby zlepšit latenci a pravděpodobnost úspěchu operaci.</span><span class="sxs-lookup"><span data-stu-id="2d580-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="2d580-249">Vezměte v úvahu více webových služeb, které poskytují akcií, ale v různých časech dne, může každá služba poskytovat různé úrovně kvality a časy odezvy.</span><span class="sxs-lookup"><span data-stu-id="2d580-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="2d580-250">K řešení těchto kolísání, můžete vydat požadavky pro všechny webové služby a také získat odpověď z některého, zrušit zbývající žádosti.</span><span class="sxs-lookup"><span data-stu-id="2d580-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="2d580-251">Můžete implementovat pomocné funkce, aby bylo snazší implementovat tento běžný vzor spouštění více operací, čekání na všechny a pak zrušení zbytek.</span><span class="sxs-lookup"><span data-stu-id="2d580-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="2d580-252">`NeedOnlyOne` Tento scénář ukazuje funkce v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2d580-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>  
  
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
  
 <span data-ttu-id="2d580-253">Potom můžete tuto funkci použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2d580-253">You can then use this function as follows:</span></span>  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a><span data-ttu-id="2d580-254">Prokládaná operace</span><span class="sxs-lookup"><span data-stu-id="2d580-254">Interleaved Operations</span></span>  
 <span data-ttu-id="2d580-255">Došlo k potížím potenciální výkon pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda pro podporu interleaving scénář, když pracujete s velmi velkých sad úloh.</span><span class="sxs-lookup"><span data-stu-id="2d580-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="2d580-256">Každé volání <xref:System.Threading.Tasks.Task.WhenAny%2A> výsledkem pokračování registrované s každý úkol.</span><span class="sxs-lookup"><span data-stu-id="2d580-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="2d580-257">Pro N počet úloh výsledkem O(N2) pokračování vytvořit během životního cyklu interleaving operace.</span><span class="sxs-lookup"><span data-stu-id="2d580-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="2d580-258">Pokud pracujete s velké sadu úloh, můžete použít kombinátorem (`Interleaved` v následujícím příkladu) Chcete-li vyřešit problémy s výkonem:</span><span class="sxs-lookup"><span data-stu-id="2d580-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>  
  
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
  
 <span data-ttu-id="2d580-259">Potom můžete kombinátorem zpracování výsledků úloh po dokončení; například:</span><span class="sxs-lookup"><span data-stu-id="2d580-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a><span data-ttu-id="2d580-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="2d580-260">WhenAllOrFirstException</span></span>  
 <span data-ttu-id="2d580-261">V některých scénářích bodového nebo shromáždění můžete počkat, všechny úlohy v sadě, pokud jeden z nich chyb, v takovém případě chcete zastavit, čekání, jakmile dojde k výjimka.</span><span class="sxs-lookup"><span data-stu-id="2d580-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="2d580-262">Můžete provést, pomocí metody kombinátorem například `WhenAllOrFirstException` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2d580-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>  
  
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
  
## <a name="building-task-based-data-structures"></a><span data-ttu-id="2d580-263">Vytváření založený na úlohách datové struktury</span><span class="sxs-lookup"><span data-stu-id="2d580-263">Building Task-based Data Structures</span></span>  
 <span data-ttu-id="2d580-264">Kromě možnost vytváření vlastních combinators založený na úlohách, že datová struktura v <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> výsledky asynchronní operace, která představuje a potřeby synchronizace k připojení k němu umožňuje velmi efektivní Zadejte, na které se mají vytvářet vlastní datové struktury pro použití v asynchronní scénáře.</span><span class="sxs-lookup"><span data-stu-id="2d580-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>  
  
### <a name="asynccache"></a><span data-ttu-id="2d580-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="2d580-265">AsyncCache</span></span>  
 <span data-ttu-id="2d580-266">Jednou z důležitým aspektem úlohy je, že ho může možné předat službě více příjemcům, které může await ho zaregistrovat pokračování s ním, získat jeho výsledek nebo výjimky (u <xref:System.Threading.Tasks.Task%601>), a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2d580-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="2d580-267">Díky tomu <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> perfektně vhodná pro použití v infrastruktuře asynchronní ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2d580-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="2d580-268">Tady je příklad malá, ale výkonné asynchronní mezipaměť postavený na <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="2d580-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
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
  
 <span data-ttu-id="2d580-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) třída přijímá jako delegáta jeho konstruktoru funkce, která přebírá `TKey` a vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="2d580-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="2d580-270">Veškeré dříve používaná hodnoty z mezipaměti jsou uloženy ve slovníku interní a `AsyncCache` zajistí, aby pouze jeden úkol se vygeneruje pro klíč, i v případě, že mezipaměť přistupuje souběžně.</span><span class="sxs-lookup"><span data-stu-id="2d580-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>  
  
 <span data-ttu-id="2d580-271">Můžete například vytvořit mezipaměť pro stažené webové stránky:</span><span class="sxs-lookup"><span data-stu-id="2d580-271">For example, you can build a cache for downloaded web pages:</span></span>  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 <span data-ttu-id="2d580-272">Potom můžete tuto mezipaměť v asynchronních metod kdykoli budete potřebovat obsah na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="2d580-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="2d580-273">`AsyncCache` Třída zajistí, že při stahování co nejméně stránky jako možné a mezipaměti výsledky.</span><span class="sxs-lookup"><span data-stu-id="2d580-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="2d580-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="2d580-274">AsyncProducerConsumerCollection</span></span>  
 <span data-ttu-id="2d580-275">Úlohy můžete použít také k vytvoření datové struktury pro spolupráci asynchronní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2d580-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="2d580-276">Jedním ze vzorů classic paralelní návrhu zvažte: producent nebo příjemce.</span><span class="sxs-lookup"><span data-stu-id="2d580-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="2d580-277">V tomto vzoru producenti generování dat, která se využívá spotřebiteli a producenti a spotřebitelé může běží paralelně.</span><span class="sxs-lookup"><span data-stu-id="2d580-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="2d580-278">Například příjemce zpracovává položky 1, který byl dříve vygenerovat podle výrobce, který je nyní generovala položku 2.</span><span class="sxs-lookup"><span data-stu-id="2d580-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="2d580-279">Pro vzoru producent nebo příjemce je vždy nutné některé datovou strukturu pro ukládání pracovních vytvořené producenti tak, aby uživatelé být upozorněni na nová data a najít, když je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2d580-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>  
  
 <span data-ttu-id="2d580-280">Zde je jednoduchá datová struktura postavená na úlohy, která umožňuje asynchronní metody, které má být použit jako producenti a spotřebitelé:</span><span class="sxs-lookup"><span data-stu-id="2d580-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>  
  
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
  
 <span data-ttu-id="2d580-281">Pomocí této datové struktury v místě můžete napsat kód například následující:</span><span class="sxs-lookup"><span data-stu-id="2d580-281">With that data structure in place, you can write code such as the following:</span></span>  
  
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
  
 <span data-ttu-id="2d580-282"><xref:System.Threading.Tasks.Dataflow> Obor názvů zahrnuje <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typu, který můžete použít podobným způsobem, ale bez nutnosti vytvořit vlastní kolekce typ:</span><span class="sxs-lookup"><span data-stu-id="2d580-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>  
  
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
>  <span data-ttu-id="2d580-283"><xref:System.Threading.Tasks.Dataflow> Je k dispozici v oboru názvů [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] prostřednictvím **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2d580-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] through **NuGet**.</span></span> <span data-ttu-id="2d580-284">Instalace sestavení, který obsahuje <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online balíček Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="2d580-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d580-285">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d580-285">See Also</span></span>  
 [<span data-ttu-id="2d580-286">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="2d580-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="2d580-287">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="2d580-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="2d580-288">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="2d580-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
