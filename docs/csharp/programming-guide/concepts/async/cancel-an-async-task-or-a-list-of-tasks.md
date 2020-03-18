---
title: Zrušení asynchronní úlohy nebo seznamu úkolů (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595718"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Zrušení asynchronní úlohy nebo seznamu úkolů (C#)

Můžete nastavit tlačítko, které můžete použít ke zrušení asynchronní aplikace, pokud nechcete čekat na dokončení. Podle příkladů v tomto tématu můžete přidat tlačítko zrušení do aplikace, která stáhne obsah jednoho webu nebo seznam webových stránek.

Příklady používají ui, které [fine-tuning vaše asynchronní aplikace (C#)](./fine-tuning-your-async-application.md) popisuje.

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="cancel-a-task"></a>Zrušení úkolu

První příklad přidruží tlačítko **Storno** k jedné úloze stahování. Pokud zvolíte tlačítko, když aplikace stahuje obsah, stahování se zruší.

### <a name="download-the-example"></a>Stáhněte si příklad

Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.

1. Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.

4. V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelATask** a pak zvolte **Nastavit jako počáteční projekt**.

5. Zvolte klávesu **F5** pro spuštění projektu (nebo stisknutím **klávesy Ctrl**+**F5** spusťte projekt bez ladění).

> [!TIP]
> Pokud nechcete projekt stáhnout, můžete zkontrolovat MainWindow.xaml.cs soubory na konci tohoto tématu.

### <a name="build-the-example"></a>Sestavení příkladu
 Následující změny přidávají tlačítko **Storno** do aplikace, která stáhne web. Pokud nechcete stáhnout nebo vytvořit příklad, můžete zkontrolovat konečný produkt v části "Kompletní příklady" na konci tohoto tématu. Hvězdičky označují změny v kódu.

 Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **StarterCode** jako **projekt spuštění** namísto **CancelATask**.

 Potom přidejte následující změny do MainWindow.xaml.cs souboru tohoto projektu.

1. Deklarovat proměnnou `CancellationTokenSource` , `cts`která je v oboru pro všechny metody, které k ní přistupují.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Přidejte následující obslužnou rutinu události pro tlačítko **Storno.** Obslužná <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> rutina `cts` události používá metodu upozornit, když uživatel požaduje zrušení.

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. Proveďte následující změny v obslužné rutině události pro tlačítko **Start** . `startButton_Click`

    - Vytvořte suktivku `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - Ve volání `AccessTheWebAsync`, který stáhne obsah zadaného webu, odešlete <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost `cts` jako argument. Vlastnost `Token` rozšíří zprávu, pokud je požadováno zrušení. Přidejte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit operaci stahování. Následující kód ukazuje změny.

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. V `AccessTheWebAsync`aplikaci <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> použijte `GetAsync` přetížení metody <xref:System.Net.Http.HttpClient> v typu ke stažení obsahu webu. Pass `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument. Token nese zprávu, pokud uživatel zvolí **tlačítko Storno.**

     Následující kód ukazuje změny `AccessTheWebAsync`v .

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. Pokud program nezrušíte, vytvoří následující výstup.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Pokud zvolíte tlačítko **Storno** před dokončením stahování obsahu programem, program vytvoří následující výstup.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Zrušení seznamu úkolů

Předchozí příklad můžete rozšířit tak, aby zrušil mnoho úkolů, a to tak, že přisuzujete stejnou `CancellationTokenSource` instanci ke každému úkolu. Pokud zvolíte tlačítko **Storno,** zrušíte všechny úkoly, které ještě nejsou dokončeny.

### <a name="download-the-example"></a>Stáhněte si příklad

Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.

1. Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.

4. V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAListOfTasks** a pak zvolte **Nastavit jako počáteční projekt**.

5. Zvolte klávesu **F5** pro spuštění projektu.

     Zvolte **klávesy Ctrl**+**F5** pro spuštění projektu bez ladění.

Pokud nechcete projekt stáhnout, můžete zkontrolovat MainWindow.xaml.cs soubory na konci tohoto tématu.

### <a name="build-the-example"></a>Sestavení příkladu

Chcete-li příklad rozšířit sami, krok za krokem postupujte podle pokynů v části Stažení příkladu, ale zvolte **CancelATask** jako **projekt spuštění**. Přidejte do tohoto projektu následující změny. Hvězdičky označují změny v programu.

1. Přidejte metodu pro vytvoření seznamu webových adres.

    ```csharp
    // ***Add a method that creates a list of web addresses.
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
    ```

2. Volání metody `AccessTheWebAsync`v .

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Přidejte následující `AccessTheWebAsync` smyčku do zpracování každé webové adresy v seznamu.

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. Vzhledem k tomu, `AccessTheWebAsync` že zobrazuje délky, metoda není nutné vrátit nic. Odeberte příkaz return a změňte návratový typ metody namísto <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Volání metody `startButton_Click` z pomocí příkazu namísto výrazu.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Pokud program nezrušíte, vytvoří následující výstup.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     Pokud zvolíte tlačítko **Storno** před dokončením stahování, výstup obsahuje délky stahování, které byly dokončeny před zrušením.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Kompletní příklady

Následující části obsahují kód pro každý z předchozích příkladů. Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .

Projekty si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Příklad - Zrušení úkolu

Následující kód je kompletní MainWindow.xaml.cs soubor pro příklad, který zruší jeden úkol.

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

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a>Příklad – Zrušení seznamu úkolů

Následující kód je kompletní soubor MainWindow.xaml.cs pro příklad, který zruší seznam úkolů.

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

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
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
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
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

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a>Viz také

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)
- [Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
