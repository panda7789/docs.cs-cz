---
title: try-catch - C# Reference
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173468"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="273f3-102">try-catch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="273f3-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="273f3-103">Příkaz try-catch se skládá `try` z bloku následovaného jednou nebo více `catch` klauzulemi, které určují obslužné rutiny pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="273f3-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="273f3-104">Při vyvolání výjimky, clr (CLR) společného `catch` jazyka hledá příkaz, který zpracovává tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-104">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="273f3-105">Pokud aktuálně spuštěná metoda neobsahuje `catch` takový blok, CLR se podívá na metodu, která volala aktuální metodu a tak dále nahoru zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="273f3-105">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="273f3-106">Pokud `catch` není nalezen žádný blok, zobrazí CLR neošetřenou zprávu o výjimce uživateli a zastaví provádění programu.</span><span class="sxs-lookup"><span data-stu-id="273f3-106">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="273f3-107">Blok `try` obsahuje střežený kód, který může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-107">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="273f3-108">Blok je spuštěn, dokud není vyvolána výjimka nebo dokud není úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="273f3-108">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="273f3-109">Například následující pokus o `null` přetypovat <xref:System.NullReferenceException> objekt vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="273f3-109">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="273f3-110">Přestože `catch` klauzule lze použít bez argumentů zachytit jakýkoli typ výjimky, toto použití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="273f3-110">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="273f3-111">Obecně platí, že byste měli zachytit pouze ty výjimky, ze kterých víte, jak se zotavit.</span><span class="sxs-lookup"><span data-stu-id="273f3-111">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="273f3-112">Proto byste měli vždy zadat argument <xref:System.Exception?displayProperty=nameWithType> objektu odvozený například:</span><span class="sxs-lookup"><span data-stu-id="273f3-112">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="273f3-113">Je možné použít více než `catch` jednu konkrétní klauzuli ve stejném příkazu try-catch.</span><span class="sxs-lookup"><span data-stu-id="273f3-113">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="273f3-114">V tomto případě je `catch` pořadí doložek důležité, protože `catch` doložky jsou zkoumány v pořadí.</span><span class="sxs-lookup"><span data-stu-id="273f3-114">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="273f3-115">Zachyťte konkrétnější výjimky před méně konkrétními výjimkami.</span><span class="sxs-lookup"><span data-stu-id="273f3-115">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="273f3-116">Kompilátor vytvoří chybu, pokud objednáte bloky catch tak, aby nikdy nebylo dosaženo pozdějšího bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-116">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="273f3-117">Použití `catch` argumentů je jedním ze způsobů filtrování výjimek, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="273f3-117">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="273f3-118">Můžete také použít filtr výjimek, který dále zkoumá výjimku a rozhodne, zda ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="273f3-118">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="273f3-119">Pokud filtr výjimek vrátí hodnotu false, pokračuje hledání obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="273f3-119">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="273f3-120">Filtry výjimek jsou vhodnější k zachycení a opětovnému vyvolání (vysvětleno níže), protože filtry ponechávají zásobník bez poškození.</span><span class="sxs-lookup"><span data-stu-id="273f3-120">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="273f3-121">Pokud novější obslužná rutina vypíše zásobníku, můžete zobrazit, kde výjimka původně pochází, nikoli jen na posledním místě, které bylo znovu vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="273f3-121">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="273f3-122">Běžně se používají výrazy filtru výjimek protokolování.</span><span class="sxs-lookup"><span data-stu-id="273f3-122">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="273f3-123">Můžete vytvořit filtr, který vždy vrátí false, který také výstupy do protokolu, můžete protokolovat výjimky, jak jdou, aniž by bylo třeba je zpracovat a znovu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="273f3-123">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="273f3-124">Příkaz [throw](throw.md) lze použít `catch` v bloku znovu vyvolat výjimku, `catch` která je zachycena příkazem.</span><span class="sxs-lookup"><span data-stu-id="273f3-124">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="273f3-125">Následující příklad extrahuje zdrojové informace z výjimky <xref:System.IO.IOException> a potom vyvolá výjimku nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="273f3-125">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="273f3-126">Můžete zachytit jednu výjimku a vyvolat jinou výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-126">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="273f3-127">Když toto, zadejte výjimku, která byla zachycena jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="273f3-127">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="273f3-128">Můžete také znovu vyvolat výjimku, pokud je zadaná podmínka pravdivá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="273f3-128">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="273f3-129">Je také možné použít filtr výjimek získat podobný výsledek často čistší způsobem (stejně jako neúpravy zásobníku, jak je vysvětleno výše v tomto dokumentu).</span><span class="sxs-lookup"><span data-stu-id="273f3-129">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="273f3-130">Následující příklad má podobné chování pro volající jako předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="273f3-130">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="273f3-131">Funkce vyvolá `InvalidCastException` zpět volajícímu, `e.Data` když `null`je .</span><span class="sxs-lookup"><span data-stu-id="273f3-131">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="273f3-132">Zevnitř `try` bloku inicializovat pouze proměnné, které jsou deklarovány v něm.</span><span class="sxs-lookup"><span data-stu-id="273f3-132">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="273f3-133">V opačném případě může dojít k výjimce před dokončením provádění bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-133">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="273f3-134">Například v následujícím příkladu kódu `n` je proměnná `try` inicializována uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-134">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="273f3-135">Pokus o použití této `try` proměnné mimo `Write(n)` blok v příkazu vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="273f3-135">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="273f3-136">Další informace o úlovku naleznete v [tématu try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="273f3-136">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="273f3-137">Výjimky v asynchronních metodách</span><span class="sxs-lookup"><span data-stu-id="273f3-137">Exceptions in async methods</span></span>

