---
title: Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970026"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)

Můžete zlepšit výkon asynchronní řešení v [návodu: Přístup k webu pomocí asynchronní a čekat (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Tato metoda asynchronně čeká na více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.

Možná jste si v návodu všimli, že se webové stránky stahují různými rychlostmi. Někdy je jedna z webových stránek velmi pomalá, což zpožďuje všechny zbývající soubory ke stažení. Když spustíte asynchronní řešení, která vytvoříte v návodu, můžete program snadno ukončit, pokud nechcete čekat, ale lepší možností by bylo spustit všechny stahování současně a nechat rychlejší stahování pokračovat bez čekání na ten, který je Zpoždění.

Metodu `Task.WhenAll` použijete na kolekci úkolů. Aplikace `WhenAll` vrátí jeden úkol, který není dokončen, dokud není dokončena každá úloha v kolekci. Zdá se, že úlohy běží paralelně, ale jsou vytvořeny žádné další podprocesy. Úkoly lze dokončit v libovolném pořadí.

> [!IMPORTANT]
> Následující postupy popisují rozšíření asynchronních aplikací, které jsou vyvinuty v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Aplikace můžete vyvinout buď vyplněním návodu nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Chcete-li spustit příklad, musíte mít v počítači nainstalovanou visual studio 2012 nebo novější.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Přidání metody Task.WhenAll do řešení GetURLContentsAsync

1. Přidejte `ProcessURLAsync` metodu do první aplikace, která je vyvinuta v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Pokud jste stáhli kód z [ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), `ProcessURLAsync` otevřete projekt AsyncWalkthrough a přidejte do MainWindow.xaml.cs souboru.

    - Pokud jste vyvinuli kód vyplněním návodu, přidejte `ProcessURLAsync` `GetURLContentsAsync` do aplikace, která obsahuje metodu. Soubor MainWindow.xaml.cs pro tuto aplikaci je prvním příkladem v části "Kompletní příklady kódu z návodu".

    Metoda `ProcessURLAsync` konsoliduje akce v `foreach` těle `SumPageSizesAsync` smyčky v původním návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Zakomentujte `foreach` nebo `SumPageSizesAsync`odstraňte smyčku v , jak ukazuje následující kód.

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

3. Vytvořte kolekci úkolů. Následující kód definuje [dotaz,](../linq/index.md) který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stahují obsah každého webu. Úkoly jsou spuštěny při vyhodnocení dotazu.

    Přidejte následující kód `SumPageSizesAsync` metody po `urlList`deklaraci .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Platí `Task.WhenAll` pro shromažďování úkolů `downloadTasks`. `Task.WhenAll`vrátí jeden úkol, který bude dokončen po dokončení všech úkolů v kolekci úkolů.

    V následujícím příkladu `await` výraz čeká na dokončení jednoho `WhenAll` úkolu, který vrátí. Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu. Přidejte následující `SumPageSizesAsync`kód do , těsně za kód, který jste přidali v předchozím kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webových stránek. Do této části `SumPageSizesAsync`přidejte následující řádek.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync

1. Přidejte následující `ProcessURLAsync` verzi druhé aplikace, která je vyvinutá v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Pokud jste stáhli kód z [ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a přidejte `ProcessURLAsync` do souboru MainWindow.xaml.cs.

    - Pokud jste vyvinuli kód vyplněním návodu, přidejte `ProcessURLAsync` `HttpClient.GetByteArrayAsync` do aplikace, která používá metodu. Soubor MainWindow.xaml.cs pro tuto aplikaci je druhým příkladem v části "Kompletní příklady kódu z návodu".

    Metoda `ProcessURLAsync` konsoliduje akce v `foreach` těle `SumPageSizesAsync` smyčky v původním návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.

    Jediný rozdíl od `ProcessURLAsync` metody v předchozím postupu je <xref:System.Net.Http.HttpClient> použití `client`instance , .

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Zakomentujte `For Each` nebo `foreach` odstraňte smyčku nebo v `SumPageSizesAsync`, jak ukazuje následující kód.

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

3. Definujte [dotaz,](../linq/index.md) který při <xref:System.Linq.Enumerable.ToArray%2A> spuštění metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly jsou spuštěny při vyhodnocení dotazu.

    Přidejte následující kód `SumPageSizesAsync` metody po `client` `urlList`deklaraci a .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Dále platí `Task.WhenAll` pro shromažďování úkolů `downloadTasks`. `Task.WhenAll`vrátí jeden úkol, který bude dokončen po dokončení všech úkolů v kolekci úkolů.

    V následujícím příkladu `await` výraz čeká na dokončení jednoho `WhenAll` úkolu, který vrátí. Po dokončení `await` výraz vyhodnotí pole celých čísel, kde každé celé číslo je délka staženého webu. Přidejte následující `SumPageSizesAsync`kód do , těsně za kód, který jste přidali v předchozím kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu, abyste získali součet délek všech webových stránek. Do této části `SumPageSizesAsync`přidejte následující řádek.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Otestování řešení Task.WhenAll

- Pro obě řešení zvolte klávesu F5 pro spuštění programu a pak zvolte tlačítko **Start.** Výstup by se měl podobat výstupu z asynchronních řešení v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Všimněte si však, že webové stránky se pokaždé zobrazují v jiném pořadí.

## <a name="example"></a>Příklad

Následující kód ukazuje rozšíření projektu, který `GetURLContentsAsync` používá metodu ke stažení obsahu z webu.

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

Následující kód ukazuje rozšíření projektu, který `HttpClient.GetByteArrayAsync` používá metodu ke stažení obsahu z webu.

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

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
