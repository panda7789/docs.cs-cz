---
title: 'Postupy: Paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 616efca79312883f17ba837d17a5ee9c97d15b34
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346139"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="f615f-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f615f-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="f615f-103">In an async method, tasks are started when they’re created.</span><span class="sxs-lookup"><span data-stu-id="f615f-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="f615f-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span><span class="sxs-lookup"><span data-stu-id="f615f-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="f615f-105">Often a task is awaited as soon as it’s created, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="f615f-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="f615f-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span><span class="sxs-lookup"><span data-stu-id="f615f-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

<span data-ttu-id="f615f-107">Between starting a task and awaiting it, you can start other tasks.</span><span class="sxs-lookup"><span data-stu-id="f615f-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="f615f-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span><span class="sxs-lookup"><span data-stu-id="f615f-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="f615f-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span><span class="sxs-lookup"><span data-stu-id="f615f-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="f615f-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span><span class="sxs-lookup"><span data-stu-id="f615f-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="f615f-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span><span class="sxs-lookup"><span data-stu-id="f615f-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="f615f-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span><span class="sxs-lookup"><span data-stu-id="f615f-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="f615f-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f615f-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="f615f-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="f615f-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="f615f-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f615f-115">To set up the project</span></span>

1. <span data-ttu-id="f615f-116">To set up a WPF application, complete the following steps.</span><span class="sxs-lookup"><span data-stu-id="f615f-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="f615f-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f615f-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="f615f-118">Create a WPF application that contains a text box and a button.</span><span class="sxs-lookup"><span data-stu-id="f615f-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="f615f-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="f615f-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="f615f-120">Add a reference for <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f615f-120">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="f615f-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="f615f-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="f615f-122">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="f615f-122">To add the code</span></span>

1. <span data-ttu-id="f615f-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="f615f-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="f615f-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="f615f-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="f615f-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span><span class="sxs-lookup"><span data-stu-id="f615f-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="f615f-126">Add the following support methods to the project:</span><span class="sxs-lookup"><span data-stu-id="f615f-126">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="f615f-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span><span class="sxs-lookup"><span data-stu-id="f615f-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="f615f-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span><span class="sxs-lookup"><span data-stu-id="f615f-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="f615f-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span><span class="sxs-lookup"><span data-stu-id="f615f-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="f615f-130">This display shows when each task has finished downloading.</span><span class="sxs-lookup"><span data-stu-id="f615f-130">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="f615f-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="f615f-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. <span data-ttu-id="f615f-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span><span class="sxs-lookup"><span data-stu-id="f615f-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="f615f-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="f615f-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="f615f-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span><span class="sxs-lookup"><span data-stu-id="f615f-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="f615f-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span><span class="sxs-lookup"><span data-stu-id="f615f-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="f615f-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span><span class="sxs-lookup"><span data-stu-id="f615f-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="f615f-137">The method awaits the completion of each task.</span><span class="sxs-lookup"><span data-stu-id="f615f-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="f615f-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span><span class="sxs-lookup"><span data-stu-id="f615f-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="f615f-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span><span class="sxs-lookup"><span data-stu-id="f615f-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="f615f-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span><span class="sxs-lookup"><span data-stu-id="f615f-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="f615f-141">Copy the following method, and paste it into your solution.</span><span class="sxs-lookup"><span data-stu-id="f615f-141">Copy the following method, and paste it into your solution.</span></span>

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. <span data-ttu-id="f615f-142">Choose the F5 key to run the program, and then choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="f615f-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="f615f-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span><span class="sxs-lookup"><span data-stu-id="f615f-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="f615f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f615f-144">Example</span></span>

<span data-ttu-id="f615f-145">The following code contains the full example.</span><span class="sxs-lookup"><span data-stu-id="f615f-145">The following code contains the full example.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="f615f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f615f-146">See also</span></span>

- [<span data-ttu-id="f615f-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f615f-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f615f-148">Asynchronous Programming with Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f615f-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f615f-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f615f-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
