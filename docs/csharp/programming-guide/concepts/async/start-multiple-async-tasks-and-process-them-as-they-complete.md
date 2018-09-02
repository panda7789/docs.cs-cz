---
title: Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: d59b65e456c528c63c79c97f6c75c328066be631
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416395"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="432ce-102">Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="432ce-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="432ce-103">S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete spustit více úkolů současně a zpracovat je postupně tak, jak jsou dokončeny namísto zpracování v pořadí, ve kterém se spouští.</span><span class="sxs-lookup"><span data-stu-id="432ce-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="432ce-104">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="432ce-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="432ce-105">Každý úkol umožňuje stažení obsahu zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="432ce-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="432ce-106">V každé iteraci nějakou smyčky, očekávané volání metody `WhenAny` vrátí úkol v kolekci úkolů, která dokončí stahování jako první.</span><span class="sxs-lookup"><span data-stu-id="432ce-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="432ce-107">Tento úkol je odebrán z kolekce a zpracování.</span><span class="sxs-lookup"><span data-stu-id="432ce-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="432ce-108">Smyčka se opakuje dokud kolekce neobsahuje žádné další úlohy.</span><span class="sxs-lookup"><span data-stu-id="432ce-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="432ce-109">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="432ce-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="432ce-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="432ce-110">Downloading the Example</span></span>  
 <span data-ttu-id="432ce-111">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="432ce-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="432ce-112">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="432ce-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="432ce-113">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="432ce-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="432ce-114">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="432ce-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="432ce-115">V **Průzkumníka řešení**, otevřete místní nabídku **ProcessTasksAsTheyFinish** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="432ce-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="432ce-116">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="432ce-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="432ce-117">Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="432ce-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="432ce-118">Projekt několikrát spusťte a tak ověřte, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="432ce-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="432ce-119">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="432ce-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="432ce-120">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="432ce-120">Building the Example</span></span>  
 <span data-ttu-id="432ce-121">V tomto příkladu přidá do kódu, který je napsán v jazyce [zrušení zbývajících asynchronních úloh po jeden je úplná (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[zrušení zbývajících asynchronních úloh po jeden je úplná](https://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) a používá stejné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="432ce-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](https://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="432ce-122">Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAfterOneTask** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="432ce-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="432ce-123">Přidejte změny v tomto tématu a `AccessTheWebAsync` metody v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="432ce-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="432ce-124">Změny jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="432ce-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="432ce-125">**CancelAfterOneTask** projekt již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="432ce-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="432ce-126">Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="432ce-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="432ce-127">V souboru MainWindow.xaml.cs projektu proveďte následující změny `AccessTheWebAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="432ce-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="432ce-128">Spusťte dotaz s použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="432ce-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="432ce-129">Přidat nějakou smyčku, která provede následující kroky pro každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="432ce-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="432ce-130">Čeká volání `WhenAny` identifikovat první úkol v kolekci, která se dokončí stažení.</span><span class="sxs-lookup"><span data-stu-id="432ce-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="432ce-131">Odebere tento úkol z kolekce.</span><span class="sxs-lookup"><span data-stu-id="432ce-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="432ce-132">Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="432ce-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="432ce-133">`firstFinishedTask` Proměnná je <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="432ce-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="432ce-134">Úloha je již dokončena, ale můžete od něj načte délku staženého webu, jak ukazuje následující příklad očekávat.</span><span class="sxs-lookup"><span data-stu-id="432ce-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="432ce-135">Projekt by měl spustit několikrát k ověření, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="432ce-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="432ce-136">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které se týkají malého počtu úkolů.</span><span class="sxs-lookup"><span data-stu-id="432ce-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="432ce-137">Další postupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="432ce-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="432ce-138">Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="432ce-138">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="432ce-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="432ce-139">Complete Example</span></span>  
 <span data-ttu-id="432ce-140">Následující kód je celý text souboru MainWindow.xaml.cs pro příklad.</span><span class="sxs-lookup"><span data-stu-id="432ce-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="432ce-141">Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="432ce-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="432ce-142">Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="432ce-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="432ce-143">Stáhnete projekt z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="432ce-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="432ce-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="432ce-144">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="432ce-145">Doladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="432ce-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="432ce-146">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="432ce-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="432ce-147">Asynchronní vzorek: Jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="432ce-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
