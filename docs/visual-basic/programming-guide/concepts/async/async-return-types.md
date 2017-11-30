---
title: "Asynchronní návratové typy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a62556fb93a3d8547d880e4ea6770b206ead900
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="81594-102">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81594-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="81594-103">Asynchronní metody mít tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void.</span><span class="sxs-lookup"><span data-stu-id="81594-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="81594-104">V jazyce Visual Basic, typ vrácené hodnoty void zapisuje jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupu.</span><span class="sxs-lookup"><span data-stu-id="81594-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="81594-105">Další informace o asynchronní metody najdete v tématu [asynchronní programování s Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="81594-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="81594-106">V jednom z těchto částí je zkontrolován každý návratový typ a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="81594-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81594-107">Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="81594-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="81594-108"><a name="BKMK_TaskTReturnType"></a>Návratový typ Task(T)</span><span class="sxs-lookup"><span data-stu-id="81594-108"><a name="BKMK_TaskTReturnType"></a> Task(T) Return Type</span></span>  
 <span data-ttu-id="81594-109"><xref:System.Threading.Tasks.Task%601> Vrátí typ se používá pro asynchronní metody, která obsahuje [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, ve kterém má operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="81594-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="81594-110">V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metody obsahuje příkaz return, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="81594-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="81594-111">Proto deklarace metody musíte zadat návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="81594-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
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
  
 <span data-ttu-id="81594-112">Když `TaskOfT_MethodAsync` je volána z ve výrazu await výraz await načte celočíselnou hodnotu (hodnota `leisureHours`) který je uložený v úloze, která je vrácena `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="81594-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="81594-113">Další informace o await výrazy najdete v tématu [Await – operátor](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="81594-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="81594-114">Následující kód volá a čeká metoda `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="81594-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="81594-115">Výsledkem je přiřazena k `result1` proměnné.</span><span class="sxs-lookup"><span data-stu-id="81594-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="81594-116">Můžete lépe pochopit, jak tomu oddělením volání `TaskOfT_MethodAsync` z používání `Await`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="81594-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="81594-117">Volání metody `TaskOfT_MethodAsync` , není okamžitě očekávaná vrátí `Task(Of Integer)`, jak očekáváte od deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="81594-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="81594-118">Úloha je přiřazená `integerTask` proměnné v příkladu.</span><span class="sxs-lookup"><span data-stu-id="81594-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="81594-119">Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="81594-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="81594-120">V takovém případě TResult představuje celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="81594-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="81594-121">Když `Await` se použije pro `integerTask`, await vyhodnocen jako obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="81594-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="81594-122">Hodnota je přiřazena k `result2` proměnné.</span><span class="sxs-lookup"><span data-stu-id="81594-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="81594-123"><xref:System.Threading.Tasks.Task%601.Result%2A> Je blokování vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81594-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="81594-124">Pokud se pokusíte k němu přístup před dokončení úkolu, vláken, který je aktuálně aktivní je blokován, dokud úloha dokončí, a hodnota je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="81594-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="81594-125">Ve většině případů byste měli hodnota přistupovat pomocí `Await` místo přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81594-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="81594-126">Zobrazení příkazy v následujícím kódu ověřte, že hodnoty `result1` proměnnou `result2` proměnnou a `Result` vlastnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="81594-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="81594-127">Nezapomeňte, že `Result` vlastnost je blokování vlastnost a neměli přístup než úkolu bylo očekáváno.</span><span class="sxs-lookup"><span data-stu-id="81594-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <span data-ttu-id="81594-128"><a name="BKMK_TaskReturnType"></a>Návratový typ úlohy</span><span class="sxs-lookup"><span data-stu-id="81594-128"><a name="BKMK_TaskReturnType"></a> Task Return Type</span></span>  
 <span data-ttu-id="81594-129">Asynchronní metody, které neobsahují žádný příkaz return nebo obsahují příkaz return, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="81594-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="81594-130">Tyto metody by [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupy napsané spustit synchronně.</span><span class="sxs-lookup"><span data-stu-id="81594-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="81594-131">Pokud používáte `Task` návratový typ pro asynchronní metody, můžete použít volání metody `Await` operátor volajícího dokončení pozastavit, dokud volané asynchronní metody dokončení.</span><span class="sxs-lookup"><span data-stu-id="81594-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="81594-132">V následujícím příkladu, asynchronní metody `Task_MethodAsync` neobsahuje příkaz return.</span><span class="sxs-lookup"><span data-stu-id="81594-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="81594-133">Proto můžete zadat návratový typ `Task` pro metodu, která umožňuje `Task_MethodAsync` k být očekáváno.</span><span class="sxs-lookup"><span data-stu-id="81594-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="81594-134">Definice `Task` neobsahuje typ `Result` vlastnost k uložení návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="81594-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
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
  
 <span data-ttu-id="81594-135">`Task_MethodAsync`je volána a očekávaná pomocí příkazu await místo await výrazu podobné volání příkazu pro synchronního `Sub` nebo metoda vrací void.</span><span class="sxs-lookup"><span data-stu-id="81594-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="81594-136">Použití `Await` operátor v tomto případě neobsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="81594-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="81594-137">Následující kód volá a čeká metoda `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="81594-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="81594-138">Stejně jako v předchozí <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` z používání `Await` operátor, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="81594-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="81594-139">Nezapomeňte však, že `Task` nemá `Result` vlastnost a že při použití operátoru await vytváří žádná hodnota `Task`.</span><span class="sxs-lookup"><span data-stu-id="81594-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="81594-140">Následující kód odděluje volání `Task_MethodAsync` z čeká na úlohy, `Task_MethodAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="81594-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <span data-ttu-id="81594-141"><a name="BKMK_VoidReturnType"></a>Typ vrácené hodnoty void</span><span class="sxs-lookup"><span data-stu-id="81594-141"><a name="BKMK_VoidReturnType"></a> Void Return Type</span></span>  
 <span data-ttu-id="81594-142">Primárním použitím `Sub` procedury je v obslužné rutiny událostí, kde není žádný návratový typ (označované jako typ vrácené hodnoty void v jiných jazycích).</span><span class="sxs-lookup"><span data-stu-id="81594-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="81594-143">Void vrátit lze použít také k přepsání metody vrácení void nebo metod, které provádějí aktivity, které můžou být zařazené do kategorie jako "fire a zapomenete."</span><span class="sxs-lookup"><span data-stu-id="81594-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="81594-144">Ale by měla vrátit `Task` kdykoli je to možné, protože nemůže být očekáváno asynchronní metody vrácení void.</span><span class="sxs-lookup"><span data-stu-id="81594-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="81594-145">Všechny volající tato metoda musí být schopen dál dokončení bez čekání na volané asynchronní metody dokončení a volající musí být nezávislé na všechny hodnoty nebo které generuje asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="81594-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="81594-146">Volající asynchronní metody vrácení void nelze catch výjimky, které jsou vyvolány z metody a může způsobit selhání aplikace jsou takové neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="81594-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="81594-147">Pokud dojde k výjimce v asynchronní metody, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložen ve vrácené úloh a znovu vyvolány, když je očekáváno úlohu.</span><span class="sxs-lookup"><span data-stu-id="81594-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="81594-148">Proto se ujistěte, že asynchronní metody, která může vytvořit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že jsou očekáváno volání metody.</span><span class="sxs-lookup"><span data-stu-id="81594-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="81594-149">Další informace o tom, jak zachycení výjimek v asynchronní metody najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="81594-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="81594-150">Následující kód definuje obslužnou rutinu události asynchronní.</span><span class="sxs-lookup"><span data-stu-id="81594-150">The following code defines an async event handler.</span></span>  
  
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
  
##  <span data-ttu-id="81594-151"><a name="BKMK_Example"></a>Úplný příklad</span><span class="sxs-lookup"><span data-stu-id="81594-151"><a name="BKMK_Example"></a> Complete Example</span></span>  
 <span data-ttu-id="81594-152">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="81594-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="81594-153">Pokud chcete spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="81594-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="81594-154">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81594-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="81594-155">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="81594-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="81594-156">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="81594-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="81594-157">V **nainstalovaná**, **šablony** kategorie, zvolte **jazyka Visual Basic**a potom zvolte **Windows**.</span><span class="sxs-lookup"><span data-stu-id="81594-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="81594-158">Zvolte **aplikaci WPF** ze seznamu typy projektů.</span><span class="sxs-lookup"><span data-stu-id="81594-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="81594-159">Zadejte `AsyncReturnTypes` jako název projektu a klikněte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="81594-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="81594-160">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="81594-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="81594-161">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="81594-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="81594-162">Pokud na kartě se nezobrazí, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="81594-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="81594-163">V **XAML** okno MainWindow.xaml, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="81594-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="81594-164">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** okno MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="81594-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="81594-165">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="81594-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="81594-166">Nahraďte kód v MainWindow.xaml.vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="81594-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
9. <span data-ttu-id="81594-167">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="81594-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="81594-168">By se zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="81594-168">The following output should appear.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81594-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="81594-169">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [<span data-ttu-id="81594-170">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81594-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="81594-171">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81594-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [<span data-ttu-id="81594-172">Asynchronní</span><span class="sxs-lookup"><span data-stu-id="81594-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="81594-173">Await – operátor</span><span class="sxs-lookup"><span data-stu-id="81594-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
