---
title: Asynchronní návratové typy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: a5553070dd68a0bc3eaad1c5e8c000f7a31f8783
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423960"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="34b0e-102">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b0e-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="34b0e-103">Asynchronní metody mají tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void.</span><span class="sxs-lookup"><span data-stu-id="34b0e-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="34b0e-104">V Visual Basic typ vrácené hodnoty void je zapsán jako procedura [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) .</span><span class="sxs-lookup"><span data-stu-id="34b0e-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="34b0e-105">Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="34b0e-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="34b0e-106">Každý návratový typ je zkontrolován v jednom z následujících sekcí a můžete najít úplný příklad, který používá všechny tři typy na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="34b0e-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="34b0e-107">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="34b0e-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_TaskTReturnType"></a><span data-ttu-id="34b0e-108">Návratový typ úlohy (T)</span><span class="sxs-lookup"><span data-stu-id="34b0e-108">Task(T) Return Type</span></span>

<span data-ttu-id="34b0e-109"><xref:System.Threading.Tasks.Task%601> návratový typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../../visual-basic/language-reference/statements/return-statement.md) , ve kterém je operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="34b0e-110">V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metoda obsahuje příkaz return, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="34b0e-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="34b0e-111">Proto musí deklarace metody určit návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="34b0e-112">Když je volána `TaskOfT_MethodAsync` v rámci výrazu await, výraz await načte celočíselnou hodnotu (hodnotu `leisureHours`), která je uložena v úloze, kterou vrací `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="34b0e-113">Další informace o výrazech await naleznete v tématu [operátor await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="34b0e-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="34b0e-114">Následující kód volá metodu and očekává `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="34b0e-115">Výsledek je přiřazen proměnné `result1`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="34b0e-116">Můžete lépe porozumět tomu, jak se to stane, oddělením volání `TaskOfT_MethodAsync` od aplikace `Await`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="34b0e-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="34b0e-117">Volání metody `TaskOfT_MethodAsync`, které není okamžitě očekáváno, vrací `Task(Of Integer)`, jak byste očekávali od deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="34b0e-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="34b0e-118">Úloha je přiřazena k proměnné `integerTask` v příkladu.</span><span class="sxs-lookup"><span data-stu-id="34b0e-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="34b0e-119">Vzhledem k tomu, že `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje vlastnost <xref:System.Threading.Tasks.Task%601.Result> typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="34b0e-120">V tomto případě TResult představuje typ Integer.</span><span class="sxs-lookup"><span data-stu-id="34b0e-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="34b0e-121">Při použití `Await` pro `integerTask`se výraz await vyhodnocuje na obsah vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A> `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="34b0e-122">Hodnota je přiřazena proměnné `result2`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="34b0e-123">Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost blokující.</span><span class="sxs-lookup"><span data-stu-id="34b0e-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="34b0e-124">Pokud se pokusíte o přístup k tomuto úkolu před jeho dokončením, bude vlákno, které je aktuálně aktivní, blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="34b0e-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="34b0e-125">Ve většině případů byste měli k hodnotě přistupovat pomocí `Await` místo přímého přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="34b0e-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="34b0e-126">Příkazy zobrazení v následujícím kódu ověřují, zda jsou hodnoty proměnné `result1`, `result2` proměnnou a vlastnost `Result` stejné.</span><span class="sxs-lookup"><span data-stu-id="34b0e-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="34b0e-127">Mějte na paměti, že vlastnost `Result` je vlastnost blokující a neměla by k ní být přistupovaná před tím, než byla úloha očekávána.</span><span class="sxs-lookup"><span data-stu-id="34b0e-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a><span data-ttu-id="34b0e-128">Návratový typ úlohy</span><span class="sxs-lookup"><span data-stu-id="34b0e-128">Task Return Type</span></span>

