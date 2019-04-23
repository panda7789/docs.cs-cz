---
title: 'Postupy: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 9710e5f31b9d01c5151b548c1b642293122d44b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297951"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Postupy: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)
Můžete zvýšit výkon asynchronního řešení v [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Tato metoda asynchronně čeká na více asynchronních operací, které jsou reprezentovány ve formě kolekci úkolů.  
  
 Možná jste si všimli v návodu, že se weby stahují různými rychlostmi. Někdy jedna z webových stránek je velmi pomalé, což způsobuje zpoždění všech zbývajících stahování. Když spustíte asynchronní řešení, které vytvoříte v tomto návodu, můžete můžete ukončit program snadno, pokud nechcete čekat, ale vhodnější by bylo začít všechna stahování současně a nechat pokračovat bez čekání na je rychlejší stahování.  zpožděné.  
  
 Můžete použít `Task.WhenAll` metody na kolekci úloh. Použití `WhenAll` vrátí jeden úkol, který není kompletní až do dokončení všech úloh v kolekci. Úkoly se zobrazují při paralelním spuštění, ale žádná další vlákna nejsou vytvořena. Úkoly lze provést v libovolném pořadí.  
  
> [!IMPORTANT]
>  Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Můžete vyvíjet aplikace dokončením návodu nebo stažením kódu z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější nainstalován v počítači.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Přidání metody Task.WhenAll do řešení GetURLContentsAsync  
  
1. Přidat `ProcessURLAsync` metoda k první aplikaci, která je napsán v jazyce [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a přidejte `ProcessURLAsync` soubor MainWindow.xaml.cs.  
  
    -   Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` aplikace, která zahrnuje `GetURLContentsAsync` metody. Soubor MainWindow.xaml.cs pro tuto aplikaci je první příklad v části "Kompletní kód příkladů z návodu".  
  
     `ProcessURLAsync` Spojuje akce v těle metody `foreach` smyčky v `SumPageSizesAsync` v původním návodu. Metody asynchronně stáhnou obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. Okomentujte nebo odstraňte `foreach` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3. Vytvořte kolekci úkolů. Následující kód definuje [dotazu](../../../../csharp/programming-guide/concepts/linq/index.md) , při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly jsou spuštěny, když je vyhodnocen dotaz.  
  
     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Použít `Task.WhenAll` na kolekci úloh, `downloadTasks`. `Task.WhenAll` Vrátí jeden úkol, který je dokončen po dokončení všech úloh v kolekci úloh.  
  
     V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, které `WhenAll` vrátí. Výraz vyhodnocen jako pole celých čísel, kde každé celé číslo je délka stahování webu. Přidejte následující kód, který `SumPageSizesAsync`, za kód, který jste přidali v předchozím kroku.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webových stránek. Přidejte následující řádek, který `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync  
  
1. Přidejte následující verzi `ProcessURLAsync` do druhé aplikace, který byl vyvinut v [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a přidejte `ProcessURLAsync` soubor MainWindow.xaml.cs.  
  
    -   Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` aplikace, která se používá `HttpClient.GetByteArrayAsync` metody. Soubor MainWindow.xaml.cs pro tuto aplikaci je druhý příklad v části "Kompletní kód příkladů z návodu".  
  
     `ProcessURLAsync` Spojuje akce v těle metody `foreach` smyčky v `SumPageSizesAsync` v původním návodu. Metody asynchronně stáhnou obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.  
  
     Jediný rozdíl oproti `ProcessURLAsync` metoda v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. Okomentujte nebo odstraňte `For Each` nebo `foreach` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3. Definování [dotazu](../../../../csharp/programming-guide/concepts/linq/index.md) , při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly jsou spuštěny, když je vyhodnocen dotaz.  
  
     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Dále použijte `Task.WhenAll` na kolekci úloh, `downloadTasks`. `Task.WhenAll` Vrátí jeden úkol, který je dokončen po dokončení všech úloh v kolekci úloh.  
  
     V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, které `WhenAll` vrátí. Jakmile budete hotovi, `await` výraz vyhodnocen jako pole celých čísel, kde každé celé číslo je délka stahování webu. Přidejte následující kód, který `SumPageSizesAsync`, za kód, který jste přidali v předchozím kroku.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu k získání součtu délek všech webových stránek. Přidejte následující řádek, který `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Otestování řešení Task.WhenAll  
  
-   Pro kteréhokoli řešení, zvolte klávesu F5 ke spuštění programu a klikněte na tlačítko **Start** tlačítko. Výstup by měl vypadat jako výstup asynchronních řešení v [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Všimněte si však, že jsou weby zobrazeny v jiném pořadí pokaždé, když.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje rozšíření pro projekt, který se používá `GetURLContentsAsync` metoda stahovat obsah z webu.  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` stahovat obsah z webu.  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
