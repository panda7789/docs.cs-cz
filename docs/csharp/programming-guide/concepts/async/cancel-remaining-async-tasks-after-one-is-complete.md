---
title: Zrušení zbývajících asynchronních úloh po dokončení jedné zC#nich ()
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 81aed54d4854ad505971fbf85cf9a080a7c392d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922018"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Zrušení zbývajících asynchronních úloh po dokončení jedné zC#nich ()
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody společně s a <xref:System.Threading.CancellationToken>můžete zrušit všechny zbývající úlohy, když je jeden úkol dokončen. `WhenAny` Metoda přebírá argument, který je kolekcí úkolů. Metoda spustí všechny úlohy a vrátí jeden úkol. Jedna úloha je dokončena, když je dokončen libovolný úkol v kolekci.  
  
 Tento příklad ukazuje, jak použít token zrušení ve spojení s `WhenAny` pro uložení na první úkol pro dokončení z kolekce úkolů a zrušení zbývajících úkolů. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu prvního stažení, která se má dokončit, a ostatní soubory ke stažení se zruší.  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.  
  
2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.  
  
3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.  
  
4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAfterOneTask** a pak zvolte **nastavit jako projekt po spuštění**.  
  
5. Kliknutím na klávesu F5 spusťte projekt.  
  
     Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.  
  
6. Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.  
  
 Pokud nechcete stáhnout projekt, můžete si prohlédnout soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytvoření příkladu  
 Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úkolůC#()](./cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů. V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.  
  
 Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** . Přidejte změny v tomto tématu do projektu.  
  
 V souboru MainWindow.XAML.cs projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování pro každý web z smyčky `AccessTheWebAsync` do následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`je v tomto příkladu použit dotaz <xref:System.Linq.Enumerable.ToArray%2A> , metoda a `WhenAny` metoda pro vytvoření a spuštění pole úkolů. Aplikace `WhenAny` do pole vrátí jeden úkol, který je při očekávání vyhodnocen jako první úkol, aby se dosáhlo dokončení v poli úkolů.  
  
 Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označují změny v souboru kódu.  
  
1. Odkomentujte nebo odstraňte smyčku.  
  
2. Vytvoří dotaz, který při spuštění vytvoří kolekci obecných úloh. Každé volání `ProcessURLAsync` `TResult` vrátí, kde je celé číslo. <xref:System.Threading.Tasks.Task%601>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Zavolejte `ToArray` na příkaz Spustit dotaz a spusťte úkoly. Aplikace `WhenAny` metody v dalším kroku spustí dotaz a spustí úlohy bez použití `ToArray`, ale jiné metody nemusí. Nejbezpečnější praxí je vynutit provádění dotazu explicitně.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Zavolejte `WhenAny` na kolekci úkolů. `WhenAny``Task(Of Task(Of Integer))` vrátí nebo .`Task<Task<int>>`  To znamená, `WhenAny` že vrátí úlohu, která se vyhodnotí `Task(Of Integer)` na `Task<int>` jeden nebo v případě, že je očekávána. Tento jeden úkol je prvním úkolem v kolekci, který má být dokončen. Úkol, který byl dokončen jako první, `firstFinishedTask`je přiřazen. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celéčíslo,protožetojenávratovýtyp.`ProcessURLAsync`  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. V tomto příkladu vás zajímá jenom úkol, který končí jako první. Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ke zrušení zbývajících úkolů.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Nakonec čeká `firstFinishedTask` na načtení délky staženého obsahu.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je úplný soubor MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.  
  
 Všimněte si, že je nutné přidat odkaz <xref:System.Net.Http>pro.  
  
 Projekt si můžete stáhnout z [části asynchronní Ukázka: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Vyladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
- [Asynchronní Ukázka: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