<span data-ttu-id="34b0e-129">Asynchronní metody, které neobsahují příkaz return nebo obsahující příkaz return, který nevrací operand, obvykle mají návratový typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="34b0e-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="34b0e-130">Tyto metody by byly procedury [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , pokud byly zapsány pro spuštění synchronně.</span><span class="sxs-lookup"><span data-stu-id="34b0e-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="34b0e-131">Použijete-li návratový typ `Task` pro asynchronní metodu, volající metoda může použít operátor `Await` k pozastavení dokončování volajícího až do dokončení volané asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="34b0e-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="34b0e-132">V následujícím příkladu asynchronní metoda `Task_MethodAsync` neobsahuje příkaz return.</span><span class="sxs-lookup"><span data-stu-id="34b0e-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="34b0e-133">Proto zadáte návratový typ `Task` pro metodu, která umožňuje očekávat `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="34b0e-134">Definice typu `Task` neobsahuje vlastnost `Result` pro uložení návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="34b0e-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

<span data-ttu-id="34b0e-135">`Task_MethodAsync` se volá a očekává se pomocí příkazu await namísto výrazu await, podobně jako volání příkazu pro synchronní `Sub` nebo metodu vracející typ void.</span><span class="sxs-lookup"><span data-stu-id="34b0e-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="34b0e-136">Použití operátoru `Await` v tomto případě nevytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34b0e-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="34b0e-137">Následující kód volá metodu and očekává `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34b0e-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="34b0e-138">Stejně jako v předchozím příkladu <xref:System.Threading.Tasks.Task%601> můžete oddělit volání `Task_MethodAsync` od aplikace operátoru `Await`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="34b0e-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="34b0e-139">Nezapomeňte však, že `Task` nemá vlastnost `Result` a že při použití operátoru await na `Task` není vytvořena žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="34b0e-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="34b0e-140">Následující kód odděluje volání `Task_MethodAsync` od čekání na úkol, který `Task_MethodAsync` vrací.</span><span class="sxs-lookup"><span data-stu-id="34b0e-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a><span data-ttu-id="34b0e-141">Návratový typ void</span><span class="sxs-lookup"><span data-stu-id="34b0e-141">Void Return Type</span></span>

<span data-ttu-id="34b0e-142">Primární použití procedur `Sub` je v obslužných rutinách událostí, kde neexistuje návratový typ (v jiných jazycích se označuje jako návratový typ void).</span><span class="sxs-lookup"><span data-stu-id="34b0e-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="34b0e-143">Návratový typ void také lze použít k přepsání metod vracejících anulování nebo pro metody, které provádějí aktivity, které mohou být zařazeny do kategorie "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="34b0e-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="34b0e-144">Měli byste však vracet `Task` všude, kde je to možné, protože asynchronní metodu vracející anulování nelze očekávat.</span><span class="sxs-lookup"><span data-stu-id="34b0e-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="34b0e-145">Každý volající takové metody musí být schopný pokračovat v dokončování bez čekání na dokončení volané asynchronní metody a volající musí být nezávislý na všech hodnotách nebo výjimkách, které asynchronní metoda generuje.</span><span class="sxs-lookup"><span data-stu-id="34b0e-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="34b0e-146">Volající asynchronní metody vracející hodnotu void nemůže zachytit výjimky, které jsou vyvolány z metody, a tyto neošetřené výjimky pravděpodobně způsobí selhání aplikace.</span><span class="sxs-lookup"><span data-stu-id="34b0e-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="34b0e-147">Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, je výjimka uložena v vrácené úloze a znovu vyvolána, když je úkol očekáván.</span><span class="sxs-lookup"><span data-stu-id="34b0e-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="34b0e-148">Proto se ujistěte, že jakákoliv asynchronní metoda, která může vyvolat výjimku, má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávána.</span><span class="sxs-lookup"><span data-stu-id="34b0e-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="34b0e-149">Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34b0e-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="34b0e-150">Následující kód definuje asynchronní obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="34b0e-150">The following code defines an async event handler.</span></span>

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

## <a name="BKMK_Example"></a><span data-ttu-id="34b0e-151">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="34b0e-151">Complete Example</span></span>

<span data-ttu-id="34b0e-152">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="34b0e-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="34b0e-153">Chcete-li spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="34b0e-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="34b0e-154">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34b0e-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="34b0e-155">Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="34b0e-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="34b0e-156">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="34b0e-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="34b0e-157">V kategorii **nainstalováno**, **šablony** zvolte možnost **Visual Basic**a pak zvolte možnost **Windows**.</span><span class="sxs-lookup"><span data-stu-id="34b0e-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="34b0e-158">V seznamu typů projektů vyberte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="34b0e-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="34b0e-159">Jako název projektu zadejte `AsyncReturnTypes` a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="34b0e-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="34b0e-160">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="34b0e-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="34b0e-161">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="34b0e-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="34b0e-162">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="34b0e-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="34b0e-163">V okně **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="34b0e-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="34b0e-164">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v okně **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="34b0e-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="34b0e-165">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="34b0e-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="34b0e-166">Nahraďte kód v souboru MainWindow. XAML. vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="34b0e-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

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
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. <span data-ttu-id="34b0e-167">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="34b0e-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="34b0e-168">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="34b0e-168">The following output should appear:</span></span>

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a><span data-ttu-id="34b0e-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34b0e-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="34b0e-170">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b0e-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="34b0e-171">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b0e-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="34b0e-172">Async</span><span class="sxs-lookup"><span data-stu-id="34b0e-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="34b0e-173">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="34b0e-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
