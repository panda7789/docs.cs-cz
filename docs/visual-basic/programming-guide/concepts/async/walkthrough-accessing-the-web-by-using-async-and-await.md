---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: c13e592eb155d14c2e7cb2388a96925a7f1fa413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349094"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="9edf0-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="9edf0-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span><span class="sxs-lookup"><span data-stu-id="9edf0-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="9edf0-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span><span class="sxs-lookup"><span data-stu-id="9edf0-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="9edf0-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="9edf0-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="9edf0-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span><span class="sxs-lookup"><span data-stu-id="9edf0-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="9edf0-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span><span class="sxs-lookup"><span data-stu-id="9edf0-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="9edf0-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="9edf0-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="9edf0-109">In this walkthrough, you complete the following tasks:</span><span class="sxs-lookup"><span data-stu-id="9edf0-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="9edf0-110">Create a WPF application</span><span class="sxs-lookup"><span data-stu-id="9edf0-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="9edf0-111">Design a simple WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="9edf0-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="9edf0-112">Add a reference</span><span class="sxs-lookup"><span data-stu-id="9edf0-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="9edf0-113">Add necessary Imports statements</span><span class="sxs-lookup"><span data-stu-id="9edf0-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="9edf0-114">Create a synchronous application</span><span class="sxs-lookup"><span data-stu-id="9edf0-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="9edf0-115">Test the synchronous solution</span><span class="sxs-lookup"><span data-stu-id="9edf0-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="9edf0-116">Convert GetURLContents to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="9edf0-117">Convert SumPageSizes to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="9edf0-118">Convert startButton_Click to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="9edf0-119">Test the asynchronous solution</span><span class="sxs-lookup"><span data-stu-id="9edf0-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="9edf0-120">Replace the GetURLContentsAsync method with a .NET Framework method</span><span class="sxs-lookup"><span data-stu-id="9edf0-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="9edf0-121">See the [Example](#example) section for the complete asynchronous example.</span><span class="sxs-lookup"><span data-stu-id="9edf0-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9edf0-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9edf0-122">Prerequisites</span></span>

<span data-ttu-id="9edf0-123">Visual Studio 2012 or later must be installed on your computer.</span><span class="sxs-lookup"><span data-stu-id="9edf0-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="9edf0-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span><span class="sxs-lookup"><span data-stu-id="9edf0-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="9edf0-125">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="9edf0-125">Create a WPF application</span></span>

