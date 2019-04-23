---
title: Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 5dd9a99b96dc1e599fc2bde3a796beadf33f8147
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324510"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="e6b58-102">Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b58-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="e6b58-103">S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda spolu s <xref:System.Threading.CancellationToken>, můžete po dokončení jednoho úkolu zrušit všechny zbývající úkoly.</span><span class="sxs-lookup"><span data-stu-id="e6b58-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="e6b58-104">`WhenAny` Metoda přebírá argument, který je kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="e6b58-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="e6b58-105">Metoda spustí všechny úlohy a vrátí jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="e6b58-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="e6b58-106">Jedna úloha je dokončena po dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e6b58-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="e6b58-107">Tento příklad ukazuje, jak použít token zrušení společně s `WhenAny` pro udržení prvního úkol k dokončení z kolekce úkolů a zrušení zbývajících úkolů.</span><span class="sxs-lookup"><span data-stu-id="e6b58-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="e6b58-108">Každý úkol umožňuje stažení obsahu webu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="e6b58-109">Příklad zobrazuje délku obsahu prvního stahování pro dokončení a zruší ostatní stahování.</span><span class="sxs-lookup"><span data-stu-id="e6b58-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6b58-110">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="e6b58-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="e6b58-111">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="e6b58-111">Downloading the Example</span></span>  
 <span data-ttu-id="e6b58-112">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="e6b58-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="e6b58-113">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6b58-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="e6b58-114">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="e6b58-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="e6b58-115">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="e6b58-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="e6b58-116">V **Průzkumníka řešení**, otevřete místní nabídku **CancelAfterOneTask** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6b58-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="e6b58-117">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="e6b58-118">Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="e6b58-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="e6b58-119">Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="e6b58-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="e6b58-120">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="e6b58-121">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="e6b58-121">Building the Example</span></span>  
 <span data-ttu-id="e6b58-122">V příkladu v tomto tématu se přidá do projektu, který je napsán v jazyce [zrušení asynchronní úlohy nebo seznamu úloh](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušení seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="e6b58-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="e6b58-123">V příkladu se používá stejné uživatelské rozhraní, i když **zrušit** tlačítko není použito explicitně.</span><span class="sxs-lookup"><span data-stu-id="e6b58-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="e6b58-124">Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6b58-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="e6b58-125">Přidejte změny v tomto tématu do daného projektu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="e6b58-126">V souboru MainWindow.xaml.vb **CancelAListOfTasks** projektu, zahajte přechod přesunutím kroků zpracování pro každý web ze smyčky v `AccessTheWebAsync` do následující asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="e6b58-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="e6b58-127">V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metodu pro vytvoření a spuštění úloh v poli.</span><span class="sxs-lookup"><span data-stu-id="e6b58-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="e6b58-128">Použití `WhenAny` na pole vrátí jeden úkol, který, když je očekáváno, je vyhodnocen jako první úkol k dosažení dokončení v poli úloh.</span><span class="sxs-lookup"><span data-stu-id="e6b58-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="e6b58-129">Proveďte následující změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e6b58-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="e6b58-130">Hvězdičky označují změny v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="e6b58-131">Okomentujte nebo odstraňte smyčku.</span><span class="sxs-lookup"><span data-stu-id="e6b58-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="e6b58-132">Vytvoření dotazu, který při spuštění vytvoří kolekci obecných úkolů.</span><span class="sxs-lookup"><span data-stu-id="e6b58-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="e6b58-133">Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e6b58-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3. <span data-ttu-id="e6b58-134">Volání `ToArray` spustit dotaz a spustilo úlohu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="e6b58-135">Použití `WhenAny` metoda v dalším kroku by spustilo dotaz a spustilo úlohu bez použití `ToArray`, ale jiné metody nemusí.</span><span class="sxs-lookup"><span data-stu-id="e6b58-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="e6b58-136">Nejbezpečnější metodou je vynutit spuštění dotazu explicitně.</span><span class="sxs-lookup"><span data-stu-id="e6b58-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. <span data-ttu-id="e6b58-137">Volání `WhenAny` na kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="e6b58-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="e6b58-138">`WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="e6b58-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="e6b58-139">To znamená `WhenAny` vrátí úkol, který se vyhodnocuje do jediné `Task(Of Integer)` nebo `Task<int>` pokus je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="e6b58-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="e6b58-140">Jeden úkol je první úkol v kolekci pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="e6b58-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="e6b58-141">Někdo přiřadí úkol, který skončil první `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="e6b58-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="e6b58-142">Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je návratový typ `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="e6b58-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5. <span data-ttu-id="e6b58-143">V tomto příkladu se zajímáte pouze úloha, která skončí jako první.</span><span class="sxs-lookup"><span data-stu-id="e6b58-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="e6b58-144">Proto použít <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušení zbývajících úkolů.</span><span class="sxs-lookup"><span data-stu-id="e6b58-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6. <span data-ttu-id="e6b58-145">Nakonec vyčkejte, než `firstFinishedTask` načte délku stahovaného obsahu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="e6b58-146">Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="e6b58-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="e6b58-147">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="e6b58-147">Complete Example</span></span>  
 <span data-ttu-id="e6b58-148">Následující kód je celý soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs pro příklad.</span><span class="sxs-lookup"><span data-stu-id="e6b58-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="e6b58-149">Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6b58-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="e6b58-150">Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e6b58-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="e6b58-151">Stáhnete projekt z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e6b58-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6b58-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b58-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="e6b58-153">Doladění aplikace s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b58-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="e6b58-154">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b58-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e6b58-155">Ukázka asynchronní metody: Vyladění aplikace</span><span class="sxs-lookup"><span data-stu-id="e6b58-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
