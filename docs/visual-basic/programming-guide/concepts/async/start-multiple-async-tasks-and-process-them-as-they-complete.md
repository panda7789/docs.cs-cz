---
title: Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b14171196a95e9a6a12f6b13f6f17d3cfe352bce
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266843"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="51625-102">Spuštění více asynchronních úloh a jejich zpracování po dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51625-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="51625-103">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>aplikace můžete spustit více úkolů najednou a zpracovat je jeden po druhém při jejich dokončení, nikoli je zpracovat v pořadí, ve kterém jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="51625-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="51625-104">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="51625-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="51625-105">Každý úkol stáhne obsah zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="51625-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="51625-106">V každé iteraci smyčky while očekávané `WhenAny` volání vrátí úlohu v kolekci úkolů, které dokončí jeho stažení jako první.</span><span class="sxs-lookup"><span data-stu-id="51625-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="51625-107">Tato úloha je odebrána z kolekce a zpracována.</span><span class="sxs-lookup"><span data-stu-id="51625-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="51625-108">Smyčka se opakuje, dokud kolekce neobsahuje žádné další úkoly.</span><span class="sxs-lookup"><span data-stu-id="51625-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51625-109">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="51625-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="51625-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="51625-110">Downloading the Example</span></span>  
 <span data-ttu-id="51625-111">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="51625-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="51625-112">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51625-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="51625-113">Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.</span><span class="sxs-lookup"><span data-stu-id="51625-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="51625-114">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="51625-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="51625-115">V **Průzkumníku řešení**otevřete místní nabídku projektu **ProcessTasksAsTheyFinish** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="51625-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="51625-116">Zvolte klávesu F5 pro spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="51625-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="51625-117">Zvolte klávesy Ctrl+F5 pro spuštění projektu bez jeho ladění.</span><span class="sxs-lookup"><span data-stu-id="51625-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="51625-118">Spusťte projekt několikrát a ověřte, zda se stažené délky nevždy zobrazují ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="51625-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="51625-119">Pokud nechcete stáhnout projekt, můžete zkontrolovat mainwindow.xaml.vb soubor na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="51625-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="51625-120">Vytvoření příkladu</span><span class="sxs-lookup"><span data-stu-id="51625-120">Building the Example</span></span>  
 <span data-ttu-id="51625-121">Tento příklad přidá ke kódu, který je vyvinut v [zrušit zbývající asynchronní úkoly po dokončení jednoho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a používá stejné ui.</span><span class="sxs-lookup"><span data-stu-id="51625-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="51625-122">Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **CancelAfterOneTask** jako **projekt Spuštění**.</span><span class="sxs-lookup"><span data-stu-id="51625-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="51625-123">Přidejte změny v tomto `AccessTheWebAsync` tématu k metodě v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="51625-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="51625-124">Změny jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="51625-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="51625-125">Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="51625-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="51625-126">Každé volání `ProcessURLAsync` v následujícím kódu <xref:System.Threading.Tasks.Task%601> `TResult` vrátí kde je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="51625-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="51625-127">V souboru MainWindow.xaml.vb projektu proveďte následující `AccessTheWebAsync` změny metody.</span><span class="sxs-lookup"><span data-stu-id="51625-127">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="51625-128">Spusťte dotaz <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> použitím <xref:System.Linq.Enumerable.ToArray%2A>namísto .</span><span class="sxs-lookup"><span data-stu-id="51625-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="51625-129">Přidejte smyčku while, která provádí následující kroky pro každou úlohu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="51625-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="51625-130">Čeká na volání `WhenAny` k identifikaci první úkol v kolekci k dokončení jeho stažení.</span><span class="sxs-lookup"><span data-stu-id="51625-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="51625-131">Odebere tento úkol z kolekce.</span><span class="sxs-lookup"><span data-stu-id="51625-131">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. <span data-ttu-id="51625-132">Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="51625-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="51625-133">Proměnná `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> `TReturn` kde je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="51625-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="51625-134">Úloha je již dokončena, ale čekáte na to, abyste načetli délku staženého webu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="51625-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="51625-135">Projekt byste měli spustit několikrát, abyste ověřili, že stažené délky se nevždy zobrazují ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="51625-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="51625-136">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které zahrnují malý počet úkolů.</span><span class="sxs-lookup"><span data-stu-id="51625-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="51625-137">Jiné přístupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="51625-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="51625-138">Další informace a příklady naleznete [v tématu Zpracování úloh při jejich dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="51625-138">For more information and examples, see [Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="51625-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="51625-139">Complete Example</span></span>  
 <span data-ttu-id="51625-140">Následující kód je úplný text mainwindow.xaml.vb souboru pro příklad.</span><span class="sxs-lookup"><span data-stu-id="51625-140">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="51625-141">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="51625-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="51625-142">Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .</span><span class="sxs-lookup"><span data-stu-id="51625-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="51625-143">Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="51625-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51625-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="51625-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="51625-145">Jemné doladění asynchronní aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51625-145">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="51625-146">Asynchronní programování s asynchronní a čeká (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51625-146">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="51625-147">Asynchronní ukázka: Jemné doladění aplikace</span><span class="sxs-lookup"><span data-stu-id="51625-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
