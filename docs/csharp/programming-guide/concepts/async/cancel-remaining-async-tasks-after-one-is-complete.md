---
title: Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: e829254c1cd47da16b14aa9c2c90312a97b4b581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169971"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="a7f98-102">Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)</span><span class="sxs-lookup"><span data-stu-id="a7f98-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="a7f98-103">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody společně s <xref:System.Threading.CancellationToken>a , můžete zrušit všechny zbývající úkoly po dokončení jednoho úkolu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="a7f98-104">Metoda `WhenAny` trvá argument, který je kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="a7f98-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="a7f98-105">Metoda spustí všechny úkoly a vrátí jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="a7f98-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="a7f98-106">Jeden úkol je dokončen po dokončení jakékoli úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a7f98-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="a7f98-107">Tento příklad ukazuje, jak použít token `WhenAny` zrušení ve spojení s podržet první úkol dokončit z kolekce úkolů a zrušit zbývající úkoly.</span><span class="sxs-lookup"><span data-stu-id="a7f98-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="a7f98-108">Každý úkol stáhne obsah webu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="a7f98-109">V příkladu se zobrazí délka obsahu prvního stažení k dokončení a zruší ostatní stahování.</span><span class="sxs-lookup"><span data-stu-id="a7f98-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7f98-110">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="a7f98-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a7f98-111">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="a7f98-111">Downloading the Example</span></span>  
 <span data-ttu-id="a7f98-112">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="a7f98-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="a7f98-113">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7f98-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="a7f98-114">Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.</span><span class="sxs-lookup"><span data-stu-id="a7f98-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="a7f98-115">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="a7f98-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="a7f98-116">V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAfterOneTask** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="a7f98-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="a7f98-117">Zvolte klávesu F5 pro spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a7f98-118">Zvolte klávesy Ctrl+F5 pro spuštění projektu bez jeho ladění.</span><span class="sxs-lookup"><span data-stu-id="a7f98-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="a7f98-119">Spusťte program několikrát a ověřte, zda se nejprve dokončí různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="a7f98-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="a7f98-120">Pokud projekt nechcete stáhnout, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a7f98-121">Vytvoření příkladu</span><span class="sxs-lookup"><span data-stu-id="a7f98-121">Building the Example</span></span>  
 <span data-ttu-id="a7f98-122">Příklad v tomto tématu přidá do projektu, který je vyvinut v [Zrušit asynchronní úkol nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="a7f98-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="a7f98-123">Příklad používá stejné ui, i když **tlačítko Storno** není použit explicitně.</span><span class="sxs-lookup"><span data-stu-id="a7f98-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="a7f98-124">Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **CancelAListOfTasks** jako **projekt StartUp**Project .</span><span class="sxs-lookup"><span data-stu-id="a7f98-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="a7f98-125">Přidejte změny v tomto tématu do tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="a7f98-126">V souboru MainWindow.xaml.cs projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování `AccessTheWebAsync` pro každý web ze smyčky do následující asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="a7f98-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="a7f98-127">V `AccessTheWebAsync`tomto příkladu používá <xref:System.Linq.Enumerable.ToArray%2A> dotaz, metodu a metodu `WhenAny` k vytvoření a spuštění pole úkolů.</span><span class="sxs-lookup"><span data-stu-id="a7f98-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="a7f98-128">Aplikace `WhenAny` pole vrátí jeden úkol, který v případě čekání vyhodnotí první úkol k dosažení dokončení v poli úkolů.</span><span class="sxs-lookup"><span data-stu-id="a7f98-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="a7f98-129">Proveďte následující `AccessTheWebAsync`změny v .</span><span class="sxs-lookup"><span data-stu-id="a7f98-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a7f98-130">Hvězdičky označují změny v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="a7f98-131">Zakomentujte nebo odstraňte smyčku.</span><span class="sxs-lookup"><span data-stu-id="a7f98-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="a7f98-132">Vytvořte dotaz, který při spuštění vytvoří kolekci obecných úloh.</span><span class="sxs-lookup"><span data-stu-id="a7f98-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="a7f98-133">Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> `TResult` kde je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a7f98-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="a7f98-134">Volání `ToArray` spuštění dotazu a spuštění úloh.</span><span class="sxs-lookup"><span data-stu-id="a7f98-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="a7f98-135">Použití `WhenAny` metody v dalším kroku by spustit dotaz a spustit `ToArray`úkoly bez použití , ale jiné metody nemusí.</span><span class="sxs-lookup"><span data-stu-id="a7f98-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="a7f98-136">Nejbezpečnější praxe je vynutit provádění dotazu explicitně.</span><span class="sxs-lookup"><span data-stu-id="a7f98-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="a7f98-137">Volání `WhenAny` na shromažďování úkolů.</span><span class="sxs-lookup"><span data-stu-id="a7f98-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="a7f98-138">`WhenAny`vrátí `Task(Of Task(Of Integer))` hodnotu a nebo `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="a7f98-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="a7f98-139">To znamená `WhenAny` vrátí úkol, který vyhodnotí jeden `Task(Of Integer)` nebo `Task<int>` když je očekáván.</span><span class="sxs-lookup"><span data-stu-id="a7f98-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="a7f98-140">Tento jediný úkol je první úkol v kolekci dokončit.</span><span class="sxs-lookup"><span data-stu-id="a7f98-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="a7f98-141">Úkol, který byl dokončen `firstFinishedTask`jako první, je přiřazen aplikaci .</span><span class="sxs-lookup"><span data-stu-id="a7f98-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="a7f98-142">Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je `ProcessURLAsync`návratový typ .</span><span class="sxs-lookup"><span data-stu-id="a7f98-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="a7f98-143">V tomto příkladu vás zajímá pouze úkol, který je dokončen jako první.</span><span class="sxs-lookup"><span data-stu-id="a7f98-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="a7f98-144">Proto slouží <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ke zrušení zbývající úkoly.</span><span class="sxs-lookup"><span data-stu-id="a7f98-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="a7f98-145">Nakonec počkejte `firstFinishedTask` na načtení délky staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="a7f98-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="a7f98-146">Spusťte program několikrát a ověřte, zda se nejprve dokončí různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="a7f98-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="a7f98-147">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="a7f98-147">Complete Example</span></span>  
 <span data-ttu-id="a7f98-148">Následující kód je kompletní MainWindow.xaml.cs soubor pro příklad.</span><span class="sxs-lookup"><span data-stu-id="a7f98-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="a7f98-149">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="a7f98-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a7f98-150">Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .</span><span class="sxs-lookup"><span data-stu-id="a7f98-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a7f98-151">Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="a7f98-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.
            //    // Argument ct carries the message if the Cancel button is chosen.
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7f98-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7f98-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="a7f98-153">Jemné doladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="a7f98-153">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="a7f98-154">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="a7f98-154">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="a7f98-155">Asynchronní ukázka: Jemné doladění aplikace</span><span class="sxs-lookup"><span data-stu-id="a7f98-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
