---
title: Asynchronní návratové typy
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 96d3a945a49a12f7c2d5d60e8ee59ce047a0bae6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347982"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="34cb4-102">Async Return Types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34cb4-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="34cb4-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span><span class="sxs-lookup"><span data-stu-id="34cb4-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="34cb4-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span><span class="sxs-lookup"><span data-stu-id="34cb4-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="34cb4-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="34cb4-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="34cb4-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="34cb4-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb4-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span><span class="sxs-lookup"><span data-stu-id="34cb4-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="34cb4-108">Task(T) Return Type</span><span class="sxs-lookup"><span data-stu-id="34cb4-108">Task(T) Return Type</span></span>

<span data-ttu-id="34cb4-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="34cb4-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span><span class="sxs-lookup"><span data-stu-id="34cb4-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="34cb4-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="34cb4-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="34cb4-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="34cb4-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="34cb4-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="34cb4-115">The result is assigned to the `result1` variable.</span><span class="sxs-lookup"><span data-stu-id="34cb4-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="34cb4-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span><span class="sxs-lookup"><span data-stu-id="34cb4-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="34cb4-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span><span class="sxs-lookup"><span data-stu-id="34cb4-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="34cb4-118">The task is assigned to the `integerTask` variable in the example.</span><span class="sxs-lookup"><span data-stu-id="34cb4-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="34cb4-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="34cb4-120">In this case, TResult represents an integer type.</span><span class="sxs-lookup"><span data-stu-id="34cb4-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="34cb4-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="34cb4-122">The value is assigned to the `result2` variable.</span><span class="sxs-lookup"><span data-stu-id="34cb4-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="34cb4-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span><span class="sxs-lookup"><span data-stu-id="34cb4-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="34cb4-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span><span class="sxs-lookup"><span data-stu-id="34cb4-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="34cb4-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span><span class="sxs-lookup"><span data-stu-id="34cb4-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="34cb4-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span><span class="sxs-lookup"><span data-stu-id="34cb4-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="34cb4-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span><span class="sxs-lookup"><span data-stu-id="34cb4-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="34cb4-128">Task Return Type</span><span class="sxs-lookup"><span data-stu-id="34cb4-128">Task Return Type</span></span>

<span data-ttu-id="34cb4-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="34cb4-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="34cb4-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span><span class="sxs-lookup"><span data-stu-id="34cb4-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="34cb4-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span><span class="sxs-lookup"><span data-stu-id="34cb4-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="34cb4-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span><span class="sxs-lookup"><span data-stu-id="34cb4-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="34cb4-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span><span class="sxs-lookup"><span data-stu-id="34cb4-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="34cb4-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span><span class="sxs-lookup"><span data-stu-id="34cb4-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

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

<span data-ttu-id="34cb4-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span><span class="sxs-lookup"><span data-stu-id="34cb4-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="34cb4-136">The application of an `Await` operator in this case doesn't produce a value.</span><span class="sxs-lookup"><span data-stu-id="34cb4-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="34cb4-137">The following code calls and awaits method `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="34cb4-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span><span class="sxs-lookup"><span data-stu-id="34cb4-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="34cb4-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span><span class="sxs-lookup"><span data-stu-id="34cb4-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="34cb4-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span><span class="sxs-lookup"><span data-stu-id="34cb4-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="34cb4-141">Void Return Type</span><span class="sxs-lookup"><span data-stu-id="34cb4-141">Void Return Type</span></span>

<span data-ttu-id="34cb4-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span><span class="sxs-lookup"><span data-stu-id="34cb4-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="34cb4-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span><span class="sxs-lookup"><span data-stu-id="34cb4-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="34cb4-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span><span class="sxs-lookup"><span data-stu-id="34cb4-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="34cb4-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span><span class="sxs-lookup"><span data-stu-id="34cb4-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="34cb4-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span><span class="sxs-lookup"><span data-stu-id="34cb4-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="34cb4-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span><span class="sxs-lookup"><span data-stu-id="34cb4-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="34cb4-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span><span class="sxs-lookup"><span data-stu-id="34cb4-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="34cb4-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34cb4-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="34cb4-150">The following code defines an async event handler.</span><span class="sxs-lookup"><span data-stu-id="34cb4-150">The following code defines an async event handler.</span></span>

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

## <a name="BKMK_Example"></a> <span data-ttu-id="34cb4-151">Complete Example</span><span class="sxs-lookup"><span data-stu-id="34cb4-151">Complete Example</span></span>

<span data-ttu-id="34cb4-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span><span class="sxs-lookup"><span data-stu-id="34cb4-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="34cb4-153">To run the project, perform the following steps:</span><span class="sxs-lookup"><span data-stu-id="34cb4-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="34cb4-154">Start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34cb4-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="34cb4-155">On the menu bar, choose **File**, **New**, **Project**.</span><span class="sxs-lookup"><span data-stu-id="34cb4-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="34cb4-156">The **New Project** dialog box opens.</span><span class="sxs-lookup"><span data-stu-id="34cb4-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="34cb4-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span><span class="sxs-lookup"><span data-stu-id="34cb4-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="34cb4-158">Choose **WPF Application** from the list of project types.</span><span class="sxs-lookup"><span data-stu-id="34cb4-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="34cb4-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="34cb4-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="34cb4-160">The new project appears in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="34cb4-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="34cb4-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span><span class="sxs-lookup"><span data-stu-id="34cb4-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="34cb4-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="34cb4-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="34cb4-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span><span class="sxs-lookup"><span data-stu-id="34cb4-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="34cb4-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="34cb4-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="34cb4-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span><span class="sxs-lookup"><span data-stu-id="34cb4-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="34cb4-166">Replace the code in MainWindow.xaml.vb with the following code.</span><span class="sxs-lookup"><span data-stu-id="34cb4-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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

9. <span data-ttu-id="34cb4-167">Choose the F5 key to run the program, and then choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="34cb4-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="34cb4-168">The following output should appear:</span><span class="sxs-lookup"><span data-stu-id="34cb4-168">The following output should appear:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34cb4-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34cb4-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="34cb4-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34cb4-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="34cb4-171">Control Flow in Async Programs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34cb4-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="34cb4-172">Async</span><span class="sxs-lookup"><span data-stu-id="34cb4-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="34cb4-173">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="34cb4-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
