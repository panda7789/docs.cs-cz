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
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)

Pomocí nástroje <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> můžete spustit více úloh současně a zpracovat je jeden po jednom, protože jsou dokončeny, a nikoli jejich zpracování v pořadí, ve kterém jsou spuštěny.

Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol stáhne obsah zadaného webu. V každé iteraci smyčky while očekává volání metody `WhenAny` vrácení úlohy v kolekci úkolů, které dokončí stahování jako první. Tato úloha je odebrána z kolekce a zpracována. Smyčka se opakuje, dokud kolekce neobsahuje žádné další úlohy.

> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio (2012 nebo novější) a .NET Framework 4,5 nebo novější.

## <a name="download-an-example-solution"></a>Stažení ukázkového řešení

Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

> [!TIP]
> Pokud nechcete stáhnout projekt, můžete místo toho zkontrolovat soubor *MainWindow.XAML.cs* na konci tohoto tématu.

1. Extrahujte soubory, které jste stáhli ze souboru *. zip* , a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte **soubor**  >  **otevřít**  >  **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste stáhli, a poté otevřete soubor řešení (*. sln*) pro *AsyncFineTuningCS* / *AsyncFineTuningVB*.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ProcessTasksAsTheyFinish** a pak zvolte **nastavit jako projekt po spuštění**.

5. Zvolte klávesu <kbd>F5</kbd> ke spuštění programu v ladění nebo stiskněte klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> a program spusťte bez ladění.

6. Spusťte projekt několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.

## <a name="create-the-program-yourself"></a>Vytvoření programu sami

Tento příklad přidá do kódu, který je vyvinut v části [zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)a používá stejné uživatelské rozhraní.

Chcete-li sestavit příklad sami, postupujte podle pokynů v části [stažení ukázkového](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) oddílu, ale nastavte **CancelAfterOneTask** jako spouštěný projekt. Přidejte změny v tomto tématu do `AccessTheWebAsync` metody v tomto projektu. Změny jsou označeny hvězdičkami.

Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání do `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

V souboru *MainWindow.XAML.cs* projektu proveďte následující změny `AccessTheWebAsync` metody:

- Spusťte dotaz použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A> .

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- Přidejte `while` smyčku, která provede následující kroky pro každý úkol v kolekci:

    1. Očekává volání `WhenAny` k identifikaci prvního úkolu v kolekci, aby bylo možné dokončit stahování.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Odebere úlohu z kolekce.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. Čeká `firstFinishedTask` , který je vrácen voláním metody `ProcessURLAsync` . `firstFinishedTask`Proměnná je <xref:System.Threading.Tasks.Task%601> , kde `TReturn` je celé číslo. Úkol je již dokončen, ale očekáváte, že bude načtena délka staženého webu, jak ukazuje následující příklad. Pokud dojde k chybě úlohy, `await` vyvolá první podřízenou výjimku uloženou v objektu `AggregateException` , na rozdíl od čtení `Result` vlastnosti, která by vyvolala `AggregateException` .

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

Spusťte program několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.

> [!CAUTION]
> Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, pro řešení problémů, které zahrnují malý počet úkolů. Další přístupy jsou ale efektivnější, pokud máte velký počet úkolů, které je potřeba zpracovat. Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text souboru *MainWindow.XAML.cs* pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad. Všimněte si také, že je nutné přidat odkaz pro <xref:System.Net.Http> .

Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
- [Vyladění aplikace s modifikátorem Async (C#)](fine-tuning-your-async-application.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)
- [Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
