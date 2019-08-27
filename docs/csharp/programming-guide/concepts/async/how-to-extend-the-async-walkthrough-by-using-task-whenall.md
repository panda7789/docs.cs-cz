---
title: 'Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: f44595a409113e4b7ff3ad2c6d0712e5debaad08
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040653"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).

Můžete zvýšit výkon asynchronního řešení v [tomto návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md) await (C#) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> pomocí metody. Tato metoda asynchronně očekává více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.

Možná jste si všimli v návodu, že se weby stahují různými sazbami. Někdy je jeden z webů velmi pomalý, což zpozdí všechna zbývající stahování. Při spuštění asynchronních řešení, která sestavíte v tomto návodu, můžete program ukončit, pokud nechcete čekat, ale lepší možností je zahájit všechna stahování ve stejnou dobu a umožnit rychlejší stahování i nadále, aniž byste čekali na to, který z nich je  platba.

`Task.WhenAll` Metodu použijete pro kolekci úkolů. Aplikace `WhenAll` vrátí jednu úlohu, která není dokončena, dokud není dokončen každý úkol v kolekci. Úkoly se zdají běžet paralelně, ale nevytvoří se žádné další podprocesy. Úkoly mohou být dokončeny v libovolném pořadí.

> [!IMPORTANT]
> Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#). Můžete vyvíjet aplikace buď dokončením návodu, nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Přidání metody Task.WhenAll do řešení GetURLContentsAsync

1. Přidejte metodu do první aplikace, která je vyvíjena v [návodu: `ProcessURLAsync` Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).

    - Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a pak přidejte `ProcessURLAsync` do souboru MainWindow.XAML.cs.

    - Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která `GetURLContentsAsync` obsahuje metodu. Soubor MainWindow.xaml.cs pro tuto aplikaci je prvním příkladem v části kompletní příklady kódu z návodu.

    Metoda slučuje akce v těle `foreach` smyčky v `SumPageSizesAsync` původním návodu. `ProcessURLAsync` Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Odkomentujte nebo odstraňte `foreach` smyčku `SumPageSizesAsync`v, jak ukazuje následující kód.

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

3. Vytvořte kolekci úkolů. Následující kód definuje [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly se spustí, když se dotaz vyhodnotí.

    Přidejte následující kód do metody `SumPageSizesAsync` po `urlList`deklaraci.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Platí `Task.WhenAll` pro kolekci úloh, `downloadTasks`. `Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.

    V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí. Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu. Přidejte následující kód do `SumPageSizesAsync`, hned po kódu, který jste přidali v předchozím kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webů. Přidejte následující řádek do `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync

1. Přidejte následující verzi `ProcessURLAsync` do druhé aplikace, která je vyvíjena v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).

    - Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a pak přidejte `ProcessURLAsync` do souboru MainWindow.XAML.cs.

    - Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která `HttpClient.GetByteArrayAsync` používá metodu. Soubor MainWindow.xaml.cs pro tuto aplikaci je druhým příkladem v části kompletní příklady kódu z návodu.

    Metoda slučuje akce v těle `foreach` smyčky v `SumPageSizesAsync` původním návodu. `ProcessURLAsync` Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.

    Jediným rozdílem z `ProcessURLAsync` metody v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Odkomentujte nebo odstraňte `For Each` smyčku nebo `SumPageSizesAsync` `foreach` v, jak ukazuje následující kód.

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

3. Definujte [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly se spustí, když se dotaz vyhodnotí.

    Po `SumPageSizesAsync` deklaraci`urlList`apřidejtenásledující kód do metody. `client`

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Dále platí `Task.WhenAll` pro kolekci úkolů, `downloadTasks`. `Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.

    V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí. Po dokončení `await` se výraz vyhodnotí jako pole celých čísel, kde každé celé číslo je délka staženého webu. Přidejte následující kód do `SumPageSizesAsync`, hned po kódu, který jste přidali v předchozím kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu k získání součtu délek všech webů. Přidejte následující řádek do `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Otestování řešení Task.WhenAll

- Pro jedno řešení zvolte klávesu F5 pro spuštění programu a pak klikněte na tlačítko **Start** . Výstup by měl vypadat podobně jako výstup z asynchronních řešení v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#). Všimněte si ale, že se weby v každé době zobrazují v jiném pořadí.

## <a name="example"></a>Příklad

Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu ke stažení obsahu z webu.

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

Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stažení obsahu z webu.

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
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
