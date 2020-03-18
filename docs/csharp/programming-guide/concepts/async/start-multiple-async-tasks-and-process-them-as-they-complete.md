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
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)

Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>aplikace můžete spustit více úkolů najednou a zpracovat je jeden po druhém při jejich dokončení, nikoli je zpracovat v pořadí, ve kterém jsou spuštěny.

Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol stáhne obsah zadaného webu. V každé iteraci smyčky while očekávané `WhenAny` volání vrátí úlohu v kolekci úkolů, které dokončí jeho stažení jako první. Tato úloha je odebrána z kolekce a zpracována. Smyčka se opakuje, dokud kolekce neobsahuje žádné další úkoly.

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio (2012 nebo novější) a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="download-an-example-solution"></a>Stažení ukázkového řešení

Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.

> [!TIP]
> Pokud nechcete stáhnout projekt, můžete si prohlédnout *soubor MainWindow.xaml.cs* na konci tohoto tématu.

1. Extrahujte soubory, které jste stáhli ze souboru *ZIP,* a spusťte aplikaci Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste stáhli, a potom otevřete soubor řešení *(.sln)* pro *AsyncFineTuningCS*/*AsyncFineTuningVB*.

4. V **Průzkumníku řešení**otevřete místní nabídku projektu **ProcessTasksAsTheyFinish** a pak zvolte **Nastavit jako počáteční projekt**.

5. Zvolte klávesu <kbd>F5</kbd> pro spuštění programu s laděním nebo stisknutím kláves <kbd>Ctrl</kbd>+<kbd>F5</kbd> program spusťte bez ladění.

6. Spusťte projekt několikrát a ověřte, zda se stažené délky nevždy zobrazují ve stejném pořadí.

## <a name="create-the-program-yourself"></a>Vytvořte si program sami

Tento příklad přidá ke kódu, který je vyvinut v [zrušit zbývající asynchronní úkoly po dokončení jednoho (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)a používá stejné ui.

Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v [části Stažení příkladu,](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) ale nastavte **CancelAfterOneTask** jako projekt po spuštění. Přidejte změny v tomto `AccessTheWebAsync` tématu k metodě v tomto projektu. Změny jsou označeny hvězdičkami.

Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání `ProcessURLAsync` do následujícího <xref:System.Threading.Tasks.Task%601>kódu `TResult` vrátí , kde je celé číslo:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

V *MainWindow.xaml.cs* souboru projektu proveďte následující `AccessTheWebAsync` změny metody:

- Spusťte dotaz <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> použitím <xref:System.Linq.Enumerable.ToArray%2A>namísto .

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- Přidejte `while` smyčku, která provádí následující kroky pro každou úlohu v kolekci:

    1. Čeká na volání `WhenAny` k identifikaci první úkol v kolekci k dokončení jeho stažení.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Odebere tento úkol z kolekce.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`. Proměnná `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> `TReturn` kde je celé číslo. Úloha je již dokončena, ale čekáte na to, abyste načetli délku staženého webu, jak ukazuje následující příklad. Pokud je chyba `await` úlohy, vyvolá první podřízenou výjimku uloženou `AggregateException`v , na rozdíl od čtení `Result` vlastnosti, která by vyvolána `AggregateException`.

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

Spusťte program několikrát a ověřte, zda se stažené délky nevždy zobrazují ve stejném pořadí.

> [!CAUTION]
> Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které zahrnují malý počet úkolů. Jiné přístupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování. Další informace a příklady naleznete v [tématu Zpracování úloh při jejich dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text *MainWindow.xaml.cs* souboru pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad. Vezměte také na vědomí, že <xref:System.Net.Http>je nutné přidat odkaz na .

Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Jemné doladění asynchronní aplikace (C#)](fine-tuning-your-async-application.md)
- [Asynchronní programování s asynchronní a await (C#)](index.md)
- [Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
