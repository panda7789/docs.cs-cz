---
title: Zpracování asynchronních úloh po jejich dokončení
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: b618fd6bf80551231d2b285fd0e8aef688d00d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71736733"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="c299d-102">Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="c299d-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="c299d-103">Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>aplikace můžete spustit více úkolů najednou a zpracovat je jeden po druhém při jejich dokončení, nikoli je zpracovat v pořadí, ve kterém jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="c299d-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="c299d-104">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="c299d-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="c299d-105">Každý úkol stáhne obsah zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="c299d-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="c299d-106">V každé iteraci smyčky while očekávané `WhenAny` volání vrátí úlohu v kolekci úkolů, které dokončí jeho stažení jako první.</span><span class="sxs-lookup"><span data-stu-id="c299d-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="c299d-107">Tato úloha je odebrána z kolekce a zpracována.</span><span class="sxs-lookup"><span data-stu-id="c299d-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="c299d-108">Smyčka se opakuje, dokud kolekce neobsahuje žádné další úkoly.</span><span class="sxs-lookup"><span data-stu-id="c299d-108">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="c299d-109">Chcete-li spustit příklady, musíte mít Visual Studio (2012 nebo novější) a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="c299d-109">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="c299d-110">Stažení ukázkového řešení</span><span class="sxs-lookup"><span data-stu-id="c299d-110">Download an example solution</span></span>

<span data-ttu-id="c299d-111">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="c299d-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="c299d-112">Pokud nechcete stáhnout projekt, můžete si prohlédnout *soubor MainWindow.xaml.cs* na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c299d-112">If you don't want to download the project, you can review the *MainWindow.xaml.cs* file at the end of this topic instead.</span></span>

1. <span data-ttu-id="c299d-113">Extrahujte soubory, které jste stáhli ze souboru *ZIP,* a spusťte aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c299d-113">Extract the files that you downloaded from the *.zip* file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="c299d-114">Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="c299d-114">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="c299d-115">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste stáhli, a potom otevřete soubor řešení *(.sln)* pro *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span><span class="sxs-lookup"><span data-stu-id="c299d-115">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (*.sln*) file for *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span></span>

4. <span data-ttu-id="c299d-116">V **Průzkumníku řešení**otevřete místní nabídku projektu **ProcessTasksAsTheyFinish** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="c299d-116">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="c299d-117">Zvolte klávesu <kbd>F5</kbd> pro spuštění programu s laděním nebo stisknutím kláves <kbd>Ctrl</kbd>+<kbd>F5</kbd> program spusťte bez ladění.</span><span class="sxs-lookup"><span data-stu-id="c299d-117">Choose the <kbd>F5</kbd> key to run the program with debugging or, press <kbd>Ctrl</kbd>+<kbd>F5</kbd> keys to run the program without debugging it.</span></span>

6. <span data-ttu-id="c299d-118">Spusťte projekt několikrát a ověřte, zda se stažené délky nevždy zobrazují ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c299d-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="c299d-119">Vytvořte si program sami</span><span class="sxs-lookup"><span data-stu-id="c299d-119">Create the program yourself</span></span>

<span data-ttu-id="c299d-120">Tento příklad přidá ke kódu, který je vyvinut v [zrušit zbývající asynchronní úkoly po dokončení jednoho (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)a používá stejné ui.</span><span class="sxs-lookup"><span data-stu-id="c299d-120">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="c299d-121">Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v [části Stažení příkladu,](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) ale nastavte **CancelAfterOneTask** jako projekt po spuštění.</span><span class="sxs-lookup"><span data-stu-id="c299d-121">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="c299d-122">Přidejte změny v tomto `AccessTheWebAsync` tématu k metodě v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="c299d-122">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="c299d-123">Změny jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="c299d-123">The changes are marked with asterisks.</span></span>

<span data-ttu-id="c299d-124">Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="c299d-124">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="c299d-125">Každé volání `ProcessURLAsync` do následujícího <xref:System.Threading.Tasks.Task%601>kódu `TResult` vrátí , kde je celé číslo:</span><span class="sxs-lookup"><span data-stu-id="c299d-125">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="c299d-126">V *MainWindow.xaml.cs* souboru projektu proveďte následující `AccessTheWebAsync` změny metody:</span><span class="sxs-lookup"><span data-stu-id="c299d-126">In the *MainWindow.xaml.cs* file of the project, make the following changes to the `AccessTheWebAsync` method:</span></span>

- <span data-ttu-id="c299d-127">Spusťte dotaz <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> použitím <xref:System.Linq.Enumerable.ToArray%2A>namísto .</span><span class="sxs-lookup"><span data-stu-id="c299d-127">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- <span data-ttu-id="c299d-128">Přidejte `while` smyčku, která provádí následující kroky pro každou úlohu v kolekci:</span><span class="sxs-lookup"><span data-stu-id="c299d-128">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1. <span data-ttu-id="c299d-129">Čeká na volání `WhenAny` k identifikaci první úkol v kolekci k dokončení jeho stažení.</span><span class="sxs-lookup"><span data-stu-id="c299d-129">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. <span data-ttu-id="c299d-130">Odebere tento úkol z kolekce.</span><span class="sxs-lookup"><span data-stu-id="c299d-130">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. <span data-ttu-id="c299d-131">Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="c299d-131">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="c299d-132">Proměnná `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> `TReturn` kde je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c299d-132">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="c299d-133">Úloha je již dokončena, ale čekáte na to, abyste načetli délku staženého webu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c299d-133">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="c299d-134">Pokud je chyba `await` úlohy, vyvolá první podřízenou výjimku uloženou `AggregateException`v , na rozdíl od čtení `Result` vlastnosti, která by vyvolána `AggregateException`.</span><span class="sxs-lookup"><span data-stu-id="c299d-134">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the `Result` property which would throw the `AggregateException`.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="c299d-135">Spusťte program několikrát a ověřte, zda se stažené délky nevždy zobrazují ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c299d-135">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="c299d-136">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které zahrnují malý počet úkolů.</span><span class="sxs-lookup"><span data-stu-id="c299d-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="c299d-137">Jiné přístupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="c299d-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="c299d-138">Další informace a příklady naleznete v [tématu Zpracování úloh při jejich dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="c299d-138">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="c299d-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="c299d-139">Complete example</span></span>

<span data-ttu-id="c299d-140">Následující kód je úplný text *MainWindow.xaml.cs* souboru pro příklad.</span><span class="sxs-lookup"><span data-stu-id="c299d-140">The following code is the complete text of the *MainWindow.xaml.cs* file for the example.</span></span> <span data-ttu-id="c299d-141">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="c299d-141">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="c299d-142">Vezměte také na vědomí, že <xref:System.Net.Http>je nutné přidat odkaz na .</span><span class="sxs-lookup"><span data-stu-id="c299d-142">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="c299d-143">Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="c299d-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a><span data-ttu-id="c299d-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="c299d-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="c299d-145">Jemné doladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="c299d-145">Fine-Tuning Your Async Application (C#)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="c299d-146">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="c299d-146">Asynchronous Programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="c299d-147">Asynchronní ukázka: Jemné doladění aplikace</span><span class="sxs-lookup"><span data-stu-id="c299d-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
