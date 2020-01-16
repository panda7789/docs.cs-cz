---
title: Await – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: b5943e509bb850abc6c74e1b97ccd5fb0038f1e0
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964335"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="e1265-102">Await – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1265-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="e1265-103">Operátor `Await` použijete pro operand v asynchronní metodě nebo výrazu lambda pro pozastavení provádění metody, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="e1265-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="e1265-104">Úkol představuje probíhající práci.</span><span class="sxs-lookup"><span data-stu-id="e1265-104">The task represents ongoing work.</span></span>

<span data-ttu-id="e1265-105">Metoda, ve které je použit `Await`, musí mít modifikátor [Async](../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="e1265-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="e1265-106">Taková metoda, definovaná pomocí modifikátoru `Async` a obvykle obsahující jeden nebo více `Await` výrazů, je označována jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="e1265-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="e1265-107">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="e1265-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="e1265-108">Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1265-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="e1265-109">Úkol, pro který použijete operátor `Await`, je obvykle návratovou hodnotou z volání metody, která implementuje [asynchronní vzor založený na úlohách](https://www.microsoft.com/download/details.aspx?id=19957), to znamená <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e1265-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="e1265-110">V následujícím kódu metoda <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`, `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="e1265-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="e1265-111">Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="e1265-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="e1265-112">Operátor `Await` se použije pro `getContentsTask` k pozastavení provádění v `SumPageSizesAsync`, dokud `getContentsTask` nedokončí.</span><span class="sxs-lookup"><span data-stu-id="e1265-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="e1265-113">Mezitím se ovládací prvek vrátí volajícímu `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="e1265-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="e1265-114">Po dokončení `getContentsTask` se výraz `Await` vyhodnotí jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="e1265-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="e1265-115">Úplný příklad najdete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="e1265-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="e1265-116">Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="e1265-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="e1265-117">Příklad je v projektu AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="e1265-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="e1265-118">Pokud je použita `Await` pro výsledek volání metody, která vrací `Task(Of TResult)`, je typ `Await`ho výrazu TResult.</span><span class="sxs-lookup"><span data-stu-id="e1265-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="e1265-119">Pokud je použita `Await` pro výsledek volání metody, která vrací `Task`, výraz `Await` nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e1265-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="e1265-120">Rozdíl je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e1265-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="e1265-121">Výraz `Await` nebo příkaz neblokuje vlákno, ve kterém se provádí.</span><span class="sxs-lookup"><span data-stu-id="e1265-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="e1265-122">Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody za výraz `Await` jako pokračování na očekávaném úkolu.</span><span class="sxs-lookup"><span data-stu-id="e1265-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="e1265-123">Ovládací prvek se pak vrátí volajícímu asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="e1265-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="e1265-124">Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.</span><span class="sxs-lookup"><span data-stu-id="e1265-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="e1265-125">Výraz `Await` může nastat pouze v těle bezprostředně ohraničující metody nebo lambda výrazu, který je označen modifikátorem `Async`.</span><span class="sxs-lookup"><span data-stu-id="e1265-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="e1265-126">Termín *await* slouží jako klíčové slovo pouze v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="e1265-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="e1265-127">Jinde je interpretován jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e1265-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="e1265-128">V rámci metody `Async` nebo lambda výrazu nemůže výraz `Await` ve výrazu dotazu být v `Catch` nebo `Finally` bloku [Try... Zachytit... Finally](../statements/try-catch-finally-statement.md), ve výrazu řídicí proměnné smyčky `For` nebo `For Each` smyčky nebo v těle příkazu [SyncLock](../statements/synclock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="e1265-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="e1265-129">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e1265-129">Exceptions</span></span>

<span data-ttu-id="e1265-130">Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e1265-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e1265-131">Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="e1265-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="e1265-132">Operátor `Await` přistupuje k těmto vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="e1265-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="e1265-133">Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, operátor `Await` znovu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e1265-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="e1265-134">Očekáváte-li asynchronní metodu vracející úlohu, která je zrušena, operátor `Await` znovu vyvolá <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="e1265-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="e1265-135">Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.</span><span class="sxs-lookup"><span data-stu-id="e1265-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="e1265-136">Například úloha může být výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1265-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1265-137">Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="e1265-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="e1265-138">Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.</span><span class="sxs-lookup"><span data-stu-id="e1265-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="e1265-139">Příklady zpracování chyb v asynchronních metodách naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e1265-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1265-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1265-140">Example</span></span>

<span data-ttu-id="e1265-141">Následující příklad model Windows Forms ukazuje použití `Await` v asynchronní metodě, `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="e1265-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="e1265-142">Kontrast s chováním této metody s chováním `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="e1265-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="e1265-143">Bez operátoru `Await` `WaitSynchronously` spouští synchronně bez ohledu na použití modifikátoru `Async` v definici a volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jeho těle.</span><span class="sxs-lookup"><span data-stu-id="e1265-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="e1265-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1265-144">See also</span></span>

- [<span data-ttu-id="e1265-145">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="e1265-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e1265-146">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="e1265-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="e1265-147">Async</span><span class="sxs-lookup"><span data-stu-id="e1265-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
