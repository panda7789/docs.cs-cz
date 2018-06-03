---
title: Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: baf18ed4c2a4693f0765358d9f9a56842991cf29
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728336"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="1ba3e-102">Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ba3e-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="1ba3e-103">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda společně s <xref:System.Threading.CancellationToken>, můžete zrušit všechny zbývající úkoly po dokončení úloh.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="1ba3e-104">`WhenAny` Metoda přebírá argument, který je kolekce úloh.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="1ba3e-105">Metoda spustí všechny úlohy a vrátí jednu úlohu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="1ba3e-106">Jediná úloha je dokončena po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="1ba3e-107">Tento příklad ukazuje, jak používat token zrušení ve spojení s `WhenAny` k uložení do první úlohy a dokončit z kolekce úloh a zrušit ve zbývajících úkolech.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="1ba3e-108">Každý úkol stáhne obsah webu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="1ba3e-109">V příkladu se zobrazí délka obsahu první stahování dokončit a zruší další soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ba3e-110">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="1ba3e-111">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="1ba3e-111">Downloading the Example</span></span>  
 <span data-ttu-id="1ba3e-112">Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1ba3e-113">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1ba3e-114">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1ba3e-115">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="1ba3e-116">V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterOneTask** projektu a potom vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1ba3e-117">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1ba3e-118">Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="1ba3e-119">Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="1ba3e-120">Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="1ba3e-121">Vytváření v příkladu</span><span class="sxs-lookup"><span data-stu-id="1ba3e-121">Building the Example</span></span>  
 <span data-ttu-id="1ba3e-122">V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) zrušit seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="1ba3e-123">Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="1ba3e-124">K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="1ba3e-125">Do tohoto projektu přidáte změny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="1ba3e-126">V souboru MainWindow.xaml.vb **CancelAListOfTasks** projektu, spusťte přechodu přesunutím zpracování kroky pro každý web smyčky v `AccessTheWebAsync` následující asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="1ba3e-127">V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metoda pro vytvoření a spuštění úloh v poli.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="1ba3e-128">Použití `WhenAny` do pole vrátí jeden úkol, pokud je očekáváno, vyhodnotí jako první úlohou k dosažení dokončování úloh v poli.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="1ba3e-129">Proveďte následující změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="1ba3e-130">Hvězdičky označit změny v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="1ba3e-131">Komentář nebo odstranit smyčky.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="1ba3e-132">Vytvořit dotaz, která po provedení vytvoří kolekci obecné úlohy.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="1ba3e-133">Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  <span data-ttu-id="1ba3e-134">Volání `ToArray` proveďte dotaz a spusťte úlohy.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="1ba3e-135">Použití `WhenAny` metoda v dalším kroku by provést dotaz a spustit úlohy bez použití `ToArray`, ale jiné metody možná není.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="1ba3e-136">Nejbezpečnější metodou je explicitně vynutit spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="1ba3e-137">Volání `WhenAny` na kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="1ba3e-138">`WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="1ba3e-139">To znamená `WhenAny` vrátí úlohu, která vyhodnotí na jednu `Task(Of Integer)` nebo `Task<int>` Pokud je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="1ba3e-140">Tento jeden úkol je první úloha v kolekci ukončíte.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="1ba3e-141">Úloha, která nejprve dokončení je přiřazen k `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="1ba3e-142">Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože se jedná návratový typ `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="1ba3e-143">V tomto příkladu co vás zajímá pouze úloha, která nejprve dokončí.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="1ba3e-144">Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušit ve zbývajících úkolech.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="1ba3e-145">Nakonec await `firstFinishedTask` načíst délka staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="1ba3e-146">Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="1ba3e-147">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="1ba3e-147">Complete Example</span></span>  
 <span data-ttu-id="1ba3e-148">Následující kód je k dokončení souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="1ba3e-149">Hvězdičky označit prvky, které byly přidány v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="1ba3e-150">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="1ba3e-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1ba3e-151">Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="1ba3e-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
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
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ba3e-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ba3e-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="1ba3e-153">Vyladění s modifikátorem Async aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ba3e-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="1ba3e-154">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ba3e-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="1ba3e-155">Ukázka asynchronního: Jemnou ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="1ba3e-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
