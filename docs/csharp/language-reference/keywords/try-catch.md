---
title: try-catch - C# odkaz
ms.custom: seodec18
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
ms.openlocfilehash: 7e48783c01a5b94f51f89d25f465f22358e7aa8f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240018"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="7b1ce-102">try-catch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7b1ce-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="7b1ce-103">Příkaz try-catch se skládá z `try` bloku, za nímž následuje jedna nebo více `catch` klauzule, které určují obslužné rutiny pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b1ce-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b1ce-104">Remarks</span></span>

<span data-ttu-id="7b1ce-105">Když je vyvolána výjimka, modul CLR (CLR) hledá `catch` příkaz, který zpracovává tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="7b1ce-106">Pokud aktuálně prováděné metody neobsahuje, `catch` blokovat, vyhledá CLR na metodu, která volá metodu aktuální výše v zásobníku volání a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="7b1ce-107">Pokud ne `catch` nalezen blok a pak zobrazí uživateli zprávu neošetřené výjimky CLR a zastaví provádění programu.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="7b1ce-108">`try` Blok obsahuje chráněné kód, který může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="7b1ce-109">Blok je udělat, dokud je vyvolána výjimka nebo je byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="7b1ce-110">Například následující pokusili přetypovat `null` objektu vyvolá <xref:System.NullReferenceException> výjimka:</span><span class="sxs-lookup"><span data-stu-id="7b1ce-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="7b1ce-111">I když `catch` klauzuli lze použít bez argumentů pro zachycení jakéhokoli typu výjimky, toto využití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="7b1ce-112">Obecně platí měli byste zachytit pouze takové výjimky, které víte, jak provést obnovení.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="7b1ce-113">Proto musíte vždycky zadat argument objekt odvozený od <xref:System.Exception?displayProperty=nameWithType> například:</span><span class="sxs-lookup"><span data-stu-id="7b1ce-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="7b1ce-114">Je možné použít více než jeden konkrétní `catch` klauzule ve stejném příkazu try-catch.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="7b1ce-115">V takovém případě pořadí `catch` klauzulí je důležité, protože `catch` klauzule jsou zkoumány podle pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="7b1ce-116">Zachycení více specifické výjimky než těch, které jsou specifické pro less.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="7b1ce-117">Kompilátor vytvoří chybu, pokud řazení, že vaše catch blokuje tak, aby novější bloku můžou být nikdy dosažen.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="7b1ce-118">Pomocí `catch` argumentů je jedním ze způsobů filtrování pro výjimky, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="7b1ce-119">Můžete také použít filtr výjimek, který prověří další výjimky můžete rozhodnout, jestli ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-119">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="7b1ce-120">Pokud filtr výjimek vrací hodnotu false, pak hledání pro obslužnou rutinu, bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-120">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="7b1ce-121">Filtry výjimek jsou upřednostňovány vůči zachytávání a opětné vyvolání (vysvětleno níže), protože filtry ponechte nepoškozená zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="7b1ce-122">Pokud je novější rutinu výpisy zásobníku, naleznete v tématu výjimka původně, odkud, ne jenom poslední místo, které byla vyvolána.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="7b1ce-123">Běžné použití výrazu filtru výjimky je protokolování.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="7b1ce-124">Můžete vytvořit filtr, která vždy vrátí hodnotu false, která také výstup protokolu, může protokolování výjimek, jako jsou přejít bez nutnosti jejich zpracování a znovu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="7b1ce-125">A [throw](throw.md) příkaz lze použít v `catch` pro opětovné vyvolání výjimky, která je zachycena `catch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-125">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="7b1ce-126">Následující příklad extrahuje informace o zdroji ze <xref:System.IO.IOException> výjimky a potom vyvolá výjimku pro nadřazenou metodu.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

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

<span data-ttu-id="7b1ce-127">Můžete zachytit jednu výjimku a jinou výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="7b1ce-128">Když toto provedete, zadejte výjimku, která je zachycena jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="7b1ce-129">Můžete také znovu vyvolat výjimku při je zadaná podmínka pravdivá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

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
> <span data-ttu-id="7b1ce-130">Je také možné použít k získání výsledku podobně jako v často přehlednější způsobem (stejně jako místo abyste upravili zásobníku, jak je popsáno dříve v tomto dokumentu) filtr výjimek.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="7b1ce-131">Následující příklad je podobné chování pro volající jako předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="7b1ce-132">Funkce vyvolá `InvalidCastException` zpět do volajícího při `e.Data` je `null`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

<span data-ttu-id="7b1ce-133">Z uvnitř `try` blokovat, inicializovat pouze proměnné, které jsou deklarovány v něm.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="7b1ce-134">V opačném případě výjimce může dojít předtím, než se dokončí provádění bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="7b1ce-135">Například v následujícím příkladu kódu proměnné `n` je inicializován uvnitř `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="7b1ce-136">Pokus o použití této proměnné mimo `try` blokovat `Write(n)` příkaz vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

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

