---
title: Zpracování asynchronních úloh po dokončení
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 335eb5dce74a7f0a2b8af550250105d460212b6a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304854"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)

S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete spustit více úkolů současně a zpracovat je postupně tak, jak jsou dokončeny namísto zpracování v pořadí, ve kterém se spouští.

Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol umožňuje stažení obsahu zadaného webu. V každé iteraci nějakou smyčky, očekávané volání metody `WhenAny` vrátí úkol v kolekci úkolů, která dokončí stahování jako první. Tento úkol je odebrán z kolekce a zpracování. Smyčka se opakuje dokud kolekce neobsahuje žádné další úlohy.

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio (2012 nebo novější) a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="download-an-example-solution"></a>Stáhnout příklad řešení

Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

> [!TIP]
> Pokud nechcete stáhnout projekt, které můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.

1. Extrahujte soubory, které jste stáhli ze souboru ZIP a poté spusťte Visual Studio.

2. V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.

3. V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste stáhli a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.

4. V **Průzkumníka řešení**, otevřete místní nabídku **ProcessTasksAsTheyFinish** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.

5. Zvolte **F5** spusťte program (nebo stiskněte klávesu **Ctrl**+**F5** klíče spustit program bez ladění).

6. Projekt několikrát spusťte a tak ověřte, že stažené délky se vždy nezobrazí ve stejném pořadí.

## <a name="create-the-program-yourself"></a>Vytvoření programu

V tomto příkladu přidá do kódu, který je napsán v jazyce [zrušení zbývajících asynchronních úloh po jeden je úplná (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md), a používá stejné uživatelské rozhraní.

Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v [stažení příkladu](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) části, ale nastavit **CancelAfterOneTask** jako spouštěný projekt. Přidejte změny v tomto tématu a `AccessTheWebAsync` metody v daném projektu. Změny jsou označeny hvězdičkami.

**CancelAfterOneTask** projekt již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

V souboru MainWindow.xaml.cs projektu proveďte následující změny `AccessTheWebAsync` metody.

-   Spusťte dotaz s použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   Přidat `while` smyčku, která provede následující kroky pro každý úkol v kolekci:

    1.  Čeká volání `WhenAny` identifikovat první úkol v kolekci, která se dokončí stažení.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  Odebere tento úkol z kolekce.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`. `firstFinishedTask` Proměnná je <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo. Úloha je již dokončena, ale můžete od něj načte délku staženého webu, jak ukazuje následující příklad očekávat.

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

Spusťte program několikrát k ověření, že stažené délky se vždy nezobrazí ve stejném pořadí.

> [!CAUTION]
> Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které se týkají malého počtu úkolů. Další postupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování. Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Kompletní příklad

Následující kód je celý text souboru MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu. Také poznamenejte si, který je nutné přidat odkaz pro <xref:System.Net.Http>.

Stáhnete projekt z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Doladění aplikace s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Ukázka asynchronní metody: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)