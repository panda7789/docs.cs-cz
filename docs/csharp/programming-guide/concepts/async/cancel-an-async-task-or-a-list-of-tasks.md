---
title: Zrušení asynchronní úlohy nebo seznamu úkolů (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595718"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Zrušení asynchronní úlohy nebo seznamu úkolů (C#)

Můžete nastavit tlačítko, které můžete použít k zrušení asynchronní aplikace, pokud nechcete čekat na jeho dokončení. Podle příkladů v tomto tématu můžete přidat tlačítko zrušení do aplikace, která stáhne obsah jednoho webu nebo seznamu webů.

V příkladech se používá uživatelské rozhraní, které popisuje [vyladění asynchronníC#aplikace ()](./fine-tuning-your-async-application.md) .

> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

## <a name="cancel-a-task"></a>Zrušení úlohy

První příklad přidruží tlačítko **Zrušit** k jedné úloze stažení. Pokud zvolíte tlačítko, zatímco aplikace stahuje obsah, stahování se zruší.

### <a name="download-the-example"></a>Stažení příkladu

Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelATask** a pak zvolte **nastavit jako projekt po spuštění**.

5. Zvolte klávesu **F5** ke spuštění projektu (nebo stiskněte klávesovou **zkratku**+**F5** pro spuštění projektu bez ladění).

> [!TIP]
> Pokud nechcete stáhnout projekt, můžete si prohlédnout soubory MainWindow.xaml.cs na konci tohoto tématu.

### <a name="build-the-example"></a>Sestavení příkladu
 Následující změny přidají tlačítko **Storno** do aplikace, která stáhne Web. Pokud nechcete stáhnout nebo sestavit příklad, můžete si prohlédnout konečný produkt v části "kompletní příklady" na konci tohoto tématu. Hvězdičky označují změny v kódu.

 Pokud chcete sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt** vyberte **StarterCode** namísto **CancelATask**.

 Pak přidejte následující změny do souboru MainWindow.xaml.cs tohoto projektu.

1. Deklarujte `CancellationTokenSource` `cts`proměnnou,, která je v oboru pro všechny metody, které k ní přistupují.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Přidejte následující obslužnou rutinu události pro tlačítko **Storno** . Obslužná rutina události používá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu k oznamování `cts` , když uživatel požaduje zrušení.

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

3. Proveďte následující změny v obslužné rutině události pro `startButton_Click`tlačítko **Start** .

    - Vytvořte instanci `cts`,. `CancellationTokenSource`

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - V volání metody `AccessTheWebAsync`, která stahuje obsah zadaného webu, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> odešlete vlastnost `cts` jako argument. Tato `Token` vlastnost šíří zprávu, pokud je požadováno zrušení. Přidejte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit operaci stahování. Následující kód ukazuje změny.

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

4. V `AccessTheWebAsync` použijte`GetAsync` přetížení metody v<xref:System.Net.Http.HttpClient> typu ke stažení obsahu webu. <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> Pass `ct`– parametr`AccessTheWebAsync`jakodruhýargument. <xref:System.Threading.CancellationToken> Pokud uživatel klikne na tlačítko **Storno** , tento token zprávu přenese.

     Následující kód ukazuje změny v `AccessTheWebAsync`.

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

5. Pokud program nerušíte, vytvoří se následující výstup.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Pokud zvolíte tlačítko **Storno** před tím, než program dokončí stahování obsahu, program vytvoří následující výstup.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Zrušení seznamu úloh

Předchozí příklad můžete roztáhnout tak, aby bylo možné zrušit mnoho úloh přiřazením `CancellationTokenSource` stejné instance ke každému úkolu. Pokud zvolíte tlačítko **Zrušit** , zrušíte tím všechny úlohy, které ještě nebyly dokončeny.

### <a name="download-the-example"></a>Stažení příkladu

Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAListOfTasks** a pak zvolte **nastavit jako projekt po spuštění**.

5. Kliknutím na klávesu **F5** spusťte projekt.

     Vyberte klávesy **CTRL**+**F5** pro spuštění projektu bez ladění.

Pokud nechcete stáhnout projekt, můžete si prohlédnout soubory MainWindow.xaml.cs na konci tohoto tématu.

### <a name="build-the-example"></a>Sestavení příkladu

Chcete-li tento příklad roztáhnout sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelATask** . Do tohoto projektu přidejte následující změny. Hvězdičky označují změny v programu.

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

2. Zavolejte metodu v `AccessTheWebAsync`.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Přidejte následující smyčku `AccessTheWebAsync` do pro zpracování každé webové adresy v seznamu.

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

4. Vzhledem `AccessTheWebAsync` k tomu, že se zobrazí délka, metoda nemusí vracet cokoli. Odeberte příkaz return a změňte návratový typ metody na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>místo.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Volejte metodu z `startButton_Click` pomocí příkazu namísto výrazu.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Pokud program nerušíte, vytvoří se následující výstup.

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

     Pokud zvolíte tlačítko **Zrušit** před dokončením stahování, bude výstup obsahovat délky stahování, která byla dokončena před zrušením.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Kompletní příklady

Následující části obsahují kód pro každý z předchozích příkladů. Všimněte si, že je nutné přidat odkaz <xref:System.Net.Http>pro.

Projekty si můžete stáhnout z [Async Sample: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)

### <a name="example---cancel-a-task"></a>Příklad – zrušení úlohy

Následující kód je úplný soubor MainWindow.xaml.cs pro příklad, který zruší jeden úkol.

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

### <a name="example---cancel-a-list-of-tasks"></a>Příklad – zrušení seznamu úloh

Následující kód je úplný soubor MainWindow.xaml.cs pro příklad, který zruší seznam úkolů.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
- [Vyladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)
- [Asynchronní Ukázka: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
