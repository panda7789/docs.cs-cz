---
title: Await – operátor (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d639d1398c0f783fcfa40ee9ff278922fd6fc7b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="88e27-102">Await – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88e27-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="88e27-103">Můžete použít `Await` operátor a operand ve výrazu asynchronní metody nebo lambda pozastavit provádění metody až do dokončení awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="88e27-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="88e27-104">Úloha reprezentuje probíhající práce.</span><span class="sxs-lookup"><span data-stu-id="88e27-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="88e27-105">Metoda, ve kterém `Await` slouží musí mít [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="88e27-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="88e27-106">Tato metoda, definované pomocí `Async` modifikátor a obvykle obsahující jednu nebo více `Await` výrazy, se označuje jako *asynchronní metody*.</span><span class="sxs-lookup"><span data-stu-id="88e27-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e27-107">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="88e27-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="88e27-108">Úvod do asynchronního programování, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="88e27-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="88e27-109">Obvykle úloh, do které můžete použít `Await` operátor je vrácená hodnota z volání metody, která implementuje [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), která je <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="88e27-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="88e27-110">V následujícím kódu <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`, `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="88e27-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="88e27-111">Tato úloha je promise k vytvoření skutečné bajtové pole po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="88e27-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="88e27-112">`Await` Operátor se použije pro `getContentsTask` pozastavit provádění v `SumPageSizesAsync` dokud `getContentsTask` dokončení.</span><span class="sxs-lookup"><span data-stu-id="88e27-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="88e27-113">Do té doby ovládací prvek se vrátí do volajícího `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="88e27-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="88e27-114">Když `getContentsTask` po dokončení, `Await` výraz vyhodnocen jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="88e27-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
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
>  <span data-ttu-id="88e27-115">Úplný příklad najdete v tématu [návod: přístup k webu pomocí modifikátoru Async a Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="88e27-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="88e27-116">Si můžete stáhnout ukázkový z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) na webu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88e27-116">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="88e27-117">Příkladem je v AsyncWalkthrough_HttpClient projektu.</span><span class="sxs-lookup"><span data-stu-id="88e27-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="88e27-118">Pokud `Await` se použije na výsledek volání metody, která vrátí `Task(Of TResult)`, typ `Await` TResult je výraz.</span><span class="sxs-lookup"><span data-stu-id="88e27-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="88e27-119">Pokud `Await` se použije na výsledek volání metody, která vrátí `Task`, `Await` výraz nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="88e27-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="88e27-120">Následující příklad ukazuje rozdíl.</span><span class="sxs-lookup"><span data-stu-id="88e27-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="88e27-121">`Await` Výraz nebo příkaz neblokuje vláken, na kterém je prováděna.</span><span class="sxs-lookup"><span data-stu-id="88e27-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="88e27-122">Místo toho ji způsobí, že kompilátor registrace zbytek asynchronní metody po `Await` výraz. pokračování v awaited úloze.</span><span class="sxs-lookup"><span data-stu-id="88e27-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="88e27-123">Ovládací prvek pak vrátí volajícímu asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="88e27-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="88e27-124">Po dokončení úlohy vyvolá jeho pokračování a spouštění obnoví asynchronní metody, kde bylo přerušeno.</span><span class="sxs-lookup"><span data-stu-id="88e27-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="88e27-125">`Await` Výrazu může dojít pouze v těle okamžitě nadřazených metoda nebo lambda výrazu, která je označena kvalifikátorem `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="88e27-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="88e27-126">Termín *Await* slouží jako klíčové slovo pouze v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="88e27-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="88e27-127">Jinam je interpretován jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="88e27-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="88e27-128">V rámci asynchronní metody nebo lambda výrazu `Await` výraz nemůže proběhnout ve výrazu dotazu v `catch` nebo `finally` blokovat z [zkuste... Catch... Nakonec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) příkaz, ve smyčce řízení proměnné výrazu `For` nebo `For Each` smyčky, nebo v těle [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="88e27-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="88e27-129">Výjimky</span><span class="sxs-lookup"><span data-stu-id="88e27-129">Exceptions</span></span>  
 <span data-ttu-id="88e27-130">Většina asynchronní metody vrátit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="88e27-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="88e27-131">Vlastnosti vrácený úlohy přenosu informací o jeho stav a historie, například zda byl dokončen, jestli asynchronní metody způsobila výjimku nebo byla zrušena a jaké konečný výsledek je.</span><span class="sxs-lookup"><span data-stu-id="88e27-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="88e27-132">`Await` Operátor přistupuje k tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="88e27-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="88e27-133">Pokud await vrácení úloh asynchronní metody, které způsobí výjimku, `Await` operátor znovu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="88e27-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="88e27-134">Pokud await vrácení úloh asynchronní metody, kterou zruší, `Await` znovu vyvolá operátor <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="88e27-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="88e27-135">Jeden úkol, který je v chybovém stavu skutečnost více výjimek.</span><span class="sxs-lookup"><span data-stu-id="88e27-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="88e27-136">Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88e27-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="88e27-137">Pokud jste await takové úlohy, znovu vyvolá operaci await pouze jeden z výjimky.</span><span class="sxs-lookup"><span data-stu-id="88e27-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="88e27-138">Nelze však předpovědi, které výjimky znovu vyvolány.</span><span class="sxs-lookup"><span data-stu-id="88e27-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="88e27-139">Příklady zpracování chyb v asynchronní metody naleznete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88e27-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e27-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e27-140">Example</span></span>  
 <span data-ttu-id="88e27-141">Windows Forms následující příklad ukazuje použití `Await` v použití asynchronní metody `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="88e27-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="88e27-142">Kontrastu chováním této metody s chováním `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="88e27-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="88e27-143">Bez `Await` operátor, `WaitSynchronously` spouští synchronně navzdory použití `Async` modifikátor v jeho definice a volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="88e27-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88e27-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="88e27-144">See Also</span></span>  
 [<span data-ttu-id="88e27-145">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="88e27-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="88e27-146">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="88e27-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="88e27-147">Asynchronní</span><span class="sxs-lookup"><span data-stu-id="88e27-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
