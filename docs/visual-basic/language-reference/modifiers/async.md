---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 244f468d9432e132c93ae8272d51098f86ad439a
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753341"
---
# <a name="async-visual-basic"></a><span data-ttu-id="fb8e1-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb8e1-102">Async (Visual Basic)</span></span>
<span data-ttu-id="fb8e1-103">`Async` Modifikátor znamená, že metoda nebo [výrazu lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) , upraví je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="fb8e1-104">Tyto metody jsou označovány jako *asynchronní metody*.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-104">Such methods are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="fb8e1-105">Asynchronní metoda představuje pohodlný způsob, jak provádět potenciálně dlouhotrvající práci bez blokování vlákna volání.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="fb8e1-106">Volající asynchronní metody může pokračovat v práci bez čekání na dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb8e1-107">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="fb8e1-108">Úvod do asynchronního programování, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb8e1-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="fb8e1-109">Následující příklad ukazuje strukturu asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="fb8e1-110">Podle úmluvy názvy asynchronních metod končí slovem „Async“.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-110">By convention, async method names end in "Async."</span></span>  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 <span data-ttu-id="fb8e1-111">Obvykle změnit metodu `Async` – klíčové slovo, obsahuje nejméně jeden [Await](../../../visual-basic/language-reference/modifiers/async.md) výraz nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="fb8e1-112">Metoda pracuje synchronně, dokud nedosáhne prvního operátoru `Await`. V tomto okamžiku se provádění metody pozastaví až do dokončení očekávané úlohy.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="fb8e1-113">Během této doby je řízení předáno zpět volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="fb8e1-114">Pokud metoda neobsahuje výraz nebo příkaz `Await`, není provádění metody pozastaveno a provede se stejně jako synchronní metoda.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-114">If the method doesn’t contain an `Await` expression or statement, the method isn’t suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="fb8e1-115">Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují slovo `Await`, protože tato situace může značit chybu.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="fb8e1-116">Další informace najdete v tématu [Chyba kompilátoru](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="fb8e1-116">For more information, see the [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span></span>  
  
 <span data-ttu-id="fb8e1-117">Klíčové slovo `Async` je nerezervované klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="fb8e1-118">Pokud modifikuje metodu nebo výraz lambda, je klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="fb8e1-119">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-119">In all other contexts, it is interpreted as an identifier.</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="fb8e1-120">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="fb8e1-120">Return Types</span></span>  
 <span data-ttu-id="fb8e1-121">Asynchronní metody je buď [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupu nebo [funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) postup, který má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="fb8e1-122">Metodu nelze deklarovat všechny [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="fb8e1-123">Zadáte `Task(Of TResult)` pro návratový typ asynchronní metody Pokud [vrátit](../../../visual-basic/language-reference/statements/return-statement.md) příkaz metody má operand typu TResult.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="fb8e1-124">Používáte `Task` Pokud žádná smysluplný hodnota je vrácena, pokud je metoda dokončena.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="fb8e1-125">To znamená, že volání metody vrací typ `Task`, ale když je typ `Task` dokončen, žádný z příkazů `Await` čekajících na tento typ `Task` nevrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>  
  
 <span data-ttu-id="fb8e1-126">Asynchronní podprogramy se používají především pro definování obslužných rutin událostí, kde je nutná procedura `Sub`.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="fb8e1-127">Volající asynchronního podprogramu ji nemůže očekávat ani zachytávat výjimky, které tato metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="fb8e1-128">Další informace a příklady naleznete v tématu [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="fb8e1-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb8e1-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb8e1-129">Example</span></span>  
 <span data-ttu-id="fb8e1-130">Následující příklady ukazují asynchronní obslužnou rutinu události, asynchronní výraz lambda a asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="fb8e1-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="fb8e1-131">Úplný příklad, který používá tyto prvky, najdete v části [návod: přístup k webu pomocí modifikátoru Async a Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="fb8e1-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="fb8e1-132">Si můžete stáhnout kód návod z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="fb8e1-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb8e1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb8e1-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="fb8e1-134">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="fb8e1-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="fb8e1-135">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="fb8e1-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="fb8e1-136">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="fb8e1-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
