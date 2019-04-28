---
title: Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: baf757f7f7a71528dd5dc36b0f807eb452577a38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702721"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich
S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda spolu s <xref:System.Threading.CancellationToken>, můžete po dokončení jednoho úkolu zrušit všechny zbývající úkoly. `WhenAny` Metoda přebírá argument, který je kolekce úkolů. Metoda spustí všechny úlohy a vrátí jeden úkol. Jedna úloha je dokončena po dokončení libovolné úlohy v kolekci.  
  
 Tento příklad ukazuje, jak použít token zrušení společně s `WhenAny` pro udržení prvního úkol k dokončení z kolekce úkolů a zrušení zbývajících úkolů. Každý úkol umožňuje stažení obsahu webu. Příklad zobrazuje délku obsahu prvního stahování pro dokončení a zruší ostatní stahování.  
  
> [!NOTE]
>  Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1. Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.  
  
2. V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.  
  
3. V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku **CancelAfterOneTask** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
5. Stiskněte klávesu F5 ke spuštění projektu.  
  
     Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.  
  
6. Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.  
  
 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Sestavení příkladu  
 V příkladu v tomto tématu se přidá do projektu, který je napsán v jazyce [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušení seznamu úloh. V příkladu se používá stejné uživatelské rozhraní, i když **zrušit** tlačítko není použito explicitně.  
  
 Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Přidejte změny v tomto tématu do daného projektu.  
  
 V souboru MainWindow.xaml.cs **CancelAListOfTasks** projektu, zahajte přechod přesunutím kroků zpracování pro každý web ze smyčky v `AccessTheWebAsync` do následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metodu pro vytvoření a spuštění úloh v poli. Použití `WhenAny` na pole vrátí jeden úkol, který, když je očekáváno, je vyhodnocen jako první úkol k dosažení dokončení v poli úloh.  
  
 Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označují změny v souboru kódu.  
  
1. Okomentujte nebo odstraňte smyčku.  
  
2. Vytvoření dotazu, který při spuštění vytvoří kolekci obecných úkolů. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Volání `ToArray` spustit dotaz a spustilo úlohu. Použití `WhenAny` metoda v dalším kroku by spustilo dotaz a spustilo úlohu bez použití `ToArray`, ale jiné metody nemusí. Nejbezpečnější metodou je vynutit spuštění dotazu explicitně.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Volání `WhenAny` na kolekci úloh. `WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.  To znamená `WhenAny` vrátí úkol, který se vyhodnocuje do jediné `Task(Of Integer)` nebo `Task<int>` pokus je očekáváno. Jeden úkol je první úkol v kolekci pro dokončení. Někdo přiřadí úkol, který skončil první `firstFinishedTask`. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je návratový typ `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. V tomto příkladu se zajímáte pouze úloha, která skončí jako první. Proto použít <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušení zbývajících úkolů.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Nakonec vyčkejte, než `firstFinishedTask` načte délku stahovaného obsahu.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je celý soubor MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.  
  
 Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.  
  
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
- [Doladění aplikace s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Ukázka asynchronní metody: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
