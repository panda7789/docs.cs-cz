---
title: Zrušení zbývajících asynchronních úloh po dokončení jedné z nich (C#)
description: Použijte metodu Task. WhenAny spolu s CancellationToken v jazyce C# pro zrušení všech zbývajících úloh, pokud je v tomto příkladu dokončen jeden úkol.
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 6de60c8faa93752961e3703a042885a71972cc4a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925277"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="f9479-103">Zrušení zbývajících asynchronních úloh po dokončení jedné z nich (C#)</span><span class="sxs-lookup"><span data-stu-id="f9479-103">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="f9479-104">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody společně s a <xref:System.Threading.CancellationToken> můžete zrušit všechny zbývající úlohy, když je jeden úkol dokončen.</span><span class="sxs-lookup"><span data-stu-id="f9479-104">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="f9479-105">`WhenAny`Metoda přebírá argument, který je kolekcí úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-105">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="f9479-106">Metoda spustí všechny úlohy a vrátí jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="f9479-106">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="f9479-107">Jedna úloha je dokončena, když je dokončen libovolný úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="f9479-107">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="f9479-108">Tento příklad ukazuje, jak použít token zrušení ve spojení s `WhenAny` pro uložení na první úkol pro dokončení z kolekce úkolů a zrušení zbývajících úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-108">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="f9479-109">Každý úkol stáhne obsah webu.</span><span class="sxs-lookup"><span data-stu-id="f9479-109">Each task downloads the contents of a website.</span></span> <span data-ttu-id="f9479-110">V příkladu se zobrazí délka obsahu prvního stažení, která se má dokončit, a ostatní soubory ke stažení se zruší.</span><span class="sxs-lookup"><span data-stu-id="f9479-110">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9479-111">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f9479-111">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="f9479-112">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="f9479-112">Downloading the Example</span></span>  
 <span data-ttu-id="f9479-113">Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="f9479-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="f9479-114">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9479-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="f9479-115">Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="f9479-115">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="f9479-116">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="f9479-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="f9479-117">V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAfterOneTask** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="f9479-117">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="f9479-118">Kliknutím na klávesu F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f9479-118">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="f9479-119">Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="f9479-119">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="f9479-120">Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="f9479-120">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="f9479-121">Pokud nechcete stáhnout projekt, můžete si prohlédnout soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f9479-121">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="f9479-122">Vytvoření příkladu</span><span class="sxs-lookup"><span data-stu-id="f9479-122">Building the Example</span></span>  
 <span data-ttu-id="f9479-123">Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-123">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="f9479-124">V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="f9479-124">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="f9479-125">Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** .</span><span class="sxs-lookup"><span data-stu-id="f9479-125">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="f9479-126">Přidejte změny v tomto tématu do projektu.</span><span class="sxs-lookup"><span data-stu-id="f9479-126">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="f9479-127">V souboru MainWindow.xaml.cs projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování pro každý web z smyčky do `AccessTheWebAsync` následující asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="f9479-127">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="f9479-128">V `AccessTheWebAsync` je v tomto příkladu použit dotaz, <xref:System.Linq.Enumerable.ToArray%2A> Metoda a `WhenAny` metoda pro vytvoření a spuštění pole úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-128">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="f9479-129">Aplikace `WhenAny` do pole vrátí jeden úkol, který je při očekávání vyhodnocen jako první úkol, aby se dosáhlo dokončení v poli úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-129">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="f9479-130">Proveďte následující změny v `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="f9479-130">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f9479-131">Hvězdičky označují změny v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="f9479-131">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="f9479-132">Odkomentujte nebo odstraňte smyčku.</span><span class="sxs-lookup"><span data-stu-id="f9479-132">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="f9479-133">Vytvoří dotaz, který při spuštění vytvoří kolekci obecných úloh.</span><span class="sxs-lookup"><span data-stu-id="f9479-133">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="f9479-134">Každé volání `ProcessURLAsync` vrátí, <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f9479-134">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="f9479-135">Zavolejte `ToArray` na příkaz Spustit dotaz a spusťte úkoly.</span><span class="sxs-lookup"><span data-stu-id="f9479-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="f9479-136">Aplikace `WhenAny` metody v dalším kroku spustí dotaz a spustí úlohy bez použití `ToArray` , ale jiné metody nemusí.</span><span class="sxs-lookup"><span data-stu-id="f9479-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="f9479-137">Nejbezpečnější praxí je vynutit provádění dotazu explicitně.</span><span class="sxs-lookup"><span data-stu-id="f9479-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="f9479-138">Zavolejte `WhenAny` na kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-138">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="f9479-139">`WhenAny`Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>` .</span><span class="sxs-lookup"><span data-stu-id="f9479-139">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="f9479-140">To znamená, že `WhenAny` vrátí úlohu, která se vyhodnotí na jeden nebo v případě, že je `Task(Of Integer)` `Task<int>` očekávána.</span><span class="sxs-lookup"><span data-stu-id="f9479-140">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="f9479-141">Tento jeden úkol je prvním úkolem v kolekci, který má být dokončen.</span><span class="sxs-lookup"><span data-stu-id="f9479-141">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="f9479-142">Úkol, který byl dokončen jako první, je přiřazen `firstFinishedTask` .</span><span class="sxs-lookup"><span data-stu-id="f9479-142">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="f9479-143">Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> `TResult` , kde je celé číslo, protože to je návratový typ `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="f9479-143">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="f9479-144">V tomto příkladu vás zajímá jenom úkol, který končí jako první.</span><span class="sxs-lookup"><span data-stu-id="f9479-144">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="f9479-145">Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ke zrušení zbývajících úkolů.</span><span class="sxs-lookup"><span data-stu-id="f9479-145">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="f9479-146">Nakonec čeká `firstFinishedTask` na načtení délky staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="f9479-146">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="f9479-147">Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="f9479-147">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="f9479-148">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="f9479-148">Complete Example</span></span>  
 <span data-ttu-id="f9479-149">Následující kód je úplný soubor MainWindow.xaml.cs pro příklad.</span><span class="sxs-lookup"><span data-stu-id="f9479-149">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="f9479-150">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="f9479-150">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="f9479-151">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="f9479-151">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="f9479-152">Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f9479-152">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9479-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9479-153">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="f9479-154">Vyladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="f9479-154">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="f9479-155">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="f9479-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="f9479-156">Asynchronní vzorek: jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="f9479-156">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
