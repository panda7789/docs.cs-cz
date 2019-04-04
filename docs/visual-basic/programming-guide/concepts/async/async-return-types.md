---
title: Asynchronní návratové typy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 7a8bc3ba98da830c8415284771460a25e0927895
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838349"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="2d173-102">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d173-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="2d173-103">Asynchronní metody mají tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void.</span><span class="sxs-lookup"><span data-stu-id="2d173-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="2d173-104">V jazyce Visual Basic je návratový typ void napsán jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postup.</span><span class="sxs-lookup"><span data-stu-id="2d173-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="2d173-105">Další informace o metodách async naleznete v tématu [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d173-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="2d173-106">Každý návratový typ je zkontrolován v jedné z následujících částí a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2d173-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d173-107">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="2d173-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="2d173-108">Návratový typ Task(T)</span><span class="sxs-lookup"><span data-stu-id="2d173-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="2d173-109"><xref:System.Threading.Tasks.Task%601> Typ vrácení se používá pro asynchronní metodu, která obsahuje [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkazem, ve kterém je operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="2d173-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="2d173-110">V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metoda obsahuje příkaz return, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="2d173-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="2d173-111">Proto deklarace metody musíte zadat návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="2d173-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 <span data-ttu-id="2d173-112">Když `TaskOfT_MethodAsync` je volána z v rámci výrazu await výraz await získá celočíselnou hodnota (hodnotu `leisureHours`), která je uložena v úkolu, který je vrácený `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="2d173-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="2d173-113">Další informace o výrazech await naleznete [operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2d173-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="2d173-114">Následující kód volá a čeká metodu `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="2d173-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="2d173-115">Výsledek je přiřazen k `result1` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d173-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="2d173-116">Můžete lépe pochopit, jak to probíhá oddělením volání `TaskOfT_MethodAsync` od aplikace `Await`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2d173-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="2d173-117">Volání metody `TaskOfT_MethodAsync` , které není okamžitě očekáváno, vrátí `Task(Of Integer)`, dle očekávání od deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="2d173-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="2d173-118">Úkol je přidělen `integerTask` proměnné v příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d173-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="2d173-119">Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="2d173-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="2d173-120">V tomto případě TResult představuje typ integer.</span><span class="sxs-lookup"><span data-stu-id="2d173-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="2d173-121">Když `Await` platí pro `integerTask`, výraz await se vyhodnocuje na obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="2d173-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="2d173-122">Je hodnota přiřazená `result2` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d173-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2d173-123"><xref:System.Threading.Tasks.Task%601.Result%2A> Vlastností je vlastnost blokování.</span><span class="sxs-lookup"><span data-stu-id="2d173-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="2d173-124">Pokud se pokusíte o přístup k ní před dokončením její úlohy, blokovaný vláknem, které je právě aktivní až do dokončení úlohy a hodnota je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2d173-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="2d173-125">Ve většině případů byste měli přistupovat k hodnotě pomocí `Await` namísto přímého přístupu.</span><span class="sxs-lookup"><span data-stu-id="2d173-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="2d173-126">Zobrazení příkazů v následujícím kódu ověřte, že hodnoty `result1` proměnné, `result2` proměnnou a `Result` vlastnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="2d173-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="2d173-127">Mějte na paměti, `Result` vlastností je vlastnost blokování a by neměl být přístupný, než bylo očekáváno úkolem.</span><span class="sxs-lookup"><span data-stu-id="2d173-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="2d173-128">Návratový typ úlohy</span><span class="sxs-lookup"><span data-stu-id="2d173-128">Task Return Type</span></span>  
 <span data-ttu-id="2d173-129">Asynchronní metody, které neobsahují příkaz return nebo obsahující příkaz return, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="2d173-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="2d173-130">Tyto metody by měly [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupy, pokud byly napsány, aby běžely synchronně.</span><span class="sxs-lookup"><span data-stu-id="2d173-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="2d173-131">Pokud používáte `Task` návratový typ pro asynchronní metodu, volající metoda můžete použít `Await` operátor k pozastavení dokončení volajícího až do dokončení volané asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d173-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="2d173-132">V následujícím příkladu asynchronní metoda `Task_MethodAsync` neobsahuje příkaz return.</span><span class="sxs-lookup"><span data-stu-id="2d173-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="2d173-133">Tedy zadáte návratový typ `Task` pro metodu, která umožňuje `Task_MethodAsync` do ní použít operátor await.</span><span class="sxs-lookup"><span data-stu-id="2d173-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="2d173-134">Definice `Task` neobsahuje `Result` vlastnost k ukládání vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d173-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="2d173-135">`Task_MethodAsync` je volán a očekáván pomocí příkazu await namísto výrazu await, podobného volání příkazu pro synchronní `Sub` nebo metody vracející hodnotu void.</span><span class="sxs-lookup"><span data-stu-id="2d173-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="2d173-136">Použití `Await` operátor v tomto případě nevytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d173-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="2d173-137">Následující kód volá a čeká metodu `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="2d173-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="2d173-138">Stejně jako v předchozím <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` od aplikace `Await` operátoru, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2d173-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="2d173-139">Nezapomeňte však, že `Task` nemá `Result` vlastnost a že se při použití operátoru await nevytvoří žádná hodnota `Task`.</span><span class="sxs-lookup"><span data-stu-id="2d173-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="2d173-140">Následující kód oddělí volání `Task_MethodAsync` z čekajícího na úkol, který `Task_MethodAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="2d173-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="2d173-141">Návratový typ void</span><span class="sxs-lookup"><span data-stu-id="2d173-141">Void Return Type</span></span>  
 <span data-ttu-id="2d173-142">Primární použití `Sub` postupy je v obslužných rutinách událostí, kde neexistuje žádný návratový typ (označované jako návratový typ void v jiných jazycích).</span><span class="sxs-lookup"><span data-stu-id="2d173-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="2d173-143">Vrácení void lze použít také k přepsání metod vracejících void nebo pro metody, které vykonávají činnosti, které lze označit jako "vypal a zapomeň."</span><span class="sxs-lookup"><span data-stu-id="2d173-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="2d173-144">Nicméně, měli byste vrátit `Task` kdykoli je to možné, protože asynchronní metody vracející typ void nemůže být očekávána.</span><span class="sxs-lookup"><span data-stu-id="2d173-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="2d173-145">Jakýkoli volající této metody musí být schopen pokračovat v dokončení bez čekání na dokončení volané asynchronní metody a volající musí být nezávislé na všech hodnotách nebo výjimkách, které generuje asynchronní metoda.</span><span class="sxs-lookup"><span data-stu-id="2d173-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="2d173-146">Volající asynchronní metody vracející typ void nemůže zachytit výjimky, které jsou vyvolány z metody a takové neošetřené výjimky mohou způsobit selhání aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d173-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="2d173-147">Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložen v rámci vrácené úlohy a znovu vyvolána při očekávání úkolu.</span><span class="sxs-lookup"><span data-stu-id="2d173-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="2d173-148">Proto se ujistěte, že asynchronní metody, které mohou způsobit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávaná.</span><span class="sxs-lookup"><span data-stu-id="2d173-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="2d173-149">Další informace o tom, jak zachytávat výjimky v asynchronních metodách, naleznete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2d173-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="2d173-150">Následující kód definuje asynchronní obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="2d173-150">The following code defines an async event handler.</span></span>  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> <span data-ttu-id="2d173-151">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="2d173-151">Complete Example</span></span>  
 <span data-ttu-id="2d173-152">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódů z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2d173-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="2d173-153">Spusťte projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="2d173-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="2d173-154">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d173-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2d173-155">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2d173-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="2d173-156">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2d173-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2d173-157">V **nainstalováno**, **šablony** kategorie, zvolte **jazyka Visual Basic**a klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="2d173-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="2d173-158">Zvolte **aplikace WPF** ze seznamu typů projektů.</span><span class="sxs-lookup"><span data-stu-id="2d173-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="2d173-159">Zadejte `AsyncReturnTypes` jako název projektu a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2d173-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="2d173-160">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="2d173-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="2d173-161">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="2d173-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="2d173-162">Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="2d173-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="2d173-163">V **XAML** okno soubor mainwindow.XAML nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2d173-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="2d173-164">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** okna souboru mainwindow.XAML.</span><span class="sxs-lookup"><span data-stu-id="2d173-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="2d173-165">V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="2d173-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="2d173-166">Nahraďte kód v souboru MainWindow.xaml.vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2d173-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="2d173-167">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2d173-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="2d173-168">By se zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="2d173-168">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d173-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d173-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="2d173-170">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d173-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="2d173-171">Tok řízení v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d173-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="2d173-172">Async</span><span class="sxs-lookup"><span data-stu-id="2d173-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="2d173-173">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="2d173-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
