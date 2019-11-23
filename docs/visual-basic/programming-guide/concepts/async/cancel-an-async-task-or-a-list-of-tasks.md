---
title: Zrušení asynchronní úlohy nebo seznamu úloh
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 2956582cd0c8e044fcd37ffab13686489a7c854c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347970"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="e43e3-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43e3-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>

<span data-ttu-id="e43e3-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span><span class="sxs-lookup"><span data-stu-id="e43e3-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="e43e3-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span><span class="sxs-lookup"><span data-stu-id="e43e3-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="e43e3-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span><span class="sxs-lookup"><span data-stu-id="e43e3-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="e43e3-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span><span class="sxs-lookup"><span data-stu-id="e43e3-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_CancelaTask"></a> <span data-ttu-id="e43e3-107">Cancel a Task</span><span class="sxs-lookup"><span data-stu-id="e43e3-107">Cancel a Task</span></span>

<span data-ttu-id="e43e3-108">The first example associates the **Cancel** button with a single download task.</span><span class="sxs-lookup"><span data-stu-id="e43e3-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="e43e3-109">If you choose the button while the application is downloading content, the download is canceled.</span><span class="sxs-lookup"><span data-stu-id="e43e3-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="e43e3-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="e43e3-110">Downloading the Example</span></span>

<span data-ttu-id="e43e3-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span><span class="sxs-lookup"><span data-stu-id="e43e3-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e43e3-112">Decompress the file that you downloaded, and then start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e43e3-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e43e3-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="e43e3-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="e43e3-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="e43e3-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e43e3-116">Choose the F5 key to run the project.</span><span class="sxs-lookup"><span data-stu-id="e43e3-116">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="e43e3-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span><span class="sxs-lookup"><span data-stu-id="e43e3-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="e43e3-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span><span class="sxs-lookup"><span data-stu-id="e43e3-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="e43e3-119">Building the Example</span><span class="sxs-lookup"><span data-stu-id="e43e3-119">Building the Example</span></span>

<span data-ttu-id="e43e3-120">The following changes add a **Cancel** button to an application that downloads a website.</span><span class="sxs-lookup"><span data-stu-id="e43e3-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="e43e3-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span><span class="sxs-lookup"><span data-stu-id="e43e3-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="e43e3-122">Asterisks mark the changes in the code.</span><span class="sxs-lookup"><span data-stu-id="e43e3-122">Asterisks mark the changes in the code.</span></span>

<span data-ttu-id="e43e3-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

<span data-ttu-id="e43e3-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span><span class="sxs-lookup"><span data-stu-id="e43e3-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>

