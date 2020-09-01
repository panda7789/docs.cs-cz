---
description: try-catch-C# – Reference
title: try-catch-C# – Reference
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
ms.openlocfilehash: e3154da2103029f704abd6873d16d372f1ae19ac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141995"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="8cda4-103">try-catch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8cda4-103">try-catch (C# Reference)</span></span>

<span data-ttu-id="8cda4-104">Příkaz try-catch se skládá z `try` bloku následovaného jednou nebo více `catch` klauzulemi, které určují obslužné rutiny pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="8cda4-104">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="8cda4-105">Je-li vyvolána výjimka, modul CLR (Common Language Runtime) vyhledá `catch` příkaz, který zpracovává tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="8cda4-106">Pokud aktuálně spuštěná metoda neobsahuje takový `catch` blok, CLR vyhledá metodu, která volala aktuální metodu, a tak dále v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="8cda4-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="8cda4-107">Pokud `catch` není nalezen žádný blok, modul CLR zobrazí uživateli neošetřenou zprávu o výjimce a zastaví provádění programu.</span><span class="sxs-lookup"><span data-stu-id="8cda4-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="8cda4-108">`try`Blok obsahuje chráněný kód, který může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="8cda4-109">Blok je proveden, dokud není vyvolána výjimka nebo je úspěšně dokončen.</span><span class="sxs-lookup"><span data-stu-id="8cda4-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="8cda4-110">Například následující pokus o přetypování `null` objektu vyvolá <xref:System.NullReferenceException> výjimku:</span><span class="sxs-lookup"><span data-stu-id="8cda4-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="8cda4-111">Přestože `catch` lze klauzuli použít bez argumentů k zachycení jakéhokoliv typu výjimky, toto použití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="8cda4-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="8cda4-112">Obecně platí, že byste měli zachytit pouze ty výjimky, ze kterých víte, jak provést obnovení.</span><span class="sxs-lookup"><span data-stu-id="8cda4-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="8cda4-113">Proto byste měli vždy zadat argument objektu odvozený z například <xref:System.Exception?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="8cda4-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="8cda4-114">Ve stejném příkazu try-catch je možné použít více než jednu konkrétní `catch` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8cda4-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="8cda4-115">V tomto případě `catch` je pořadí klauzulí důležité, protože `catch` klauzule jsou zkontrolovány v pořadí.</span><span class="sxs-lookup"><span data-stu-id="8cda4-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="8cda4-116">Zachyťte konkrétnější výjimky před méně specifickými výjimkami.</span><span class="sxs-lookup"><span data-stu-id="8cda4-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="8cda4-117">Kompilátor vytvoří chybu, Pokud seřadíte bloky catch tak, aby k nim nikdy nebylo možné získat přístup později.</span><span class="sxs-lookup"><span data-stu-id="8cda4-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="8cda4-118">Použití `catch` argumentů je jedním ze způsobů, jak filtrovat výjimky, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="8cda4-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="8cda4-119">Můžete také použít filtr výjimek, který dále prověřuje výjimku k rozhodnutí, zda je zpracována.</span><span class="sxs-lookup"><span data-stu-id="8cda4-119">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="8cda4-120">Pokud filtr výjimek vrátí hodnotu false, hledání obslužné rutiny pokračuje.</span><span class="sxs-lookup"><span data-stu-id="8cda4-120">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="8cda4-121">Filtry výjimek jsou vhodnější pro zachycení a opětovné vyvolání (vysvětlení níže), protože filtry ponechají zásobník neškodný.</span><span class="sxs-lookup"><span data-stu-id="8cda4-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="8cda4-122">Pokud později obslužná rutina vypíše zásobník, můžete zjistit, kde výjimka původně pochází z, nikoli jenom poslední místo, které bylo znovu vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="8cda4-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="8cda4-123">Běžné použití výrazů filtru výjimky je protokolování.</span><span class="sxs-lookup"><span data-stu-id="8cda4-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="8cda4-124">Můžete vytvořit filtr, který vždycky vrátí hodnotu false, která také vrací výstup do protokolu, a to tak, že se výjimky zaprotokolují, aniž byste je museli zpracovávat a znovu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="8cda4-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="8cda4-125">Příkaz [throw](throw.md) lze použít v `catch` bloku k opětovnému vyvolání výjimky, která je zachycena `catch` příkazem.</span><span class="sxs-lookup"><span data-stu-id="8cda4-125">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="8cda4-126">Následující příklad extrahuje informace o zdroji z <xref:System.IO.IOException> výjimky a poté vyvolá výjimku z nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="8cda4-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

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

<span data-ttu-id="8cda4-127">Můžete zachytit jednu výjimku a vyvolat jinou výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="8cda4-128">V takovém případě určete výjimku, kterou jste zachytil jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8cda4-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="8cda4-129">Můžete také znovu vyvolat výjimku, pokud je zadaná podmínka pravdivá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8cda4-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

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
> <span data-ttu-id="8cda4-130">Je také možné použít filtr výjimek a získat tak podobný výsledek často čisticím způsobem (a také Neupravovat zásobník, jak je vysvětleno výše v tomto dokumentu).</span><span class="sxs-lookup"><span data-stu-id="8cda4-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="8cda4-131">Následující příklad má podobné chování jako v předchozím příkladu pro volající.</span><span class="sxs-lookup"><span data-stu-id="8cda4-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="8cda4-132">Funkce vyvolá `InvalidCastException` zpětné volání volajícímu, pokud `e.Data` je `null` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="8cda4-133">V rámci `try` bloku inicializujte pouze proměnné, které jsou deklarovány v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="8cda4-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="8cda4-134">V opačném případě může výjimka nastat před dokončením provádění bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="8cda4-135">Například v následujícím příkladu kódu `n` je proměnná inicializována uvnitř `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="8cda4-136">Pokus o použití této proměnné mimo `try` blok v `Write(n)` příkazu vytvoří chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8cda4-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

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

<span data-ttu-id="8cda4-137">Další informace o catch naleznete v tématu [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="8cda4-137">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="8cda4-138">Výjimky v asynchronních metodách</span><span class="sxs-lookup"><span data-stu-id="8cda4-138">Exceptions in async methods</span></span>

<span data-ttu-id="8cda4-139">Asynchronní metoda je označena modifikátorem  [Async](async.md) a obvykle obsahuje jeden nebo více výrazů nebo příkazů await.</span><span class="sxs-lookup"><span data-stu-id="8cda4-139">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="8cda4-140">Výraz Await aplikuje operátor [await](../operators/await.md) na <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="8cda4-140">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="8cda4-141">Když ovládací prvek dosáhne `await` v asynchronní metodě, je průběh metody pozastaven, dokud se nedokončí dokončená úloha.</span><span class="sxs-lookup"><span data-stu-id="8cda4-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="8cda4-142">Po dokončení úlohy může provádění pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="8cda4-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="8cda4-143">Další informace naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cda4-143">For more information, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="8cda4-144">Dokončený úkol, ke kterému `await` je použito, může být v chybovém stavu z důvodu neošetřené výjimky v metodě, která vrací úlohu.</span><span class="sxs-lookup"><span data-stu-id="8cda4-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="8cda4-145">Čekání na úkol vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="8cda4-146">Úloha může také končit ve zrušeném stavu, pokud asynchronní proces, který je vrátí, je zrušen.</span><span class="sxs-lookup"><span data-stu-id="8cda4-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="8cda4-147">Čekání na zrušený úkol vyvolá výjimku `OperationCanceledException` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-147">Awaiting a canceled task throws an `OperationCanceledException`.</span></span>

<span data-ttu-id="8cda4-148">Chcete-li zachytit výjimku, očekávat úlohu v `try` bloku a zachytit výjimku v přidruženém `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="8cda4-149">Příklad naleznete v části [příklad asynchronní metody](#async-method-example) .</span><span class="sxs-lookup"><span data-stu-id="8cda4-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="8cda4-150">Úloha může být v chybném stavu, protože v očekávané asynchronní metodě došlo k více výjimkám.</span><span class="sxs-lookup"><span data-stu-id="8cda4-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="8cda4-151">Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8cda4-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8cda4-152">Při čekání na takovou úlohu je zachycena pouze jedna z výjimek a nelze předpovědět, která výjimka bude zachycena.</span><span class="sxs-lookup"><span data-stu-id="8cda4-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="8cda4-153">Příklad naleznete v části [Task. WhenAll example](#taskwhenall-example) .</span><span class="sxs-lookup"><span data-stu-id="8cda4-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="8cda4-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cda4-154">Example</span></span>

<span data-ttu-id="8cda4-155">V následujícím příkladu `try` blok obsahuje volání `ProcessString` metody, která může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="8cda4-156">`catch`Klauzule obsahuje obslužnou rutinu výjimky, která pouze zobrazí zprávu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="8cda4-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="8cda4-157">Když `throw` je příkaz volán zevnitř `ProcessString` , systém vyhledá `catch` příkaz a zobrazí zprávu `Exception caught` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-157">When the `throw` statement is called from inside `ProcessString`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="8cda4-158">Příklad dvou bloků catch</span><span class="sxs-lookup"><span data-stu-id="8cda4-158">Two catch blocks example</span></span>

<span data-ttu-id="8cda4-159">V následujícím příkladu jsou použity dva bloky catch a nejvíc specifická výjimka, která je první, je zachycena.</span><span class="sxs-lookup"><span data-stu-id="8cda4-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="8cda4-160">Chcete-li zachytit minimální specifickou výjimku, můžete nahradit příkaz throw příkazem `ProcessString` pomocí následujícího příkazu: `throw new Exception()` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="8cda4-161">Pokud umístíte blok catch, který je nejméně specifický, jako první v příkladu, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="8cda4-162">Příklad asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="8cda4-162">Async method example</span></span>

<span data-ttu-id="8cda4-163">Následující příklad znázorňuje zpracování výjimek pro asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="8cda4-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="8cda4-164">Chcete-li zachytit výjimku, kterou asynchronní úloha vyvolá, umístěte `await` výraz do `try` bloku a zachyťte výjimku v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="8cda4-165">Odkomentujte `throw new Exception` řádek v příkladu k demonstraci zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="8cda4-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="8cda4-166">`IsFaulted`Vlastnost úlohy je nastavena na hodnotu `True` , vlastnost úlohy `Exception.InnerException` je nastavena na výjimku a výjimka je zachycena v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="8cda4-167">Odkomentujte `throw new OperationCanceledException` řádek k předvedení toho, co se stane, když zrušíte asynchronní proces.</span><span class="sxs-lookup"><span data-stu-id="8cda4-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="8cda4-168">`IsCanceled`Vlastnost úlohy je nastavena na hodnotu `true` a výjimka je zachycena v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="8cda4-169">Za určitých podmínek, které se nevztahují na tento příklad, `IsFaulted` je vlastnost úlohy nastavena na hodnotu `true` a `IsCanceled` je nastavena na `false` .</span><span class="sxs-lookup"><span data-stu-id="8cda4-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="8cda4-170">Příklad Task. WhenAll</span><span class="sxs-lookup"><span data-stu-id="8cda4-170">Task.WhenAll example</span></span>

<span data-ttu-id="8cda4-171">Následující příklad znázorňuje zpracování výjimek, kde více úloh může mít za následek vícenásobné výjimky.</span><span class="sxs-lookup"><span data-stu-id="8cda4-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="8cda4-172">`try`Blok čeká na úlohu vrácenou voláním <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8cda4-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8cda4-173">Úkol je dokončen, když jsou dokončeny tři úkoly, na které se WhenAll aplikuje.</span><span class="sxs-lookup"><span data-stu-id="8cda4-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="8cda4-174">Každá ze tří úkolů způsobuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="8cda4-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="8cda4-175">`catch`Blok prochází výjimky, které jsou umístěny ve `Exception.InnerExceptions` vlastnosti úkolu, který vrátil <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8cda4-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="8cda4-176">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cda4-176">C# language specification</span></span>

<span data-ttu-id="8cda4-177">Další informace naleznete v oddílu [Try příkazu](~/_csharplang/spec/statements.md#the-try-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8cda4-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cda4-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cda4-178">See also</span></span>

- [<span data-ttu-id="8cda4-179">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cda4-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8cda4-180">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8cda4-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8cda4-181">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cda4-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8cda4-182">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="8cda4-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="8cda4-183">throw</span><span class="sxs-lookup"><span data-stu-id="8cda4-183">throw</span></span>](throw.md)
- [<span data-ttu-id="8cda4-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="8cda4-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="8cda4-185">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="8cda4-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
