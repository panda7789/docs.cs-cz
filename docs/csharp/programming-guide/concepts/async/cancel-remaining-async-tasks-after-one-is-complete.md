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
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody společně s <xref:System.Threading.CancellationToken>a , můžete zrušit všechny zbývající úkoly po dokončení jednoho úkolu. Metoda `WhenAny` trvá argument, který je kolekce úkolů. Metoda spustí všechny úkoly a vrátí jeden úkol. Jeden úkol je dokončen po dokončení jakékoli úlohy v kolekci.  
  
 Tento příklad ukazuje, jak použít token `WhenAny` zrušení ve spojení s podržet první úkol dokončit z kolekce úkolů a zrušit zbývající úkoly. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu prvního stažení k dokončení a zruší ostatní stahování.  
  
> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.  
  
1. Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.  
  
2. Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.  
  
3. V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.  
  
4. V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAfterOneTask** a pak zvolte **Nastavit jako počáteční projekt**.  
  
5. Zvolte klávesu F5 pro spuštění projektu.  
  
     Zvolte klávesy Ctrl+F5 pro spuštění projektu bez jeho ladění.  
  
6. Spusťte program několikrát a ověřte, zda se nejprve dokončí různé soubory ke stažení.  
  
 Pokud projekt nechcete stáhnout, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytvoření příkladu  
 Příklad v tomto tématu přidá do projektu, který je vyvinut v [Zrušit asynchronní úkol nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznam úkolů. Příklad používá stejné ui, i když **tlačítko Storno** není použit explicitně.  
  
 Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **CancelAListOfTasks** jako **projekt StartUp**Project . Přidejte změny v tomto tématu do tohoto projektu.  
  
 V souboru MainWindow.xaml.cs projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování `AccessTheWebAsync` pro každý web ze smyčky do následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`tomto příkladu používá <xref:System.Linq.Enumerable.ToArray%2A> dotaz, metodu a metodu `WhenAny` k vytvoření a spuštění pole úkolů. Aplikace `WhenAny` pole vrátí jeden úkol, který v případě čekání vyhodnotí první úkol k dosažení dokončení v poli úkolů.  
  
 Proveďte následující `AccessTheWebAsync`změny v . Hvězdičky označují změny v souboru kódu.  
  
1. Zakomentujte nebo odstraňte smyčku.  
  
2. Vytvořte dotaz, který při spuštění vytvoří kolekci obecných úloh. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> `TResult` kde je celé číslo.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Volání `ToArray` spuštění dotazu a spuštění úloh. Použití `WhenAny` metody v dalším kroku by spustit dotaz a spustit `ToArray`úkoly bez použití , ale jiné metody nemusí. Nejbezpečnější praxe je vynutit provádění dotazu explicitně.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Volání `WhenAny` na shromažďování úkolů. `WhenAny`vrátí `Task(Of Task(Of Integer))` hodnotu a nebo `Task<Task<int>>`.  To znamená `WhenAny` vrátí úkol, který vyhodnotí jeden `Task(Of Integer)` nebo `Task<int>` když je očekáván. Tento jediný úkol je první úkol v kolekci dokončit. Úkol, který byl dokončen `firstFinishedTask`jako první, je přiřazen aplikaci . Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je `ProcessURLAsync`návratový typ .  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. V tomto příkladu vás zajímá pouze úkol, který je dokončen jako první. Proto slouží <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ke zrušení zbývající úkoly.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Nakonec počkejte `firstFinishedTask` na načtení délky staženého obsahu.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Spusťte program několikrát a ověřte, zda se nejprve dokončí různé soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je kompletní MainWindow.xaml.cs soubor pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.  
  
 Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)
- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
