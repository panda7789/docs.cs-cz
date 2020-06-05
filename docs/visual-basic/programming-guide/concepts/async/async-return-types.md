---
title: Asynchronní návratové typy
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 5d19fc9831580412da24333be0885fce55384658
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396711"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="6d5a8-102">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d5a8-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="6d5a8-103">Asynchronní metody mají tři možné návratové typy: <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.Task> a void.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="6d5a8-104">V Visual Basic typ vrácené hodnoty void je zapsán jako procedura [Sub](../../language-features/procedures/sub-procedures.md) .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-104">In Visual Basic, the void return type is written as a [Sub](../../language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="6d5a8-105">Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="6d5a8-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="6d5a8-106">Každý návratový typ je zkontrolován v jednom z následujících sekcí a můžete najít úplný příklad, který používá všechny tři typy na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="6d5a8-107">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a><span data-ttu-id="6d5a8-108">Návratový typ úlohy (T)</span><span class="sxs-lookup"><span data-stu-id="6d5a8-108">Task(T) Return Type</span></span>

<span data-ttu-id="6d5a8-109"><xref:System.Threading.Tasks.Task%601>Návratový typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../language-reference/statements/return-statement.md) , ve kterém je operand typu `TResult` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="6d5a8-110">V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metoda obsahuje příkaz return, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="6d5a8-111">Proto deklarace metody musí specifikovat návratový typ `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="6d5a8-112">Když `TaskOfT_MethodAsync` je volána z výrazu await, výraz await načte celočíselnou hodnotu (hodnotu `leisureHours` ), která je uložena v úkolu, který vrací `TaskOfT_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6d5a8-113">Další informace o výrazech await naleznete v tématu [operátor await](../../../language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6d5a8-113">For more information about await expressions, see [Await Operator](../../../language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="6d5a8-114">Následující kód volá a očekává metodu `TaskOfT_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6d5a8-115">Výsledek je přiřazen `result1` proměnné.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="6d5a8-116">Můžete lépe porozumět tomu, jak se to stane, oddělením volání `TaskOfT_MethodAsync` z aplikace `Await` , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="6d5a8-117">Volání metody `TaskOfT_MethodAsync` , která není okamžitě očekávána `Task(Of Integer)` , vrátí, jak byste očekávali od deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="6d5a8-118">Úkol je přiřazen k `integerTask` proměnné v příkladu.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="6d5a8-119">Protože `integerTask` je <xref:System.Threading.Tasks.Task%601> , obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="6d5a8-120">V tomto případě TResult představuje typ Integer.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="6d5a8-121">Při `Await` použití na je `integerTask` Výraz Await vyhodnocen jako obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti `integerTask` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="6d5a8-122">Hodnota je přiřazena `result2` proměnné.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="6d5a8-123"><xref:System.Threading.Tasks.Task%601.Result%2A>Vlastnost je vlastnost blokování.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="6d5a8-124">Pokud se pokusíte o přístup k tomuto úkolu před jeho dokončením, bude vlákno, které je aktuálně aktivní, blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="6d5a8-125">Ve většině případů byste měli k hodnotě přistupovat pomocí místo přímého `Await` přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="6d5a8-126">Příkazy zobrazení v následujícím kódu ověřují, zda hodnoty `result1` proměnné, `result2` proměnné a `Result` vlastnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="6d5a8-127">Mějte na paměti, že `Result` vlastnost je blokující vlastnost a neměla by k ní být přistupovaná před tím, než se její úloha očekává.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a><span data-ttu-id="6d5a8-128">Návratový typ úlohy</span><span class="sxs-lookup"><span data-stu-id="6d5a8-128">Task Return Type</span></span>

<span data-ttu-id="6d5a8-129">Asynchronní metody, které neobsahují příkaz return nebo obsahující příkaz return, který nevrací operand, obvykle mají návratový typ <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6d5a8-130">Tyto metody by byly procedury [Sub](../../language-features/procedures/sub-procedures.md) , pokud byly zapsány pro spuštění synchronně.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-130">Such methods would be [Sub](../../language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="6d5a8-131">Použijete-li `Task` návratový typ pro asynchronní metodu, volající metoda může použít `Await` operátor pro pozastavení dokončování volajícího až do dokončení volané asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="6d5a8-132">V následujícím příkladu asynchronní metoda neobsahuje `Task_MethodAsync` příkaz return.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="6d5a8-133">Proto zadáte návratový typ `Task` pro metodu, která umožňuje `Task_MethodAsync` očekávat.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="6d5a8-134">Definice `Task` typu nezahrnuje `Result` vlastnost pro uložení návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

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

<span data-ttu-id="6d5a8-135">`Task_MethodAsync`se volá a očekává se pomocí příkazu await namísto výrazu await, podobně jako volání příkazu pro synchronní `Sub` nebo návratovou metodu typu void.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="6d5a8-136">Použití `Await` operátoru v tomto případě nevytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="6d5a8-137">Následující kód volá a očekává metodu `Task_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="6d5a8-138">Jako v předchozím <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` od aplikace `Await` operátora, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="6d5a8-139">Mějte ale na paměti, že `Task` vlastnost neobsahuje `Result` vlastnost a že při použití operátoru await na objekt není vyprodukována žádná hodnota `Task` .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="6d5a8-140">Následující kód odděluje volání `Task_MethodAsync` z čekání na úkol, který `Task_MethodAsync` vrací.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a><span data-ttu-id="6d5a8-141">Návratový typ void</span><span class="sxs-lookup"><span data-stu-id="6d5a8-141">Void Return Type</span></span>

<span data-ttu-id="6d5a8-142">Primární použití `Sub` procedur je v obslužných rutinách událostí, kde neexistuje návratový typ (v jiných jazycích se označuje jako návratový typ void).</span><span class="sxs-lookup"><span data-stu-id="6d5a8-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="6d5a8-143">Návratový typ void také lze použít k přepsání metod vracejících anulování nebo pro metody, které provádějí aktivity, které mohou být zařazeny do kategorie "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="6d5a8-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="6d5a8-144">Měli byste však vracet `Task` , kdykoli je to možné, protože asynchronní metoda vracející typ void nemůže být očekávána.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="6d5a8-145">Každý volající takové metody musí být schopný pokračovat v dokončování bez čekání na dokončení volané asynchronní metody a volající musí být nezávislý na všech hodnotách nebo výjimkách, které asynchronní metoda generuje.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="6d5a8-146">Volající asynchronní metody vracející hodnotu void nemůže zachytit výjimky, které jsou vyvolány z metody, a tyto neošetřené výjimky pravděpodobně způsobí selhání aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="6d5a8-147">Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> , výjimka je uložena v vrácené úloze a znovu vyvolána, když je úloha očekávána.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="6d5a8-148">Proto se ujistěte, že jakákoliv asynchronní metoda, která může vyvolat výjimku, má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávána.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="6d5a8-149">Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d5a8-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="6d5a8-150">Následující kód definuje asynchronní obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-150">The following code defines an async event handler.</span></span>

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

## <a name="complete-example"></a><a name="BKMK_Example"></a><span data-ttu-id="6d5a8-151">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="6d5a8-151">Complete Example</span></span>

<span data-ttu-id="6d5a8-152">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="6d5a8-153">Chcete-li spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6d5a8-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="6d5a8-154">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="6d5a8-155">Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="6d5a8-156">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="6d5a8-157">V kategorii **nainstalováno**, **šablony** zvolte možnost **Visual Basic**a pak zvolte možnost **Windows**.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="6d5a8-158">V seznamu typů projektů vyberte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="6d5a8-159">`AsyncReturnTypes`Jako název projektu zadejte a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="6d5a8-160">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="6d5a8-161">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="6d5a8-162">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="6d5a8-163">V okně **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="6d5a8-164">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v okně **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="6d5a8-165">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="6d5a8-166">Nahraďte kód v souboru MainWindow. XAML. vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6d5a8-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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

9. <span data-ttu-id="6d5a8-167">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="6d5a8-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="6d5a8-168">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6d5a8-168">The following output should appear:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d5a8-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d5a8-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="6d5a8-170">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d5a8-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="6d5a8-171">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d5a8-171">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
- [<span data-ttu-id="6d5a8-172">Async</span><span class="sxs-lookup"><span data-stu-id="6d5a8-172">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="6d5a8-173">Await – operátor</span><span class="sxs-lookup"><span data-stu-id="6d5a8-173">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
