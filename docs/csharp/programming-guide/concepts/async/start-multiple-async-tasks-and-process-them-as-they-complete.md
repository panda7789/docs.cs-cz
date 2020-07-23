---
title: Zpracování asynchronních úloh po dokončení
description: Tento příklad ukazuje, jak použít Task. WhenAny v jazyce C# ke spuštění více úkolů a zpracování jejich výsledků při jejich dokončení, místo jejich zpracování v pořadí.
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a7cfa0bdf783fe9bb735241ca398fde7895f1493
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925147"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="0374c-103">Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="0374c-103">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="0374c-104">Pomocí nástroje <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> můžete spustit více úloh současně a zpracovat je jeden po jednom, protože jsou dokončeny, a nikoli jejich zpracování v pořadí, ve kterém jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="0374c-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="0374c-105">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="0374c-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="0374c-106">Každý úkol stáhne obsah zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="0374c-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="0374c-107">V každé iteraci smyčky while očekává volání metody `WhenAny` vrácení úlohy v kolekci úkolů, které dokončí stahování jako první.</span><span class="sxs-lookup"><span data-stu-id="0374c-107">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="0374c-108">Tato úloha je odebrána z kolekce a zpracována.</span><span class="sxs-lookup"><span data-stu-id="0374c-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="0374c-109">Smyčka se opakuje, dokud kolekce neobsahuje žádné další úlohy.</span><span class="sxs-lookup"><span data-stu-id="0374c-109">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="0374c-110">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio (2012 nebo novější) a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="0374c-110">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="0374c-111">Stažení ukázkového řešení</span><span class="sxs-lookup"><span data-stu-id="0374c-111">Download an example solution</span></span>

<span data-ttu-id="0374c-112">Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="0374c-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="0374c-113">Pokud nechcete stáhnout projekt, můžete místo toho zkontrolovat soubor *MainWindow.XAML.cs* na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0374c-113">If you don't want to download the project, you can review the *MainWindow.xaml.cs* file at the end of this topic instead.</span></span>

1. <span data-ttu-id="0374c-114">Extrahujte soubory, které jste stáhli ze souboru *. zip* , a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-114">Extract the files that you downloaded from the *.zip* file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="0374c-115">Na panelu nabídek vyberte **soubor**  >  **otevřít**  >  **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="0374c-115">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="0374c-116">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste stáhli, a poté otevřete soubor řešení (*. sln*) pro *AsyncFineTuningCS* / *AsyncFineTuningVB*.</span><span class="sxs-lookup"><span data-stu-id="0374c-116">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (*.sln*) file for *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span></span>

4. <span data-ttu-id="0374c-117">V **Průzkumník řešení**otevřete místní nabídku pro projekt **ProcessTasksAsTheyFinish** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="0374c-117">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="0374c-118">Zvolte klávesu <kbd>F5</kbd> ke spuštění programu v ladění nebo stiskněte klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> a program spusťte bez ladění.</span><span class="sxs-lookup"><span data-stu-id="0374c-118">Choose the <kbd>F5</kbd> key to run the program with debugging or, press <kbd>Ctrl</kbd>+<kbd>F5</kbd> keys to run the program without debugging it.</span></span>

6. <span data-ttu-id="0374c-119">Spusťte projekt několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0374c-119">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="0374c-120">Vytvoření programu sami</span><span class="sxs-lookup"><span data-stu-id="0374c-120">Create the program yourself</span></span>

<span data-ttu-id="0374c-121">Tento příklad přidá do kódu, který je vyvinut v části [zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)a používá stejné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0374c-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="0374c-122">Chcete-li sestavit příklad sami, postupujte podle pokynů v části [stažení ukázkového](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) oddílu, ale nastavte **CancelAfterOneTask** jako spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="0374c-122">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="0374c-123">Přidejte změny v tomto tématu do `AccessTheWebAsync` metody v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="0374c-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="0374c-124">Změny jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="0374c-124">The changes are marked with asterisks.</span></span>

<span data-ttu-id="0374c-125">Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="0374c-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="0374c-126">Každé volání do `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:</span><span class="sxs-lookup"><span data-stu-id="0374c-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="0374c-127">V souboru *MainWindow.XAML.cs* projektu proveďte následující změny `AccessTheWebAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="0374c-127">In the *MainWindow.xaml.cs* file of the project, make the following changes to the `AccessTheWebAsync` method:</span></span>

- <span data-ttu-id="0374c-128">Spusťte dotaz použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="0374c-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- <span data-ttu-id="0374c-129">Přidejte `while` smyčku, která provede následující kroky pro každý úkol v kolekci:</span><span class="sxs-lookup"><span data-stu-id="0374c-129">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1. <span data-ttu-id="0374c-130">Očekává volání `WhenAny` k identifikaci prvního úkolu v kolekci, aby bylo možné dokončit stahování.</span><span class="sxs-lookup"><span data-stu-id="0374c-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. <span data-ttu-id="0374c-131">Odebere úlohu z kolekce.</span><span class="sxs-lookup"><span data-stu-id="0374c-131">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. <span data-ttu-id="0374c-132">Čeká `firstFinishedTask` , který je vrácen voláním metody `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="0374c-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="0374c-133">`firstFinishedTask`Proměnná je <xref:System.Threading.Tasks.Task%601> , kde `TReturn` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="0374c-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="0374c-134">Úkol je již dokončen, ale očekáváte, že bude načtena délka staženého webu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0374c-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="0374c-135">Pokud dojde k chybě úlohy, `await` vyvolá první podřízenou výjimku uloženou v objektu `AggregateException` , na rozdíl od čtení `Result` vlastnosti, která by vyvolala `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="0374c-135">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the `Result` property which would throw the `AggregateException`.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="0374c-136">Spusťte program několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0374c-136">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="0374c-137">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, pro řešení problémů, které zahrnují malý počet úkolů.</span><span class="sxs-lookup"><span data-stu-id="0374c-137">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="0374c-138">Další přístupy jsou ale efektivnější, pokud máte velký počet úkolů, které je potřeba zpracovat.</span><span class="sxs-lookup"><span data-stu-id="0374c-138">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="0374c-139">Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="0374c-139">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="0374c-140">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="0374c-140">Complete example</span></span>

<span data-ttu-id="0374c-141">Následující kód je úplný text souboru *MainWindow.XAML.cs* pro příklad.</span><span class="sxs-lookup"><span data-stu-id="0374c-141">The following code is the complete text of the *MainWindow.xaml.cs* file for the example.</span></span> <span data-ttu-id="0374c-142">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="0374c-142">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="0374c-143">Všimněte si také, že je nutné přidat odkaz pro <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="0374c-143">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="0374c-144">Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="0374c-144">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0374c-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="0374c-145">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="0374c-146">Vyladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="0374c-146">Fine-Tuning Your Async Application (C#)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="0374c-147">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="0374c-147">Asynchronous Programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="0374c-148">Asynchronní vzorek: jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="0374c-148">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