<span data-ttu-id="7b1ce-137">Další informace o catch, naleznete v tématu [konstrukce try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ce-137">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="7b1ce-138">Výjimky v asynchronních metodách</span><span class="sxs-lookup"><span data-stu-id="7b1ce-138">Exceptions in Async Methods</span></span>
<span data-ttu-id="7b1ce-139">Asynchronní metoda je označena [asynchronní](async.md) modifikátor a obvykle obsahuje jeden nebo více await výrazy nebo příkazy.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-139">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="7b1ce-140">Výraz await se vztahuje [await](await.md) operátor <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-140">An await expression applies the [await](await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="7b1ce-141">Když ovládací prvek dosáhne `await` v asynchronní metodě, je pozastavený průběh v metodě, až do dokončení očekávané úlohy.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="7b1ce-142">Po dokončení úlohy se provádění může pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="7b1ce-143">Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../programming-guide/concepts/async/index.md) a [tok řízení v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ce-143">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="7b1ce-144">Dokončené úlohy, ke kterému `await` platí může být v chybovém stavu kvůli neošetřené výjimce v metodě, která vrátí úkol.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="7b1ce-145">Čekání na výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="7b1ce-146">Úkol může také skončit ve zrušeném stavu Pokud se zruší asynchronní proces, který vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="7b1ce-147">Čeká na zrušenou úlohu vyvolá `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-147">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="7b1ce-148">Další informace o tom, jak zrušit asynchronní proces najdete v tématu [asynchronní aplikace Fine-Tuning](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ce-148">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="7b1ce-149">K zachycení výjimky, await úkol v `try` blokovat a zachytit výjimku v přidruženém `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-149">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="7b1ce-150">Příklad najdete v části "Vzorový".</span><span class="sxs-lookup"><span data-stu-id="7b1ce-150">For an example, see the "Example" section.</span></span>

<span data-ttu-id="7b1ce-151">Úloha může být v chybovém stavu, protože došlo k více výjimek v očekávaná asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-151">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="7b1ce-152">Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-152">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7b1ce-153">Když budete očekávat takový úkol, je zachycena pouze jednu z výjimek a nelze předpovědět, které k výjimce.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-153">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="7b1ce-154">Příklad najdete v části "Vzorový".</span><span class="sxs-lookup"><span data-stu-id="7b1ce-154">For an example, see the "Example" section.</span></span>

## <a name="example"></a><span data-ttu-id="7b1ce-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b1ce-155">Example</span></span>

<span data-ttu-id="7b1ce-156">V následujícím příkladu `try` blok obsahuje volání `ProcessString` metodu, která může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-156">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="7b1ce-157">`catch` Klauzule obsahujícím obslužnou rutinu výjimky, která zobrazuje pouze zprávu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-157">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="7b1ce-158">Při `throw` příkazu je volána z uvnitř `MyMethod`, hledá systému `catch` příkaz a zobrazí se zpráva `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-158">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="example"></a><span data-ttu-id="7b1ce-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b1ce-159">Example</span></span>

<span data-ttu-id="7b1ce-160">V následujícím příkladu se používají dva bloky catch a nejspecifičtější výjimku, která nastane dřív, je zachycena.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-160">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="7b1ce-161">K zachycení nejméně konkrétní výjimky, můžete nahradit příkaz throw v `ProcessString` pomocí následujícího příkazu: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-161">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="7b1ce-162">Pokud v příkladu nejdřív umístíte blok catch nejméně specifická, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-162">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="example"></a><span data-ttu-id="7b1ce-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b1ce-163">Example</span></span>

<span data-ttu-id="7b1ce-164">Následující příklad ukazuje zpracování výjimek pro asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-164">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="7b1ce-165">Pokud chcete zachytit výjimku, která vyvolá asynchronní úlohy, umístěte `await` výrazu v `try` blokovat a zachytit výjimku v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-165">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="7b1ce-166">Zrušením komentáře u `throw new Exception` řádek v příkladu předvést zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-166">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="7b1ce-167">Úkolu `IsFaulted` je nastavena na `True`, úkolu `Exception.InnerException` je nastavena na výjimky a výjimky je zachycena v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-167">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="7b1ce-168">Zrušením komentáře u `throw new OperationCancelledException` řádku předvést, co se stane, když zrušíte asynchronní proces.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-168">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="7b1ce-169">Úkolu `IsCanceled` je nastavena na `true`, která je zachycena výjimka v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-169">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="7b1ce-170">Za určitých podmínek, které se nevztahují na tohoto příkladu, úloha `IsFaulted` je nastavena na `true` a `IsCanceled` je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-170">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="example"></a><span data-ttu-id="7b1ce-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b1ce-171">Example</span></span>

<span data-ttu-id="7b1ce-172">Následující příklad ukazuje zpracování výjimek, kde více úkolů může vést k více výjimek.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-172">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="7b1ce-173">`try` Bloku očekává úkol, který je vrácen voláním <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-173">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7b1ce-174">Po dokončení tři úkolů, u kterých je použitá WhenAll je úloha dokončena.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-174">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="7b1ce-175">Všechny tři úkoly dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-175">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="7b1ce-176">`catch` Bloku prochází výjimky, které jsou součástí `Exception.InnerExceptions` vlastnosti úkolu, který byl vrácen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b1ce-176">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="7b1ce-177">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b1ce-177">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b1ce-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b1ce-178">See also</span></span>

- [<span data-ttu-id="7b1ce-179">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b1ce-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b1ce-180">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7b1ce-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b1ce-181">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b1ce-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b1ce-182">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="7b1ce-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="7b1ce-183">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="7b1ce-183">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="7b1ce-184">throw</span><span class="sxs-lookup"><span data-stu-id="7b1ce-184">throw</span></span>](throw.md)
- [<span data-ttu-id="7b1ce-185">try-finally</span><span class="sxs-lookup"><span data-stu-id="7b1ce-185">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="7b1ce-186">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="7b1ce-186">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)