<span data-ttu-id="273f3-138">Asynchronní metoda je [označena asynchronním](async.md) modifikátorem a obvykle obsahuje jeden nebo více výrazů nebo příkazů await.</span><span class="sxs-lookup"><span data-stu-id="273f3-138">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="273f3-139">Výraz await použije operátor [await](../operators/await.md) <xref:System.Threading.Tasks.Task> na <xref:System.Threading.Tasks.Task%601>operátor a nebo .</span><span class="sxs-lookup"><span data-stu-id="273f3-139">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="273f3-140">Když ovládací prvek `await` dosáhne v asynchronní metodě, průběh metody je pozastaven, dokud nebude dokončena očekávaná úloha.</span><span class="sxs-lookup"><span data-stu-id="273f3-140">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="273f3-141">Po dokončení úlohy může spuštění pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="273f3-141">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="273f3-142">Další informace naleznete [v tématu Asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md) a [control flow v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="273f3-142">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="273f3-143">Dokončená úloha, na kterou `await` je použita může být v chybovém stavu z důvodu neošetřené výjimky v metodě, která vrátí úkol.</span><span class="sxs-lookup"><span data-stu-id="273f3-143">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="273f3-144">Čekání na úkol vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-144">Awaiting the task throws an exception.</span></span> <span data-ttu-id="273f3-145">Úloha může také skončit ve stavu zrušena, pokud je zrušen asynchronní proces, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="273f3-145">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="273f3-146">Čekání na zrušený úkol `OperationCanceledException`vyvolá .</span><span class="sxs-lookup"><span data-stu-id="273f3-146">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="273f3-147">Další informace o zrušení asynchronního procesu naleznete v [tématu Jemné doladění asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="273f3-147">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="273f3-148">Chcete-li zachytit výjimku, počkejte na úkol v `try` bloku `catch` a zachyťte výjimku v přidruženém bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="273f3-149">Příklad naleznete v části [Příklad metody Async.](#async-method-example)</span><span class="sxs-lookup"><span data-stu-id="273f3-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="273f3-150">Úloha může být v chybovém stavu, protože došlo k více výjimkám v aočekávaná asynchronní metoda.</span><span class="sxs-lookup"><span data-stu-id="273f3-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="273f3-151">Úkol může být například výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="273f3-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="273f3-152">Když čekáte na takový úkol, je zachycena pouze jedna z výjimek a nemůžete předpovědět, která výjimka bude zachycena.</span><span class="sxs-lookup"><span data-stu-id="273f3-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="273f3-153">Příklad naleznete v části [Task.WhenAll example.](#taskwhenall-example)</span><span class="sxs-lookup"><span data-stu-id="273f3-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="273f3-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="273f3-154">Example</span></span>

<span data-ttu-id="273f3-155">V následujícím příkladu `try` blok obsahuje volání `ProcessString` metody, která může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="273f3-156">Klauzule `catch` obsahuje obslužnou rutinu výjimky, která pouze zobrazí zprávu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="273f3-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="273f3-157">Při `throw` volání příkazu `MyMethod`zevnitř systém vyhledá `catch` příkaz a `Exception caught`zobrazí zprávu .</span><span class="sxs-lookup"><span data-stu-id="273f3-157">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="273f3-158">Příklad dvou bloků úlovků</span><span class="sxs-lookup"><span data-stu-id="273f3-158">Two catch blocks example</span></span>

<span data-ttu-id="273f3-159">V následujícím příkladu jsou použity dva bloky catch a nejkonkrétnější výjimka, která je na prvním místě, je zachycena.</span><span class="sxs-lookup"><span data-stu-id="273f3-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="273f3-160">Chcete-li zachytit nejméně konkrétní výjimku, `ProcessString` můžete nahradit throw `throw new Exception()`prohlášení v s následujícím příkazem: .</span><span class="sxs-lookup"><span data-stu-id="273f3-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="273f3-161">Pokud v příkladu umístíte nejprve nejméně specifický blok catch, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="273f3-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="273f3-162">Příklad asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="273f3-162">Async method example</span></span>

<span data-ttu-id="273f3-163">Následující příklad ilustruje zpracování výjimek pro asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="273f3-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="273f3-164">Chcete-li zachytit výjimku, kterou vyvolá `await` asynchronní `try` úloha, umístěte výraz `catch` do bloku a zachyťte výjimku v bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="273f3-165">Odkomentujte `throw new Exception` řádek v příkladu, abyste demonstrovali zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="273f3-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="273f3-166">`IsFaulted` Vlastnost úkolu je nastavena `True`na , `Exception.InnerException` vlastnost úkolu je nastavena na výjimku `catch` a výjimka je zachycena v bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="273f3-167">Odkomentujte `throw new OperationCanceledException` řádek a předveďte, co se stane, když zrušíte asynchronní proces.</span><span class="sxs-lookup"><span data-stu-id="273f3-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="273f3-168">`IsCanceled` Vlastnost úkolu je nastavena `true`na , a výjimka je zachycena `catch` v bloku.</span><span class="sxs-lookup"><span data-stu-id="273f3-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="273f3-169">Za určitých podmínek, které se v tomto `IsFaulted` příkladu `true` nevztahují, je vlastnost úkolu nastavena na položku a `IsCanceled` je nastavena na . `false`</span><span class="sxs-lookup"><span data-stu-id="273f3-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="273f3-170">Task.WhenPříklad</span><span class="sxs-lookup"><span data-stu-id="273f3-170">Task.WhenAll example</span></span>

<span data-ttu-id="273f3-171">Následující příklad znázorňuje zpracování výjimek, kde více úkolů může mít za následek více výjimek.</span><span class="sxs-lookup"><span data-stu-id="273f3-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="273f3-172">Blok `try` čeká na úkol, který je vrácen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>voláním .</span><span class="sxs-lookup"><span data-stu-id="273f3-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="273f3-173">Úkol je dokončen po dokončení tří úkolů, na které je použita WhenAll.</span><span class="sxs-lookup"><span data-stu-id="273f3-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="273f3-174">Každý ze tří úkolů způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="273f3-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="273f3-175">Blok `catch` iterates prostřednictvím výjimky, které `Exception.InnerExceptions` se nacházejí ve vlastnosti <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>úkolu, který byl vrácen .</span><span class="sxs-lookup"><span data-stu-id="273f3-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="273f3-176">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="273f3-176">C# language specification</span></span>

<span data-ttu-id="273f3-177">Další informace naleznete v části [try statement](~/_csharplang/spec/statements.md#the-try-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="273f3-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="273f3-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="273f3-178">See also</span></span>

- [<span data-ttu-id="273f3-179">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="273f3-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="273f3-180">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="273f3-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="273f3-181">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="273f3-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="273f3-182">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="273f3-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="273f3-183">throw</span><span class="sxs-lookup"><span data-stu-id="273f3-183">throw</span></span>](throw.md)
- [<span data-ttu-id="273f3-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="273f3-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="273f3-185">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="273f3-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