1. <span data-ttu-id="9edf0-126">Start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9edf0-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="9edf0-127">On the menu bar, choose **File**, **New**, **Project**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="9edf0-128">The **New Project** dialog box opens.</span><span class="sxs-lookup"><span data-stu-id="9edf0-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="9edf0-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span><span class="sxs-lookup"><span data-stu-id="9edf0-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="9edf0-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="9edf0-131">The new project appears in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="9edf0-132">Design a simple WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="9edf0-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="9edf0-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span><span class="sxs-lookup"><span data-stu-id="9edf0-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="9edf0-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="9edf0-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span><span class="sxs-lookup"><span data-stu-id="9edf0-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="9edf0-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span><span class="sxs-lookup"><span data-stu-id="9edf0-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="9edf0-137">Set the **Name** property to `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="9edf0-138">Set the **Height** property to 250.</span><span class="sxs-lookup"><span data-stu-id="9edf0-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="9edf0-139">Set the **Width** property to 500.</span><span class="sxs-lookup"><span data-stu-id="9edf0-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="9edf0-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="9edf0-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="9edf0-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span><span class="sxs-lookup"><span data-stu-id="9edf0-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="9edf0-142">Set the **Name** property to `startButton`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="9edf0-143">Change the value of the **Content** property from **Button** to **Start**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="9edf0-144">Position the text box and the button so that both appear in the **MainWindow** window.</span><span class="sxs-lookup"><span data-stu-id="9edf0-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="9edf0-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9edf0-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="9edf0-146">Add a reference</span><span class="sxs-lookup"><span data-stu-id="9edf0-146">Add a reference</span></span>

1. <span data-ttu-id="9edf0-147">In **Solution Explorer**, highlight your project's name.</span><span class="sxs-lookup"><span data-stu-id="9edf0-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="9edf0-148">On the menu bar, choose **Project**, **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="9edf0-149">The **Reference Manager** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="9edf0-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="9edf0-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span><span class="sxs-lookup"><span data-stu-id="9edf0-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="9edf0-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span><span class="sxs-lookup"><span data-stu-id="9edf0-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="9edf0-152">In the list of names, select the **System.Net.Http** check box.</span><span class="sxs-lookup"><span data-stu-id="9edf0-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="9edf0-153">Choose the **OK** button to close the dialog box.</span><span class="sxs-lookup"><span data-stu-id="9edf0-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="9edf0-154">Add necessary Imports statements</span><span class="sxs-lookup"><span data-stu-id="9edf0-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="9edf0-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span><span class="sxs-lookup"><span data-stu-id="9edf0-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="9edf0-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span><span class="sxs-lookup"><span data-stu-id="9edf0-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="9edf0-157">Create a synchronous application</span><span class="sxs-lookup"><span data-stu-id="9edf0-157">Create a synchronous application</span></span>

1. <span data-ttu-id="9edf0-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="9edf0-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="9edf0-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="9edf0-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="9edf0-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="9edf0-161">The code for the synchronous solution contains the following four methods:</span><span class="sxs-lookup"><span data-stu-id="9edf0-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="9edf0-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span><span class="sxs-lookup"><span data-stu-id="9edf0-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="9edf0-163">`SetUpURLList`, which makes and returns a list of web addresses.</span><span class="sxs-lookup"><span data-stu-id="9edf0-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="9edf0-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span><span class="sxs-lookup"><span data-stu-id="9edf0-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="9edf0-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span><span class="sxs-lookup"><span data-stu-id="9edf0-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="9edf0-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="9edf0-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="9edf0-167">Test the synchronous solution</span><span class="sxs-lookup"><span data-stu-id="9edf0-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="9edf0-168">Choose the F5 key to run the program, and then choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="9edf0-169">Output that resembles the following list should appear:</span><span class="sxs-lookup"><span data-stu-id="9edf0-169">Output that resembles the following list should appear:</span></span>

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    <span data-ttu-id="9edf0-170">Notice that it takes a few seconds to display the counts.</span><span class="sxs-lookup"><span data-stu-id="9edf0-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="9edf0-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span><span class="sxs-lookup"><span data-stu-id="9edf0-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="9edf0-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="9edf0-173">These efforts fail until the byte counts start to appear.</span><span class="sxs-lookup"><span data-stu-id="9edf0-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="9edf0-174">If a website isn’t responding, you have no indication of which site failed.</span><span class="sxs-lookup"><span data-stu-id="9edf0-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="9edf0-175">It is difficult even to stop waiting and close the program.</span><span class="sxs-lookup"><span data-stu-id="9edf0-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="9edf0-176">Convert GetURLContents to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="9edf0-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span><span class="sxs-lookup"><span data-stu-id="9edf0-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="9edf0-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span><span class="sxs-lookup"><span data-stu-id="9edf0-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="9edf0-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9edf0-180">As you follow the steps in this walkthrough, several compiler errors appear.</span><span class="sxs-lookup"><span data-stu-id="9edf0-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="9edf0-181">You can ignore them and continue with the walkthrough.</span><span class="sxs-lookup"><span data-stu-id="9edf0-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="9edf0-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="9edf0-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9edf0-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="9edf0-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span><span class="sxs-lookup"><span data-stu-id="9edf0-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="9edf0-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span><span class="sxs-lookup"><span data-stu-id="9edf0-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="9edf0-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span><span class="sxs-lookup"><span data-stu-id="9edf0-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="9edf0-188">In the meantime, control returns to the caller of the current method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="9edf0-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="9edf0-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="9edf0-191">The previous statement can be separated into the following two statements to clarify what happens.</span><span class="sxs-lookup"><span data-stu-id="9edf0-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="9edf0-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="9edf0-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span><span class="sxs-lookup"><span data-stu-id="9edf0-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="9edf0-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span><span class="sxs-lookup"><span data-stu-id="9edf0-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="9edf0-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="9edf0-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="9edf0-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span><span class="sxs-lookup"><span data-stu-id="9edf0-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="9edf0-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span><span class="sxs-lookup"><span data-stu-id="9edf0-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="9edf0-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="9edf0-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="9edf0-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span><span class="sxs-lookup"><span data-stu-id="9edf0-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="9edf0-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span><span class="sxs-lookup"><span data-stu-id="9edf0-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="9edf0-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="9edf0-203">The task functions like "Task(void)" and enables the method to be awaited.</span><span class="sxs-lookup"><span data-stu-id="9edf0-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="9edf0-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span><span class="sxs-lookup"><span data-stu-id="9edf0-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="9edf0-205">The previous statement abbreviates the following two lines of code.</span><span class="sxs-lookup"><span data-stu-id="9edf0-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="9edf0-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span><span class="sxs-lookup"><span data-stu-id="9edf0-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="9edf0-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span><span class="sxs-lookup"><span data-stu-id="9edf0-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="9edf0-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span><span class="sxs-lookup"><span data-stu-id="9edf0-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="9edf0-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="9edf0-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9edf0-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="9edf0-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span><span class="sxs-lookup"><span data-stu-id="9edf0-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="9edf0-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span><span class="sxs-lookup"><span data-stu-id="9edf0-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="9edf0-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="9edf0-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

    <span data-ttu-id="9edf0-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span><span class="sxs-lookup"><span data-stu-id="9edf0-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="9edf0-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span><span class="sxs-lookup"><span data-stu-id="9edf0-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="9edf0-216">Make the following changes in the method signature:</span><span class="sxs-lookup"><span data-stu-id="9edf0-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="9edf0-217">Change the return type to `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="9edf0-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="9edf0-219">The following code shows these changes.</span><span class="sxs-lookup"><span data-stu-id="9edf0-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="9edf0-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span><span class="sxs-lookup"><span data-stu-id="9edf0-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="9edf0-221">Convert SumPageSizes to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="9edf0-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="9edf0-223">First, change the call to `GetURLContents` to an asynchronous call.</span><span class="sxs-lookup"><span data-stu-id="9edf0-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="9edf0-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span><span class="sxs-lookup"><span data-stu-id="9edf0-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="9edf0-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span><span class="sxs-lookup"><span data-stu-id="9edf0-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="9edf0-226">The following code shows these changes.</span><span class="sxs-lookup"><span data-stu-id="9edf0-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="9edf0-227">The previous assignment abbreviates the following two lines of code.</span><span class="sxs-lookup"><span data-stu-id="9edf0-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="9edf0-228">Make the following changes in the method's signature:</span><span class="sxs-lookup"><span data-stu-id="9edf0-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="9edf0-229">Mark the method with the `Async` modifier.</span><span class="sxs-lookup"><span data-stu-id="9edf0-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="9edf0-230">Add "Async" to the method name.</span><span class="sxs-lookup"><span data-stu-id="9edf0-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="9edf0-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span><span class="sxs-lookup"><span data-stu-id="9edf0-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="9edf0-232">Therefore, change the method type from `Sub` to `Function`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="9edf0-233">The return type of the function is `Task`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="9edf0-234">The following code shows these changes.</span><span class="sxs-lookup"><span data-stu-id="9edf0-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="9edf0-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span><span class="sxs-lookup"><span data-stu-id="9edf0-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="9edf0-236">Convert startButton_Click to an asynchronous method</span><span class="sxs-lookup"><span data-stu-id="9edf0-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="9edf0-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span><span class="sxs-lookup"><span data-stu-id="9edf0-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="9edf0-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span><span class="sxs-lookup"><span data-stu-id="9edf0-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="9edf0-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="9edf0-240">The call returns a `Task`, not a `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="9edf0-241">As in previous procedures, you can convert the call by using one statement or two statements.</span><span class="sxs-lookup"><span data-stu-id="9edf0-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="9edf0-242">The following code shows these changes.</span><span class="sxs-lookup"><span data-stu-id="9edf0-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="9edf0-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="9edf0-244">You can reenable the button at the end of the event handler.</span><span class="sxs-lookup"><span data-stu-id="9edf0-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="9edf0-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9edf0-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="9edf0-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="9edf0-247">Typically, the names of event handlers aren’t changed.</span><span class="sxs-lookup"><span data-stu-id="9edf0-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="9edf0-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9edf0-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="9edf0-249">The conversion of the project from synchronous to asynchronous processing is complete.</span><span class="sxs-lookup"><span data-stu-id="9edf0-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="9edf0-250">Test the asynchronous solution</span><span class="sxs-lookup"><span data-stu-id="9edf0-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="9edf0-251">Choose the F5 key to run the program, and then choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="9edf0-252">Output that resembles the output of the synchronous solution should appear.</span><span class="sxs-lookup"><span data-stu-id="9edf0-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="9edf0-253">However, notice the following differences.</span><span class="sxs-lookup"><span data-stu-id="9edf0-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="9edf0-254">The results don’t all occur at the same time, after the processing is complete.</span><span class="sxs-lookup"><span data-stu-id="9edf0-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="9edf0-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span><span class="sxs-lookup"><span data-stu-id="9edf0-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="9edf0-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span><span class="sxs-lookup"><span data-stu-id="9edf0-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="9edf0-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span><span class="sxs-lookup"><span data-stu-id="9edf0-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="9edf0-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="9edf0-259">Most importantly, the UI thread isn’t blocked during the downloads.</span><span class="sxs-lookup"><span data-stu-id="9edf0-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="9edf0-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span><span class="sxs-lookup"><span data-stu-id="9edf0-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="9edf0-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span><span class="sxs-lookup"><span data-stu-id="9edf0-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="9edf0-262">Replace the GetURLContentsAsync method with a .NET Framework method</span><span class="sxs-lookup"><span data-stu-id="9edf0-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="9edf0-263">The .NET Framework provides many async methods that you can use.</span><span class="sxs-lookup"><span data-stu-id="9edf0-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="9edf0-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span><span class="sxs-lookup"><span data-stu-id="9edf0-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="9edf0-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span><span class="sxs-lookup"><span data-stu-id="9edf0-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="9edf0-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="9edf0-267">Add the following declaration at the start of the method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="9edf0-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="9edf0-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span><span class="sxs-lookup"><span data-stu-id="9edf0-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="9edf0-270">Choose the F5 key to run the program, and then choose the **Start** button.</span><span class="sxs-lookup"><span data-stu-id="9edf0-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="9edf0-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span><span class="sxs-lookup"><span data-stu-id="9edf0-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="9edf0-272">Příklad</span><span class="sxs-lookup"><span data-stu-id="9edf0-272">Example</span></span>

<span data-ttu-id="9edf0-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span><span class="sxs-lookup"><span data-stu-id="9edf0-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="9edf0-274">Notice that it strongly resembles the original, synchronous solution.</span><span class="sxs-lookup"><span data-stu-id="9edf0-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

<span data-ttu-id="9edf0-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="9edf0-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
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

## <a name="see-also"></a><span data-ttu-id="9edf0-276">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9edf0-276">See also</span></span>

- [<span data-ttu-id="9edf0-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="9edf0-278">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="9edf0-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="9edf0-279">Async</span><span class="sxs-lookup"><span data-stu-id="9edf0-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="9edf0-280">Asynchronous Programming with Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="9edf0-281">Async Return Types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="9edf0-282">Task-based Asynchronous Programming (TAP)</span><span class="sxs-lookup"><span data-stu-id="9edf0-282">Task-based Asynchronous Programming (TAP)</span></span>](https://go.microsoft.com/fwlink/?LinkId=204847)
- [<span data-ttu-id="9edf0-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="9edf0-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9edf0-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
