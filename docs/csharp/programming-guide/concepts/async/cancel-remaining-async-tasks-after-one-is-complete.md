---
title: Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 22a29dec90dcbbd24ff1a6081fd7bf1d56d6ac0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda společně s <xref:System.Threading.CancellationToken>, můžete zrušit všechny zbývající úkoly po dokončení úloh. `WhenAny` Metoda přebírá argument, který je kolekce úloh. Metoda spustí všechny úlohy a vrátí jednu úlohu. Jediná úloha je dokončena po dokončení všech úloh v kolekci.  
  
 Tento příklad ukazuje, jak používat token zrušení ve spojení s `WhenAny` k uložení do první úlohy a dokončit z kolekce úloh a zrušit ve zbývajících úkolech. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu první stahování dokončit a zruší další soubory ke stažení.  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningCS.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterOneTask** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
5.  Zvolte klávesu F5 a spusťte projekt.  
  
     Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.  
  
6.  Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.  
  
 Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytváření v příkladu  
 V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznamu úloh. Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.  
  
 K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Do tohoto projektu přidáte změny v tomto tématu.  
  
 V souboru MainWindow.xaml.cs **CancelAListOfTasks** projektu, spusťte přechodu přesunutím zpracování kroky pro každý web smyčky v `AccessTheWebAsync` následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metoda pro vytvoření a spuštění úloh v poli. Použití `WhenAny` do pole vrátí jeden úkol, pokud je očekáváno, vyhodnotí jako první úlohou k dosažení dokončování úloh v poli.  
  
 Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označit změny v souboru kódu.  
  
1.  Komentář nebo odstranit smyčky.  
  
2.  Vytvořit dotaz, která po provedení vytvoří kolekci obecné úlohy. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  Volání `ToArray` proveďte dotaz a spusťte úlohy. Použití `WhenAny` metoda v dalším kroku by provést dotaz a spustit úlohy bez použití `ToArray`, ale jiné metody možná není. Nejbezpečnější metodou je explicitně vynutit spuštění dotazu.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Volání `WhenAny` na kolekci úloh. `WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.  To znamená `WhenAny` vrátí úlohu, která vyhodnotí na jednu `Task(Of Integer)` nebo `Task<int>` Pokud je očekáváno. Tento jeden úkol je první úloha v kolekci ukončíte. Úloha, která nejprve dokončení je přiřazen k `firstFinishedTask`. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože se jedná návratový typ `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  V tomto příkladu co vás zajímá pouze úloha, která nejprve dokončí. Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušit ve zbývajících úkolech.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  Nakonec await `firstFinishedTask` načíst délka staženého obsahu.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je kompletní MainWindow.xaml.cs soubor v příkladu. Hvězdičky označit prvky, které byly přidány v tomto příkladu.  
  
 Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.  
  
 Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Vyladění s modifikátorem Async aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Ukázka asynchronního: Jemnou ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
