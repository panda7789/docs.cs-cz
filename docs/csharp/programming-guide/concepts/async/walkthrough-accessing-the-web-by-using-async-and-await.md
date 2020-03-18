---
title: 'Návod: Přístup k webu pomocí asynchronní a čeká (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281782"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Návod: Přístup k webu pomocí asynchronní a čeká (C#)

Asynchronní programy můžete psát snadněji a intuitivně pomocí funkcí async/await. Můžete napsat asynchronní kód, který vypadá jako synchronní kód a nechat kompilátor zpracovat obtížné funkce zpětného volání a pokračování, které obvykle znamená asynchronní kód.

Další informace o funkci Async naleznete [v tématu Asynchronní programování s asynchronní a čeká (C#)](./index.md).

Tento návod začíná synchronní windows presentation foundation (WPF) aplikace, která sečte počet bajtů v seznamu webů. Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.

Pokud nechcete vytvářet aplikace sami, můžete si stáhnout [ukázku asynchronní: Přístup k webovému návodu (C# a Visual Basic).](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="create-a-wpf-application"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

     Otevře se dialogové okno **Nový projekt.**

3. V podokně **Nainstalované šablony** zvolte Visual C# a ze seznamu typů projektů zvolte **WPF Aplikace.**

4. Do **Name** textového pole `AsyncExampleWPF`Název zadejte a pak zvolte tlačítko **OK.**

     Nový projekt se zobrazí v **Průzkumníku řešení**.

## <a name="design-a-simple-wpf-mainwindow"></a>Navrhněte jednoduchý WPF MainWindow

1. V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**

2. Pokud okno **Panel u nástrojů** není viditelné, otevřete nabídku **Zobrazení** a pak zvolte **Panel nástrojů**.

3. Přidejte **Button** button ovládací prvek a **textbox** ovládací prvek **mainwindow** okna.

4. Zvýrazněte ovládací prvek **TextBox** a v okně **Vlastnosti** nastavte následující hodnoty:

    - Nastavte **Name** vlastnost Name `resultsTextBox`na .

    - Nastavte **Height** vlastnost 250.

    - Nastavte **width** vlastnost 500.

    - Na kartě **Text** zadejte neproporcionované písmo, například Lucida Console nebo Global Monospace.

5. Zvýrazněte ovládací prvek **Button** a v okně **Vlastnosti** nastavte následující hodnoty:

    - Nastavte **Name** vlastnost Name `startButton`na .

    - Změňte hodnotu vlastnosti **Content** z **tlačítka** na **start**.

6. Umístěte textové pole a tlačítko tak, aby se obě zobrazily v okně **MainWindow.**

     Další informace o Návrháři WPF XAML naleznete [v tématu Vytvoření uživatelského uživatelského panelu pomocí návrháře XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Přidání odkazu

1. V **Průzkumníku řešení**zvýrazněte název projektu.

2. Na řádku nabídek zvolte **Project** > **Add Reference**.

     Zobrazí se dialogové okno **Správce odkazů.**

3. V horní části dialogového okna ověřte, zda projekt cílí na rozhraní .NET Framework 4.5 nebo vyšší.

4. V kategorii **Sestavení** zvolte **Framework,** pokud ještě není vybrána.

5. V seznamu názvů zaškrtněte políčko **System.Net.Http.**

6. Zvolte tlačítko **OK,** chcete-li zavřít dialogové okno.

## <a name="add-necessary-using-directives"></a>Přidat potřebné pomocí směrnic

1. V **Průzkumníku řešení**otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **Zobrazit kód**.

2. Přidejte `using` následující direktivy v horní části souboru kódu, pokud ještě nejsou k dispozici.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Vytvoření synchronní aplikace

1. V okně návrhu MainWindow.xaml poklepejte na tlačítko `startButton_Click` **Start** a vytvořte obslužnou rutinu události v MainWindow.xaml.cs.

2. V MainWindow.xaml.cs zkopírujte následující kód `startButton_Click`do těla :

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kód volá metodu, která `SumPageSizes`řídí aplikaci , a `startButton_Click`zobrazí zprávu při návratu ovládacího prvku do aplikace .

3. Kód synchronního řešení obsahuje následující čtyři metody:

    - `SumPageSizes`, který získá seznam adres URL `SetUpURLList` webových `GetURLContents` stránek `DisplayResults` z a pak volání a zpracovat každou adresu URL.

    - `SetUpURLList`, který vytvoří a vrátí seznam webových adres.

    - `GetURLContents`, který stáhne obsah jednotlivých webových stránek a vrátí obsah jako bajtové pole.

    - `DisplayResults`, který zobrazuje počet bajtů v poli bajtů pro každou adresu URL.

    Zkopírujte následující čtyři metody a vložte je pod obslužnou rutinu `startButton_Click` události v MainWindow.xaml.cs:

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
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
    ```

## <a name="test-the-synchronous-solution"></a>Testování synchronního řešení

Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**

Výstup, který se podobá následujícímu seznamu by se měl objevit:

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

Všimněte si, že trvá několik sekund k zobrazení počty. Během této doby je vlákno uživatelského rozhraní blokováno, zatímco čeká na požadované prostředky ke stažení. V důsledku toho nelze po výběru tlačítka **Start** přesunout, maximalizovat, minimalizovat nebo dokonce zavřít okno zobrazení. Tyto snahy se nezdaří, dokud se nezačnou objevovat počty bajtů. Pokud web neodpovídá, nemáte žádný údaj o tom, který web selhal. Je obtížné dokonce přestat čekat a zavřít program.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Převod obsahu GetURLNa na asynchronní metodu

1. Chcete-li převést synchronní řešení na asynchronní řešení, je `GetURLContents` nejlepší místo <xref:System.Net.HttpWebRequest> pro <xref:System.Net.HttpWebRequest.GetResponse%2A> spuštění, <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> protože volání metody a metody jsou tam, kde aplikace přistupuje k webu. Rozhraní .NET Framework usnadňuje převod poskytnutím asynchronních verzí obou metod.

     Další informace o metodách, `GetURLContents`které <xref:System.Net.WebRequest>se používají v , naleznete v tématu .

    > [!NOTE]
    > Při postupujte podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru. Můžete je ignorovat a pokračovat v návodu.

     Změňte metodu, která je volána ve třetím řádku z `GetURLContents` `GetResponse` na <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchronní metodu založenou na úlohách.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync`vrátí <xref:System.Threading.Tasks.Task%601>. V tomto případě má *proměnná vrácení úkolu*, `TResult`, typ <xref:System.Net.WebResponse>. Úloha je příslibem vytvoření `WebResponse` skutečného objektu po stažení požadovaných dat a dokončení úlohy.

     Chcete-li `WebResponse` načíst hodnotu z úkolu, použijte `GetResponseAsync`operátor [await](../../../language-reference/operators/await.md) na volání , jak ukazuje následující kód.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     Operátor `await` pozastaví provádění aktuální metody `GetURLContents`, dokud nebude očekávaná úloha dokončena. Do té doby ovládací prvek vrátí volajícímu aktuální metody. V tomto příkladu je `GetURLContents`aktuální metoda `SumPageSizes`a volající je . Po dokončení úkolu je přislíbený `WebResponse` objekt vytvořen jako hodnota očekávaného úkolu `response`a přiřazen proměnné .

     Předchozí příkaz lze rozdělit do následujících dvou příkazů objasnit, co se stane.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Potom await operátor je použita na `WebResponse` úlohu načíst hodnotu.

     Pokud vaše asynchronní metoda má práci, která nezávisí na dokončení úkolu, metoda může pokračovat v této práci mezi těmito `await` dvěma příkazy, po volání asynchronní metody a před operátor je použita. Příklady naleznete v tématu [Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Vzhledem k `await` tomu, že jste přidali operátor v předchozím kroku, dojde k chybě kompilátoru. Operátor lze použít pouze v metodách, které jsou označeny [asynchronním](../../../language-reference/keywords/async.md) modifikátorem. Při opakování kroků převodu, které mají `CopyTo` být nahrazeny `CopyToAsync`voláním, ignorujte chybu.

    - Změňte název metody, která je <xref:System.IO.Stream.CopyToAsync%2A>volána na .

    - Metoda `CopyTo` `CopyToAsync` nebo zkopíruje bajty do `content`svého argumentu a nevrátí smysluplnou hodnotu. V synchronní verzi `CopyTo` volání je jednoduchý příkaz, který nevrátí hodnotu. Asynchronní verze , `CopyToAsync`vrátí <xref:System.Threading.Tasks.Task>. Úloha funguje jako "Task(void)" a umožňuje, aby byla metoda očekávána. Použít `Await` `await` nebo na `CopyToAsync`volání , jak ukazuje následující kód.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Předchozí příkaz zkracuje následující dva řádky kódu.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. Vše, co zbývá `GetURLContents` udělat, je upravit podpis metody. `await` Operátor můžete použít pouze v metodách, které jsou označeny [asynchronním](../../../language-reference/keywords/async.md) modifikátorem. Přidejte modifikátor pro označení metody jako *asynchronní metody*, jak ukazuje následující kód.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Návratový typ asynchronní metody <xref:System.Threading.Tasks.Task>může <xref:System.Threading.Tasks.Task%601>být `void` pouze , nebo v c#. Obvykle návratový typ `void` se používá pouze v obslužné rutině asynchronní události, kde `void` je požadováno. V ostatních případech `Task(T)` se použije, pokud má dokončená metoda [příkaz return,](../../../language-reference/keywords/return.md) který vrací hodnotu typu T, a použijete, `Task` pokud dokončená metoda nevrátí smysluplnou hodnotu. Návratový `Task` typ si můžete myslet jako "Task(void)."

     Další informace naleznete [v tématu Asynchronní návratové typy (C#)](./async-return-types.md).

     Metoda `GetURLContents` má příkaz return a příkaz vrátí bajtové pole. Proto návratový typ asynchronní verze je Task(T), kde T je bajtové pole. Proveďte v podpisu metody následující změny:

    - Změňte návratový `Task<byte[]>`typ na .

    - Podle konvence asynchronní metody mají názvy, které končí v `GetURLContentsAsync`"Async", takže přejmenovat metodu .

     Následující kód ukazuje tyto změny.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     S těmito několika změnami je dokončen převod `GetURLContents` na asynchronní metodu.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Převést SumPageSizes na asynchronní metodu

1. Opakujte kroky z předchozího postupu pro `SumPageSizes`. Nejprve změňte `GetURLContents` volání na asynchronní volání.

    - Změňte název metody, která je `GetURLContents` `GetURLContentsAsync`volána z do , pokud jste tak ještě neučinili.

    - Použít `await` pro úlohu, která `GetURLContentsAsync` se vrátí k získání hodnoty bajtového pole.

     Následující kód ukazuje tyto změny.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Předchozí přiřazení zkracuje následující dva řádky kódu.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. V podpisu metody proveďte následující změny:

    - Označte metodu modifikátorem. `async`

    - Přidejte "Async" do názvu metody.

    - Neexistuje žádná proměnná vrácení úkolu, `SumPageSizesAsync` T, tentokrát, protože nevrací hodnotu `return` pro T. (Metoda nemá žádný příkaz.) Metoda však musí `Task` vrátit a být ačekatelný. Proto změňte návratový typ `void` metody `Task`z .

    Následující kód ukazuje tyto změny.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Převod `SumPageSizes` na `SumPageSizesAsync` do je dokončena.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Převést startButton_Click na asynchronní metodu

1. V obslužné rutině události `SumPageSizes` změňte název volané metody z na `SumPageSizesAsync`, pokud jste tak ještě neučinili.

2. Protože `SumPageSizesAsync` je asynchronní metoda, změňte kód v obslužné rutině události a počkejte na výsledek.

     Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`. Volání vrátí `Task`, není `Task(T)`.

     Stejně jako v předchozích postupech můžete převést volání pomocí jednoho příkazu nebo dva příkazy. Následující kód ukazuje tyto změny.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. Chcete-li zabránit náhodnému opětovnému návratu do operace, přidejte do horní části `startButton_Click` následující příkaz a zakažte tlačítko **Start.**

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Tlačítko můžete znovu povolit na konci obslužné rutiny události.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Další informace o reentrancy naleznete v [tématu Zpracování reentrancy v asynchronních aplikacích (C#)](./handling-reentrancy-in-async-apps.md).

4. Nakonec přidejte `async` modifikátor do deklarace tak, `SumPagSizesAsync`aby obslužná rutina události může čekat .

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Obvykle názvy obslužné rutiny událostí se nezmění. Návratový typ se nezmění `Task` na protože obslužné rutiny událostí musí vrátit `void`.

     Převod projektu ze synchronního na asynchronní zpracování je dokončen.

## <a name="test-the-asynchronous-solution"></a>Testování asynchronního řešení

1. Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**

2. Výstup, který se podobá výstupu synchronní řešení by se měla zobrazit. Všimněte si však následující rozdíly.

    - Výsledky nedochází všechny ve stejnou dobu, po dokončení zpracování. Oba programy například obsahují `startButton_Click` řádek, ve které textové pole vymaže. Záměrem je vymazat textové pole mezi spuštěními, pokud zvolíte tlačítko **Start** podruhé, po jedné sadě výsledků se objevil. V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, když jsou dokončeny soubory ke stažení a vlákno uživatelského rozhraní může dělat jinou práci. V asynchronní verzi se textové pole vymaže ihned po výběru tlačítka **Start.**

    - A co je nejdůležitější, vlákno uživatelského rozhraní není blokován během stahování. Okno můžete přesunout nebo změnit velikost během stahování, počítání a zobrazování webových prostředků. Pokud je jeden z webů pomalý nebo nereaguje, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v červeném poli v pravém horním rohu).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Nahradit metodu GetURLContentsAsync metodou rozhraní .NET Framework

1. Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronních metod, které můžete použít. Jeden z <xref:System.Net.Http.HttpClient> nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>metoda , dělá přesně to, co potřebujete pro tento návod. Můžete jej použít namísto metody, kterou jste vytvořili `GetURLContentsAsync` v dřívější mši.

     Prvním krokem je vytvoření `HttpClient` objektu `SumPageSizesAsync`v metodě . Na začátek metody přidejte následující deklaraci.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. V `SumPageSizesAsync,` nahradit volání `GetURLContentsAsync` metody volání metody. `HttpClient`

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Odeberte nebo `GetURLContentsAsync` okomentovat metodu, kterou jste napsali.

4. Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**

     Chování této verze projektu by měla odpovídat chování, které popisuje postup "Chcete-li otestovat asynchronní řešení", ale s ještě menší námahou od vás.

## <a name="example-code"></a>Příklad kódu

Následující kód obsahuje úplný příklad převodu ze synchronního na asynchronní řešení pomocí `GetURLContentsAsync` asynchronní metody, kterou jste napsali. Všimněte si, že se silně podobá původnímu synchronnímu řešení.

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
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

Následující kód obsahuje úplný příklad řešení, `HttpClient` které `GetByteArrayAsync`používá metodu .

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
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

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

## <a name="see-also"></a>Viz také

- [Ukázka asynchronní: Přístup k webovému návodu (C# a Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Asynchronní návratové typy (C#)](./async-return-types.md)
- [Asynchronní programování založené na úlohách (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
