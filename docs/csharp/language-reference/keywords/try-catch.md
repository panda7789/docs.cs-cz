---
title: "try-catch (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 753beb554796ad0aa2c5e15c715240453de9a3e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="b8fb5-102">try-catch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b8fb5-102">try-catch (C# Reference)</span></span>
<span data-ttu-id="b8fb5-103">Try-catch – příkaz se skládá z `try` bloku, za nímž následuje jeden nebo více `catch` klauzule, které určují obslužné rutiny pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8fb5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8fb5-104">Remarks</span></span>  
 <span data-ttu-id="b8fb5-105">Když je vyvolána výjimka, modul CLR (CLR) hledá `catch` příkaz, který zpracovává výjimku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="b8fb5-106">Pokud například neobsahuje metodu aktuálně prováděné `catch` blok CLR vypadá na metodu, která volá metodu aktuální, a tak dále zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="b8fb5-107">Pokud žádné `catch` blok a pak modulu CLR, zobrazí se zpráva neošetřené výjimky pro uživatele a zastaví provádění tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>  
  
 <span data-ttu-id="b8fb5-108">`try` Blok obsahuje chráněného kód, který může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="b8fb5-109">Blok je provést, dokud je vyvolána výjimka, nebo je byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="b8fb5-110">Například následující pokus přetypovat `null` objektu vyvolá <xref:System.NullReferenceException> výjimka:</span><span class="sxs-lookup"><span data-stu-id="b8fb5-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 <span data-ttu-id="b8fb5-111">I když `catch` klauzuli lze použít bez argumentů k zachycení jakýkoli typ výjimky, toto využití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="b8fb5-112">Obecně platí by měla pouze zachytit tyto výjimky, kterých víte, jak jej obnovit.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="b8fb5-113">Proto musíte vždycky zadat argument objekt odvozené z <xref:System.Exception?displayProperty=nameWithType> například:</span><span class="sxs-lookup"><span data-stu-id="b8fb5-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 <span data-ttu-id="b8fb5-114">Je možné použít více než jeden konkrétní `catch` klauzule v jednom příkazu try-catch.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="b8fb5-115">V tomto případě pořadí `catch` klauzule je důležité, protože `catch` klauzule se zkontrolují v pořadí.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="b8fb5-116">Před méně konkrétní ty catch konkrétnější výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="b8fb5-117">Kompilátor vyvolá chybu, je-li pořadí, že vaše catch blokuje tak, aby nikdy dostupný novější blok.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>  
  
 <span data-ttu-id="b8fb5-118">Pomocí `catch` argumentů je jeden způsob, jak filtrovat výjimky, které chcete zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="b8fb5-119">Můžete také použít výraz predikátu, která prověřuje další výjimka můžete rozhodnout, jestli se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-119">You can also use a predicate expression that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="b8fb5-120">Výraz predikátu vrací hodnotu false, potom pokračuje hledání pro obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-120">If the predicate expression returns false, then the search for a handler continues.</span></span>  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 <span data-ttu-id="b8fb5-121">Filtry výjimek, je vhodnější zachytávání a opětné vyvolání (vysvětleno níže), protože zásobník nepoškozená nechte filtry.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="b8fb5-122">Pokud obslužnou rutinu novější výpisy zásobníku, uvidíte, kde výjimka původně pochází, nikoli pouze poslední, který byl znovu vyvolány místo.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="b8fb5-123">Běžně se používají výrazy filtru výjimek je protokolování.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="b8fb5-124">Můžete vytvořit predikátem funkci, která vždy vrátí hodnotu false, který také výstupy do protokolů, jako přejde bez nutnosti mohli je zpracovat a opětovné můžete protokolovat výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-124">You can create a predicate function that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>  
  
 <span data-ttu-id="b8fb5-125">A [throw](../../../csharp/language-reference/keywords/throw.md) příkaz lze použít v `catch` blok k znovu vyvolání výjimky, která bude zachycena `catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-125">A [throw](../../../csharp/language-reference/keywords/throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="b8fb5-126">Následující příklad extrahuje informace o zdroji ze <xref:System.IO.IOException> výjimka a potom vyvolá výjimku pro nadřazenou metodu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>  
  
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
  
 <span data-ttu-id="b8fb5-127">Můžete zachytit jednu výjimku a vyvolat různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="b8fb5-128">Když to uděláte, zadejte výjimku, která zachycena jako v popisu vnitřní výjimky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 <span data-ttu-id="b8fb5-129">Můžete také znovu vyvolat výjimku, pokud je zadaná podmínka hodnotu true, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b8fb5-130">Z uvnitř `try` blokovat, inicializovat pouze proměnné, které jsou deklarované v něm.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-130">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="b8fb5-131">Výjimku, jinak může dojít, než bude dokončeno spuštění bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-131">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="b8fb5-132">Například v následujícím příkladu kódu proměnnou `n` je inicializován uvnitř `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-132">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="b8fb5-133">Pokus o použití této proměnné mimo `try` blokovat `Write(n)` příkaz vygeneruje se chybová zpráva kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-133">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="b8fb5-134">Další informace o catch najdete v tématu [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="b8fb5-134">For more information about catch, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
## <a name="exceptions-in-async-methods"></a><span data-ttu-id="b8fb5-135">Výjimky v asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="b8fb5-135">Exceptions in Async Methods</span></span>  
 <span data-ttu-id="b8fb5-136">Asynchronní metody je označena kvalifikátorem [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor a obvykle obsahuje jeden nebo více await výrazy nebo příkazy.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-136">An async method is marked  by an  [async](../../../csharp/language-reference/keywords/async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="b8fb5-137">Await výraz se vztahuje [await](../../../csharp/language-reference/keywords/await.md) operátorovi <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-137">An await expression applies the [await](../../../csharp/language-reference/keywords/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="b8fb5-138">Při řízení dosáhnou `await` v asynchronní metody, je průběh v metodě pozastaveno, dokud dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-138">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="b8fb5-139">Po dokončení úlohy provádění může pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-139">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="b8fb5-140">Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md) a [řízení toku v asynchronních programech](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="b8fb5-140">For more information, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
 <span data-ttu-id="b8fb5-141">Dokončené úlohy, ke kterému `await` platí může být v chybovém stavu z důvodu neošetřené výjimce v metodě, který vrátí úlohu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-141">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="b8fb5-142">Systém čeká na úlohu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-142">Awaiting the task throws an exception.</span></span> <span data-ttu-id="b8fb5-143">Úlohu můžete také skončit ve zrušené stavu, pokud se zruší asynchronní proces, který vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-143">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="b8fb5-144">Systém čeká na zrušené úlohy vyvolá `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-144">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="b8fb5-145">Další informace o tom, jak zrušit asynchronní proces najdete v tématu [Fine-Tuning vaše asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="b8fb5-145">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="b8fb5-146">K zachycení výjimky, kde čekají na úlohu v `try` blokovat a zachycení výjimky v přidruženém `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-146">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="b8fb5-147">Příklad najdete v části "Příklad".</span><span class="sxs-lookup"><span data-stu-id="b8fb5-147">For an example, see the "Example" section.</span></span>  
  
 <span data-ttu-id="b8fb5-148">Úloha může být v chybovém stavu, protože několik výjimek došlo k chybě v očekávané asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-148">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="b8fb5-149">Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-149">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8fb5-150">Když jste await takových úloh, pouze jeden z výjimky je zachycena a nemůžete předpovědět, které k výjimce.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-150">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="b8fb5-151">Příklad najdete v části "Příklad".</span><span class="sxs-lookup"><span data-stu-id="b8fb5-151">For an example, see the "Example" section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8fb5-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8fb5-152">Example</span></span>  
 <span data-ttu-id="b8fb5-153">V následujícím příkladu `try` blok obsahuje volání `ProcessString` metoda, která může způsobit výjimku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-153">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="b8fb5-154">`catch` Klauzule WHERE obsahuje jenom na obrazovce se objeví zpráva obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-154">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="b8fb5-155">Když `throw` příkaz je volána z uvnitř `MyMethod`, hledá v systému `catch` příkaz a zobrazí zprávu `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-155">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b8fb5-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8fb5-156">Example</span></span>  
 <span data-ttu-id="b8fb5-157">V následujícím příkladu se používají dva bloky catch a nejvíce výjimka, která dodává první, je zachycena.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-157">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>  
  
 <span data-ttu-id="b8fb5-158">K zachycení výjimky nejméně specifická, můžete nahradit v příkazu throw `ProcessString` s následující příkaz: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-158">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>  
  
 <span data-ttu-id="b8fb5-159">Pokud nejprve umístit blok catch nejmenší konkrétní v příkladu se zobrazí následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-159">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="b8fb5-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8fb5-160">Example</span></span>  
 <span data-ttu-id="b8fb5-161">Následující příklad ilustruje zpracování výjimek pro asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-161">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="b8fb5-162">Zachytit výjimku, která vyvolá asynchronní úlohy, umístit `await` výrazu v `try` blokovat a zachycení výjimky v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-162">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>  
  
 <span data-ttu-id="b8fb5-163">Zrušením komentáře u `throw new Exception` řádku v příkladu za účelem ukázky zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-163">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="b8fb5-164">Úkolu `IsFaulted` je nastavena na `True`, úkolu `Exception.InnerException` je nastavena na výjimku a je výjimka zachycena v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-164">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>  
  
 <span data-ttu-id="b8fb5-165">Zrušením komentáře u `throw new OperationCancelledException` řádku k předvedení toho, co se stane, když zrušíte asynchronní proces.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-165">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="b8fb5-166">Úkolu `IsCanceled` je nastavena na `true`, a je výjimka zachycena v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-166">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="b8fb5-167">Za určitých podmínek, které se nevztahují na tomto příkladu úlohu na `IsFaulted` je nastavena na `true` a `IsCanceled` je nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-167">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="b8fb5-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8fb5-168">Example</span></span>  
 <span data-ttu-id="b8fb5-169">Následující příklad ukazuje zpracování výjimek, kde více úloh může mít za následek více výjimek.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-169">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="b8fb5-170">`try` Bloku čeká úloha, která se vrátí po volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-170">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8fb5-171">Po dokončení tři úloh, pro které je použito WhenAll dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-171">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>  
  
 <span data-ttu-id="b8fb5-172">Jednotlivé tři úlohy dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-172">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="b8fb5-173">`catch` Bloku iteruje výjimky, které jsou součástí `Exception.InnerExceptions` vlastnost úloha, která vrátila <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8fb5-173">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b8fb5-174">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8fb5-174">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8fb5-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8fb5-175">See Also</span></span>  
 [<span data-ttu-id="b8fb5-176">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8fb5-176">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b8fb5-177">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b8fb5-177">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b8fb5-178">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8fb5-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b8fb5-179">Zkuste, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="b8fb5-179">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="b8fb5-180">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="b8fb5-180">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="b8fb5-181">throw</span><span class="sxs-lookup"><span data-stu-id="b8fb5-181">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="b8fb5-182">try-finally –</span><span class="sxs-lookup"><span data-stu-id="b8fb5-182">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="b8fb5-183">Postupy: explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="b8fb5-183">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