1. <span data-ttu-id="e43e3-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span><span class="sxs-lookup"><span data-stu-id="e43e3-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="e43e3-126">Add the following event handler for the **Cancel** button.</span><span class="sxs-lookup"><span data-stu-id="e43e3-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="e43e3-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span><span class="sxs-lookup"><span data-stu-id="e43e3-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. <span data-ttu-id="e43e3-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="e43e3-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="e43e3-129">Instantiate the `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="e43e3-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - <span data-ttu-id="e43e3-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span><span class="sxs-lookup"><span data-stu-id="e43e3-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="e43e3-131">The `Token` property propagates the message if cancellation is requested.</span><span class="sxs-lookup"><span data-stu-id="e43e3-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="e43e3-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span><span class="sxs-lookup"><span data-stu-id="e43e3-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="e43e3-133">The following code shows the changes.</span><span class="sxs-lookup"><span data-stu-id="e43e3-133">The following code shows the changes.</span></span>

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. <span data-ttu-id="e43e3-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span><span class="sxs-lookup"><span data-stu-id="e43e3-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="e43e3-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span><span class="sxs-lookup"><span data-stu-id="e43e3-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="e43e3-136">The token carries the message if the user chooses the **Cancel** button.</span><span class="sxs-lookup"><span data-stu-id="e43e3-136">The token carries the message if the user chooses the **Cancel** button.</span></span>

    <span data-ttu-id="e43e3-137">The following code shows the changes in `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e43e3-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. <span data-ttu-id="e43e3-138">If you don’t cancel the program, it produces the following output:</span><span class="sxs-lookup"><span data-stu-id="e43e3-138">If you don’t cancel the program, it produces the following output:</span></span>

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    <span data-ttu-id="e43e3-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output:</span><span class="sxs-lookup"><span data-stu-id="e43e3-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output:</span></span>

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="e43e3-140">Cancel a List of Tasks</span><span class="sxs-lookup"><span data-stu-id="e43e3-140">Cancel a List of Tasks</span></span>

<span data-ttu-id="e43e3-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span><span class="sxs-lookup"><span data-stu-id="e43e3-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="e43e3-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span><span class="sxs-lookup"><span data-stu-id="e43e3-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="e43e3-143">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="e43e3-143">Downloading the Example</span></span>

<span data-ttu-id="e43e3-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span><span class="sxs-lookup"><span data-stu-id="e43e3-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e43e3-145">Decompress the file that you downloaded, and then start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e43e3-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e43e3-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="e43e3-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="e43e3-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="e43e3-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e43e3-149">Choose the F5 key to run the project.</span><span class="sxs-lookup"><span data-stu-id="e43e3-149">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="e43e3-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span><span class="sxs-lookup"><span data-stu-id="e43e3-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="e43e3-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span><span class="sxs-lookup"><span data-stu-id="e43e3-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="e43e3-152">Building the Example</span><span class="sxs-lookup"><span data-stu-id="e43e3-152">Building the Example</span></span>

<span data-ttu-id="e43e3-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="e43e3-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="e43e3-154">Add the following changes to that project.</span><span class="sxs-lookup"><span data-stu-id="e43e3-154">Add the following changes to that project.</span></span> <span data-ttu-id="e43e3-155">Asterisks mark the changes in the program.</span><span class="sxs-lookup"><span data-stu-id="e43e3-155">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="e43e3-156">Add a method to create a list of web addresses.</span><span class="sxs-lookup"><span data-stu-id="e43e3-156">Add a method to create a list of web addresses.</span></span>

    ```vb
    ' ***Add a method that creates a list of web addresses.
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
    ```

2. <span data-ttu-id="e43e3-157">Call the method in `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e43e3-157">Call the method in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. <span data-ttu-id="e43e3-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span><span class="sxs-lookup"><span data-stu-id="e43e3-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. <span data-ttu-id="e43e3-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span><span class="sxs-lookup"><span data-stu-id="e43e3-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="e43e3-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e43e3-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    <span data-ttu-id="e43e3-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span><span class="sxs-lookup"><span data-stu-id="e43e3-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. <span data-ttu-id="e43e3-162">If you don’t cancel the program, it produces the following output:</span><span class="sxs-lookup"><span data-stu-id="e43e3-162">If you don’t cancel the program, it produces the following output:</span></span>

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

    <span data-ttu-id="e43e3-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span><span class="sxs-lookup"><span data-stu-id="e43e3-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="e43e3-164">Complete Examples</span><span class="sxs-lookup"><span data-stu-id="e43e3-164">Complete Examples</span></span>

<span data-ttu-id="e43e3-165">The following sections contain the code for each of the previous examples.</span><span class="sxs-lookup"><span data-stu-id="e43e3-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="e43e3-166">Notice that you must add a reference for <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e43e3-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="e43e3-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e43e3-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="cancel-a-task-example"></a><span data-ttu-id="e43e3-168">Příklad zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="e43e3-168">Cancel a Task Example</span></span>

<span data-ttu-id="e43e3-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span><span class="sxs-lookup"><span data-stu-id="e43e3-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="e43e3-170">Příklad zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="e43e3-170">Cancel a List of Tasks Example</span></span>

<span data-ttu-id="e43e3-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span><span class="sxs-lookup"><span data-stu-id="e43e3-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>

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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
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

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="e43e3-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e43e3-172">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="e43e3-173">Asynchronous Programming with Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43e3-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e43e3-174">Fine-Tuning Your Async Application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43e3-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="e43e3-175">Async Sample: Fine Tuning Your Application</span><span class="sxs-lookup"><span data-stu-id="e43e3-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
