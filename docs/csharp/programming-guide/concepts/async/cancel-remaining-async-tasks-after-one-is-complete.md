---
title: "Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5e1a899223d0f6d15e6851c9320275bafe876118
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="4b85a-102">Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich</span><span class="sxs-lookup"><span data-stu-id="4b85a-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="4b85a-103">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda společně s <xref:System.Threading.CancellationToken>, můžete zrušit všechny zbývající úkoly po dokončení úloh.</span><span class="sxs-lookup"><span data-stu-id="4b85a-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="4b85a-104">`WhenAny` Metoda přebírá argument, který je kolekce úloh.</span><span class="sxs-lookup"><span data-stu-id="4b85a-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="4b85a-105">Metoda spustí všechny úlohy a vrátí jednu úlohu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="4b85a-106">Jediná úloha je dokončena po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4b85a-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="4b85a-107">Tento příklad ukazuje, jak používat token zrušení ve spojení s `WhenAny` k uložení do první úlohy a dokončit z kolekce úloh a zrušit ve zbývajících úkolech.</span><span class="sxs-lookup"><span data-stu-id="4b85a-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="4b85a-108">Každý úkol stáhne obsah webu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="4b85a-109">V příkladu se zobrazí délka obsahu první stahování dokončit a zruší další soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="4b85a-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b85a-110">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="4b85a-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="4b85a-111">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="4b85a-111">Downloading the Example</span></span>  
 <span data-ttu-id="4b85a-112">Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="4b85a-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="4b85a-113">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b85a-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4b85a-114">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b85a-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="4b85a-115">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="4b85a-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="4b85a-116">V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterOneTask** projektu a potom vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="4b85a-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="4b85a-117">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="4b85a-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="4b85a-118">Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.</span><span class="sxs-lookup"><span data-stu-id="4b85a-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="4b85a-119">Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="4b85a-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="4b85a-120">Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="4b85a-121">Vytváření v příkladu</span><span class="sxs-lookup"><span data-stu-id="4b85a-121">Building the Example</span></span>  
 <span data-ttu-id="4b85a-122">V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="4b85a-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="4b85a-123">Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="4b85a-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="4b85a-124">K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="4b85a-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="4b85a-125">Do tohoto projektu přidáte změny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="4b85a-126">V souboru MainWindow.xaml.cs **CancelAListOfTasks** projektu, spusťte přechodu přesunutím zpracování kroky pro každý web smyčky v `AccessTheWebAsync` následující asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="4b85a-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="4b85a-127">V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metoda pro vytvoření a spuštění úloh v poli.</span><span class="sxs-lookup"><span data-stu-id="4b85a-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="4b85a-128">Použití `WhenAny` do pole vrátí jeden úkol, pokud je očekáváno, vyhodnotí jako první úlohou k dosažení dokončování úloh v poli.</span><span class="sxs-lookup"><span data-stu-id="4b85a-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="4b85a-129">Proveďte následující změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="4b85a-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="4b85a-130">Hvězdičky označit změny v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="4b85a-131">Komentář nebo odstranit smyčky.</span><span class="sxs-lookup"><span data-stu-id="4b85a-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="4b85a-132">Vytvořit dotaz, která po provedení vytvoří kolekci obecné úlohy.</span><span class="sxs-lookup"><span data-stu-id="4b85a-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="4b85a-133">Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4b85a-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  <span data-ttu-id="4b85a-134">Volání `ToArray` proveďte dotaz a spusťte úlohy.</span><span class="sxs-lookup"><span data-stu-id="4b85a-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="4b85a-135">Použití `WhenAny` metoda v dalším kroku by provést dotaz a spustit úlohy bez použití `ToArray`, ale jiné metody možná není.</span><span class="sxs-lookup"><span data-stu-id="4b85a-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="4b85a-136">Nejbezpečnější metodou je explicitně vynutit spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="4b85a-137">Volání `WhenAny` na kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="4b85a-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="4b85a-138">`WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="4b85a-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="4b85a-139">To znamená `WhenAny` vrátí úlohu, která vyhodnotí na jednu `Task(Of Integer)` nebo `Task<int>` Pokud je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="4b85a-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="4b85a-140">Tento jeden úkol je první úloha v kolekci ukončíte.</span><span class="sxs-lookup"><span data-stu-id="4b85a-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="4b85a-141">Úloha, která nejprve dokončení je přiřazen k `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="4b85a-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="4b85a-142">Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože se jedná návratový typ `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="4b85a-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  <span data-ttu-id="4b85a-143">V tomto příkladu co vás zajímá pouze úloha, která nejprve dokončí.</span><span class="sxs-lookup"><span data-stu-id="4b85a-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="4b85a-144">Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušit ve zbývajících úkolech.</span><span class="sxs-lookup"><span data-stu-id="4b85a-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  <span data-ttu-id="4b85a-145">Nakonec await `firstFinishedTask` načíst délka staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 <span data-ttu-id="4b85a-146">Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="4b85a-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="4b85a-147">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="4b85a-147">Complete Example</span></span>  
 <span data-ttu-id="4b85a-148">Následující kód je kompletní MainWindow.xaml.cs soubor v příkladu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="4b85a-149">Hvězdičky označit prvky, které byly přidány v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4b85a-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="4b85a-150">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="4b85a-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="4b85a-151">Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="4b85a-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
            //        String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
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
            resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b85a-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b85a-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="4b85a-153">Vyladění s modifikátorem Async aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="4b85a-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="4b85a-154">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="4b85a-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="4b85a-155">Ukázka asynchronního: Jemnou ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="4b85a-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
