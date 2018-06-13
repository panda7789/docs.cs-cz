---
title: Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 29dc629abae13bb7ba3a9b0cb87300e6d1cbe2d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333720"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete současně spustit více úloh a zpracování jednotlivých jejich jste dokončit, nikoli jejich zpracování v pořadí, ve kterém se spouští.  
  
 Následující příklad používá dotaz k vytvoření kolekce úloh. Každý úkol stáhne obsah zadaného webu. V každé iteraci chvíli cykly, awaited volání `WhenAny` vrátí úlohu v kolekci úloh, které nejprve dokončí jeho stažení. Tuto úlohu je z kolekce odebrán a zpracovat. Smyčky se opakuje, dokud kolekce obsahuje žádné další úlohy.  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningCS.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **ProcessTasksAsTheyFinish** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
5.  Zvolte klávesu F5 a spusťte projekt.  
  
     Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.  
  
6.  Spusťte projekt několikrát k ověření, že staženou délky nezobrazí vždy ve stejném pořadí.  
  
 Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytváření v příkladu  
 Tento příklad přidá do kód, který je vyvinuta v [zrušení zbývajících asynchronních úloh po jedné je dokončení (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[zrušení zbývajících asynchronních úloh po jedné je úplná](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) a používá stejné uživatelské rozhraní.  
  
 K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAfterOneTask** jako **spouštěný projekt**. Přidat změny v tomto tématu `AccessTheWebAsync` metoda v tomto projektu. Změny jsou označené hvězdičky.  
  
 **CancelAfterOneTask** projekt už zahrnuje dotaz, který při spuštění vytvoří kolekci úloh. Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 V souboru MainWindow.xaml.cs projektu, proveďte následující změny `AccessTheWebAsync` metoda.  
  
-   Spusťte dotaz tak, že použití <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   Přidat chvíli smyčky, která provede následující kroky pro každý úkol v kolekci.  
  
    1.  Čeká volání `WhenAny` k identifikaci první úloha v kolekci ukončíte jeho stažení.  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  Tento úkol odstraní z kolekce.  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  Čeká `firstFinishedTask`, který se vrátí po volání `ProcessURLAsync`. `firstFinishedTask` Proměnná <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo. Úloha je již dokončena, ale můžete ji načíst délka stažené web, jak ukazuje následující příklad await.  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 Byste měli spustit projekt několikrát k ověření, že staženou délky nezobrazí vždy ve stejném pořadí.  
  
> [!CAUTION]
>  Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu k řešení problémů, které zahrnují malý počet úloh. Jiné postupy jsou však efektivnější, pokud máte velký počet úloh ke zpracování. Další informace a příklady naleznete v tématu [zpracování úloh po dokončení](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je úplný text souboru MainWindow.xaml.cs pro tento příklad. Hvězdičky označit prvky, které byly přidány v tomto příkladu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Vyladění s modifikátorem Async aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Ukázka asynchronního: Jemnou ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
