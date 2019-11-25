---
title: Zrušení zbývajících asynchronních úloh po dokončení jedné z nich
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: e6747f35e665611ac7a48a87f955c8b893ee2b99
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347927"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="f1273-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1273-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="f1273-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span><span class="sxs-lookup"><span data-stu-id="f1273-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="f1273-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="f1273-105">The method starts all the tasks and returns a single task.</span><span class="sxs-lookup"><span data-stu-id="f1273-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="f1273-106">The single task is complete when any task in the collection is complete.</span><span class="sxs-lookup"><span data-stu-id="f1273-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="f1273-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="f1273-108">Each task downloads the contents of a website.</span><span class="sxs-lookup"><span data-stu-id="f1273-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="f1273-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span><span class="sxs-lookup"><span data-stu-id="f1273-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="f1273-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span><span class="sxs-lookup"><span data-stu-id="f1273-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="f1273-111">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="f1273-111">Downloading the Example</span></span>

<span data-ttu-id="f1273-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span><span class="sxs-lookup"><span data-stu-id="f1273-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="f1273-113">Decompress the file that you downloaded, and then start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1273-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f1273-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f1273-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="f1273-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="f1273-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="f1273-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="f1273-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="f1273-117">Choose the F5 key to run the project.</span><span class="sxs-lookup"><span data-stu-id="f1273-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="f1273-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span><span class="sxs-lookup"><span data-stu-id="f1273-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="f1273-119">Run the program several times to verify that different downloads finish first.</span><span class="sxs-lookup"><span data-stu-id="f1273-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="f1273-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span><span class="sxs-lookup"><span data-stu-id="f1273-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="f1273-121">Building the Example</span><span class="sxs-lookup"><span data-stu-id="f1273-121">Building the Example</span></span>

<span data-ttu-id="f1273-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="f1273-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span><span class="sxs-lookup"><span data-stu-id="f1273-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="f1273-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="f1273-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="f1273-125">Add the changes in this topic to that project.</span><span class="sxs-lookup"><span data-stu-id="f1273-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="f1273-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span><span class="sxs-lookup"><span data-stu-id="f1273-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

<span data-ttu-id="f1273-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="f1273-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="f1273-129">Make the following changes in `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f1273-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f1273-130">Asterisks mark the changes in the code file.</span><span class="sxs-lookup"><span data-stu-id="f1273-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="f1273-131">Comment out or delete the loop.</span><span class="sxs-lookup"><span data-stu-id="f1273-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="f1273-132">Create a query that, when executed, produces a collection of generic tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="f1273-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span><span class="sxs-lookup"><span data-stu-id="f1273-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="f1273-134">Call `ToArray` to execute the query and start the tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="f1273-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span><span class="sxs-lookup"><span data-stu-id="f1273-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="f1273-136">The safest practice is to force execution of the query explicitly.</span><span class="sxs-lookup"><span data-stu-id="f1273-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="f1273-137">Call `WhenAny` on the collection of tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="f1273-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="f1273-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="f1273-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span><span class="sxs-lookup"><span data-stu-id="f1273-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="f1273-140">That single task is the first task in the collection to finish.</span><span class="sxs-lookup"><span data-stu-id="f1273-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="f1273-141">The task that finished first is assigned to `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="f1273-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="f1273-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="f1273-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="f1273-143">In this example, you’re interested only in the task that finishes first.</span><span class="sxs-lookup"><span data-stu-id="f1273-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="f1273-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span><span class="sxs-lookup"><span data-stu-id="f1273-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="f1273-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span><span class="sxs-lookup"><span data-stu-id="f1273-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="f1273-146">Run the program several times to verify that different downloads finish first.</span><span class="sxs-lookup"><span data-stu-id="f1273-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="f1273-147">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="f1273-147">Complete Example</span></span>

<span data-ttu-id="f1273-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span><span class="sxs-lookup"><span data-stu-id="f1273-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="f1273-149">Asterisks mark the elements that were added for this example.</span><span class="sxs-lookup"><span data-stu-id="f1273-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="f1273-150">Notice that you must add a reference for <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f1273-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="f1273-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f1273-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to firstFinishedTask.
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await firstFinishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a><span data-ttu-id="f1273-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1273-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="f1273-153">Fine-Tuning Your Async Application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1273-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="f1273-154">Asynchronous Programming with Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1273-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f1273-155">Async Sample: Fine Tuning Your Application</span><span class="sxs-lookup"><span data-stu-id="f1273-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
