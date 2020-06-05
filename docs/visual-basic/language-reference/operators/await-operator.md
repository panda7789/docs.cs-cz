---
title: Await – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371827"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="66848-102">Await – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66848-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="66848-103">Operátor lze použít `Await` pro operand v asynchronní metodě nebo výrazu lambda pro pozastavení provádění metody, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="66848-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="66848-104">Úkol představuje probíhající práci.</span><span class="sxs-lookup"><span data-stu-id="66848-104">The task represents ongoing work.</span></span>

<span data-ttu-id="66848-105">Metoda, ve které `Await` se používá, musí mít modifikátor [Async](../modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="66848-105">The method in which `Await` is used must have an [Async](../modifiers/async.md) modifier.</span></span> <span data-ttu-id="66848-106">Taková metoda, která je definována pomocí `Async` modifikátoru a obvykle obsahuje jeden nebo více `Await` výrazů, je označována jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="66848-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="66848-107">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="66848-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="66848-108">Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="66848-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="66848-109">Úkol, na který operátor použijete, `Await` je obvykle návratovou hodnotou z volání metody, která implementuje [asynchronní vzor založený na úlohách](https://www.microsoft.com/download/details.aspx?id=19957), to znamená, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="66848-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="66848-110">V následujícím kódu <xref:System.Net.Http.HttpClient> Metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí hodnotu `getContentsTask` , `Task(Of Byte())` .</span><span class="sxs-lookup"><span data-stu-id="66848-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="66848-111">Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="66848-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="66848-112">`Await`Operátor je použit na `getContentsTask` pro pozastavení provádění v, `SumPageSizesAsync` dokud `getContentsTask` není dokončeno.</span><span class="sxs-lookup"><span data-stu-id="66848-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="66848-113">Mezitím se ovládací prvek vrátí volajícímu `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="66848-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="66848-114">Po `getContentsTask` dokončení se `Await` výraz vyhodnotí jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="66848-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

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
> <span data-ttu-id="66848-115">Úplný příklad najdete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="66848-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="66848-116">Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="66848-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="66848-117">Příklad je v projektu AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="66848-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="66848-118">Pokud `Await` je použita na výsledek volání metody, která vrací `Task(Of TResult)` , je typ `Await` výrazu TResult.</span><span class="sxs-lookup"><span data-stu-id="66848-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="66848-119">Pokud `Await` je použita na výsledek volání metody, která vrací `Task` , `Await` výraz nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="66848-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="66848-120">Rozdíl je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="66848-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="66848-121">`Await`Výraz nebo příkaz neblokuje vlákno, ve kterém je prováděno.</span><span class="sxs-lookup"><span data-stu-id="66848-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="66848-122">Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody za `Await` výraz, jako pokračování na očekávaném úkolu.</span><span class="sxs-lookup"><span data-stu-id="66848-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="66848-123">Ovládací prvek se pak vrátí volajícímu asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="66848-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="66848-124">Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.</span><span class="sxs-lookup"><span data-stu-id="66848-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="66848-125">`Await`Výraz může nastat pouze v těle přímo ohraničující metody nebo lambda výraz, který je označen `Async` modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="66848-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="66848-126">Termín *await* slouží jako klíčové slovo pouze v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="66848-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="66848-127">Jinde je interpretován jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="66848-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="66848-128">V rámci `Async` metody nebo výrazu lambda se `Await` výraz nemůže vyskytovat ve výrazu dotazu v `Catch` `Finally` bloku nebo bloku [Try... Zachytit... Finally](../statements/try-catch-finally-statement.md), ve výrazu řídicí proměnné smyčky `For` smyčky nebo nebo `For Each` v těle [SyncLock](../statements/synclock-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="66848-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="66848-129">Výjimky</span><span class="sxs-lookup"><span data-stu-id="66848-129">Exceptions</span></span>

<span data-ttu-id="66848-130">Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="66848-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="66848-131">Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="66848-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="66848-132">Tento `Await` operátor přistupuje k těmto vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="66848-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="66848-133">Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, `Await` operátor znovu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="66848-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="66848-134">Pokud očekáváte asynchronní metodu vracející úlohu, která je zrušena, operátor znovu `Await` vyvolá <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="66848-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="66848-135">Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.</span><span class="sxs-lookup"><span data-stu-id="66848-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="66848-136">Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66848-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66848-137">Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="66848-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="66848-138">Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.</span><span class="sxs-lookup"><span data-stu-id="66848-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="66848-139">Příklady zpracování chyb v asynchronních metodách naleznete v tématu [Try... Zachytit... Finally – příkaz](../statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="66848-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="66848-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="66848-140">Example</span></span>

<span data-ttu-id="66848-141">Následující příklad model Windows Forms ukazuje použití `Await` v asynchronní metodě, `WaitAsynchronouslyAsync` .</span><span class="sxs-lookup"><span data-stu-id="66848-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="66848-142">Kontrast s chováním této metody s chováním `WaitSynchronously` .</span><span class="sxs-lookup"><span data-stu-id="66848-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="66848-143">Bez `Await` operátora `WaitSynchronously` běží synchronně navzdory použití `Async` modifikátoru v definici a volání do <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jeho těla.</span><span class="sxs-lookup"><span data-stu-id="66848-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66848-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="66848-144">See also</span></span>

- [<span data-ttu-id="66848-145">Asynchronní programování s modifikátorem Async a operátoru await</span><span class="sxs-lookup"><span data-stu-id="66848-145">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="66848-146">Návod: přístup k webu pomocí modifikátoru Async a operátoru await</span><span class="sxs-lookup"><span data-stu-id="66848-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="66848-147">Async</span><span class="sxs-lookup"><span data-stu-id="66848-147">Async</span></span>](../modifiers/async.md)
