---
title: Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: cd7214313fbe8f61b56089cf103fde10d6bc47a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648831"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="4f1b6-102">Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f1b6-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="4f1b6-103">S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete spustit více úkolů současně a zpracovat je postupně tak, jak jsou dokončeny namísto zpracování v pořadí, ve kterém se spouští.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="4f1b6-104">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="4f1b6-105">Každý úkol umožňuje stažení obsahu zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="4f1b6-106">V každé iteraci nějakou smyčky, očekávané volání metody `WhenAny` vrátí úkol v kolekci úkolů, která dokončí stahování jako první.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="4f1b6-107">Tento úkol je odebrán z kolekce a zpracování.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="4f1b6-108">Smyčka se opakuje dokud kolekce neobsahuje žádné další úlohy.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f1b6-109">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="4f1b6-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="4f1b6-110">Downloading the Example</span></span>  
 <span data-ttu-id="4f1b6-111">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="4f1b6-112">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="4f1b6-113">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="4f1b6-114">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="4f1b6-115">V **Průzkumníka řešení**, otevřete místní nabídku **ProcessTasksAsTheyFinish** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="4f1b6-116">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="4f1b6-117">Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="4f1b6-118">Projekt několikrát spusťte a tak ověřte, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="4f1b6-119">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="4f1b6-120">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="4f1b6-120">Building the Example</span></span>  
 <span data-ttu-id="4f1b6-121">V tomto příkladu přidá do kódu, který je napsán v jazyce [zrušení zbývajících asynchronních úloh po jeden je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a používá stejné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="4f1b6-122">Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAfterOneTask** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="4f1b6-123">Přidejte změny v tomto tématu a `AccessTheWebAsync` metody v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="4f1b6-124">Změny jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="4f1b6-125">**CancelAfterOneTask** projekt již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="4f1b6-126">Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="4f1b6-127">V souboru MainWindow.xaml.vb nebo projektu, proveďte následující změny `AccessTheWebAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-127">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="4f1b6-128">Spusťte dotaz s použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="4f1b6-129">Přidat nějakou smyčku, která provede následující kroky pro každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="4f1b6-130">Čeká volání `WhenAny` identifikovat první úkol v kolekci, která se dokončí stažení.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="4f1b6-131">Odebere tento úkol z kolekce.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-131">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. <span data-ttu-id="4f1b6-132">Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="4f1b6-133">`firstFinishedTask` Proměnná je <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="4f1b6-134">Úloha je již dokončena, ale můžete od něj načte délku staženého webu, jak ukazuje následující příklad očekávat.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="4f1b6-135">Projekt by měl spustit několikrát k ověření, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4f1b6-136">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které se týkají malého počtu úkolů.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="4f1b6-137">Další postupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="4f1b6-138">Další informace a příklady najdete v tématu [zpracování úkolů při jejich dokončování](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="4f1b6-138">For more information and examples, see [Processing Tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="4f1b6-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="4f1b6-139">Complete Example</span></span>  
 <span data-ttu-id="4f1b6-140">Následující kód je celý text souboru MainWindow.xaml.vb pro příklad.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-140">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="4f1b6-141">Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="4f1b6-142">Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="4f1b6-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="4f1b6-143">Stáhnete projekt z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="4f1b6-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f1b6-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f1b6-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="4f1b6-145">Doladění aplikace s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f1b6-145">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="4f1b6-146">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f1b6-146">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4f1b6-147">Ukázka asynchronní metody: Vyladění aplikace</span><span class="sxs-lookup"><span data-stu-id="4f1b6-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
