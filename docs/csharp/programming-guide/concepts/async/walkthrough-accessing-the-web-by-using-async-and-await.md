---
title: 'Průvodce: Přístup k webu pomocí modifikátoru async a operátoru await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: f06bf93f1de4de2aa70c761e1bfb101d4dde48a2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127144"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Průvodce: Přístup k webu pomocí modifikátoru async a operátoru await (C#)

Asynchronní programy můžete napsat snadno a intuitivně s použitím funkce async/await. Můžete psát asynchronní kód, který vypadá jako synchronní kód a nechte kompilátor obtížné zpětného volání funkce a pokračování, které obvykle zahrnuje asynchronního kódu.

Další informace o funkci Async naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sumarizuje počet bajtů v seznamu webů. Návodu poté převádí aplikaci, aby asynchronní řešení pomocí nové funkce.

Pokud nechcete, aby k vytváření aplikací, si můžete stáhnout [asynchronní vzorek: Přístup k webovému návodu (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="create-a-wpf-application"></a>Vytvoření aplikace WPF

1.  Spusťte Visual Studio.

2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

3.  V **nainstalované šablony** podokně zvolte Visual C# a pak zvolte **aplikace WPF** ze seznamu typů projektů.

4.  V **název** textové pole, zadejte `AsyncExampleWPF`a klikněte na tlačítko **OK** tlačítko.

     Nový projekt se zobrazí v **Průzkumníka řešení**.

## <a name="design-a-simple-wpf-mainwindow"></a>Návrh jednoduchého hlavního okna MainWindow WPF

1.  V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.

2.  Pokud **nástrojů** okně není zobrazena, otevřete **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.

3.  Přidat **tlačítko** ovládacího prvku a **textového pole** ovládací prvek **hlavního okna MainWindow** okna.

4.  Zvýrazněte **TextBox** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:

    -   Nastavte **název** vlastnost `resultsTextBox`.

    -   Nastavte **výška** vlastnost na 250.

    -   Nastavte **šířka** vlastnost na hodnotu 500.

    -   Na **Text** kartu, zadejte neproporcionální písmo jako Arial konzoly nebo globální neproporcionálním písmem v.

5.  Zvýrazněte **tlačítko** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:

    -   Nastavte **název** vlastnost `startButton`.

    -   Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **Start**.

6.  Umístěte do textového pole a tlačítko tak, aby oba se objeví v **hlavního okna MainWindow** okna.

     Další informace o Návrhář WPF XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Přidat odkaz

1.  V **Průzkumníka řešení**, vyberte název vašeho projektu.

2.  V panelu nabídky zvolte **projektu** > **přidat odkaz**.

     **Správce odkazů** zobrazí se dialogové okno.

3.  V horní části dialogového okna ověřte, že váš projekt je cílen na verzi rozhraní .NET Framework 4.5 nebo vyšší.

4.  V **sestavení** kategorie, zvolte **Framework** Pokud není již vybrána.

5.  Vyberte v seznamu názvů **System.Net.Http** zaškrtávací políčko.

6.  Zvolte **OK** tlačítka zavřete dialogové okno.

## <a name="add-necessary-using-directives"></a>Přidat nezbytné direktivy using

1.  V **Průzkumníka řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **zobrazit kód**.

2.  Přidejte následující `using` direktivy v horní části souboru kódu, pokud již nejsou k dispozici.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Vytvoření synchronní aplikace

1.  V okně návrhu, MainWindow.xaml, dvakrát klikněte **Start** pro vytvoření `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs.

2.  V MainWindow.xaml.cs, zkopírujte následující kód do hlavní části `startButton_Click`:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kód volá metodu, která řídí aplikaci, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí `startButton_Click`.

3.  Kód pro synchronní řešení obsahuje následující čtyři metody:

    -   `SumPageSizes`, která načte seznam adres URL webové stránky z `SetUpURLList` a pak zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.

    -   `SetUpURLList`, který provede a vrátí seznam webové adresy.

    -   `GetURLContents`, který stáhne obsah každého webu a vrátí obsah jako bajtové pole.

    -   `DisplayResults`, který zobrazuje počet bajtů v bajtové pole pro každou adresu URL.

    Následující čtyři metody zkopírujte a vložte je za `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs:

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

## <a name="test-the-synchronous-solution"></a>Otestování synchronního řešení

Zvolte **F5** klíče ke spuštění programu a klikněte na tlačítko **Start** tlačítko.

Výstup, který vypadá podobně jako v následujícím seznamu by měl vypadat:

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

Všimněte si, že trvá několik sekund zobrazí počty. Během této doby vlákno uživatelského rozhraní je blokována během čekání požadované prostředky ke stažení. V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo dokonce zavřete okno zobrazení po zvolení **Start** tlačítko. Tyto aktivity dál rozšiřuji neúspěšné, dokud se začnou objevovat počtu bajtů. Pokud web nereaguje, je nutné žádná zpráva o které lokalitě se nezdařilo. Je obtížné i zastavte čekání a ukončení programu.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Převedení metody GetURLContents na asynchronní metodu

1.  Převést synchronní řešení na asynchronní řešení, je nejlepším místem pro spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> – metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje na web . Rozhraní .NET Framework zjednodušuje převod zadáním asynchronní verze obě metody.

     Další informace o metodách, které se používají v `GetURLContents`, naleznete v tématu <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Jak budete postupovat podle kroků v tomto názorném postupu se zobrazí několik chyby kompilátoru. Můžete je ignorovat a pokračovat v tomto návodu.

     Změnit metodu, která je volána v třetí řádek `GetURLContents` z `GetResponse` na asynchronní, založené na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  `GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě *úloh návratové*, `TResult`, má typ <xref:System.Net.WebResponse>. Úkol je příslib z k vytvoření skutečný `WebResponse` objektu po stažení požadovaných dat a je úloha spuštěná na dokončení.

     Načíst `WebResponse` hodnoty z úlohy, použijte [await](../../../../csharp/language-reference/keywords/await.md) operátor volání `GetResponseAsync`, jak ukazuje následující kód.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await` Operátor pozastaví vykonávání aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol. Mezitím se ovládací prvek vrátí volajícímu metody, aktuální. V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`. Úloha dokončení přislíbeném `WebResponse` objekt je vytvořen jako hodnota očekávané úlohy a přiřazená k proměnné `response`.

     Předchozí příkaz je možné rozdělit na následující dva příkazy o vysvětlení, co se stane.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Pak operátor await se použije na úlohu k načtení `WebResponse` hodnotu.

     Pokud asynchronní metoda má práce, která nezávisí na dokončení úlohy, metoda může pokračovat v práci mezi tyto dva příkazy po volání metody async a před `await` je použit operátor. Příklady najdete v tématu [jak: Paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [jak: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3.  Vzhledem k tomu, že jste přidali `await` dojde k chybě kompilátoru operátor v předchozím kroku. Operátor, který lze použít pouze v metodách, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor. Ignorovat chybu, zatímco nahraďte volání kroky převod `CopyTo` voláním `CopyToAsync`.

    -   Změnit název metody, která je volána k <xref:System.IO.Stream.CopyToAsync%2A>.

    -   `CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů do svého argumentu, `content`a nevrací smysluplnou hodnotu. Synchronní verze volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu. Asynchronní verze `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úloha funkce jako "Task(void)" a umožňuje metodu k ní použít operátor await. Použít `Await` nebo `await` volání `CopyToAsync`, jak ukazuje následující kód.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Předchozí příkaz zkrátí následující dva řádky kódu.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4.  Všechno, zůstane do `GetURLContents` je upravte podpis metody. Můžete použít `await` operátor pouze v metodách, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor. Přidat modifikátor k označení metody jako *asynchronní metoda*, jak ukazuje následující kód.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, nebo `void` v jazyce C#. Obvykle, návratový typ `void` se používá jenom v asynchronní obslužnou rutinu události, kde `void` je povinný. V ostatních případech použijete `Task(T)` pokud dokončené metody [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který vrátí hodnotu typu T a používáte `Task` Pokud dokončená metoda nevrací hodnotu smysluplné. Můžete si představit `Task` návratový typ jako "Task(void)."

     Další informace najdete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

     Metoda `GetURLContents` disponuje návratovým příkazem, a příkaz vrátí pole bajtů. Návratový typ asynchronní verze je proto Task(T), kde T je bajtové pole. Proveďte následující změny v podpisu metody:

    -   Změňte návratový typ na `Task<byte[]>`.

    -   Podle konvence asynchronní metody mají názvy, které končí slovem "Async", takže přejmenovat metodu `GetURLContentsAsync`.

     Následující kód znázorňuje tyto změny.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Tyto drobné změny převodu `GetURLContents` na asynchronní metodu dokončení.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Převedení metody SumPageSizes na asynchronní metodu

1.  Zopakujte kroky z předchozího postupu pro `SumPageSizes`. Nejprve změňte volání `GetURLContents` pro asynchronní volání.

    -   Změnit název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.

    -   Použít `await` úkolu, který `GetURLContentsAsync` hodnota pole vrátí získat bajt.

     Následující kód znázorňuje tyto změny.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Dřívější přiřazení zkrátí následující dva řádky kódu.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  Proveďte následující změny v podpisu metody:

    -   Označení metody `async` modifikátor.

    -   Přidáte k názvu metody "Async".

    -   Neexistuje žádná proměnná vrácené úlohy, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metoda nemá žádný `return` příkazu.) Metoda však musí vrátit `Task` bude očekávatelný. Proto změnit návratový typ metody z `void` k `Task`.

    Následující kód znázorňuje tyto změny.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Převod `SumPageSizes` k `SumPageSizesAsync` je dokončena.

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a>Převedení metody startButton_Click na asynchronní metodu

1.  V obslužné rutině události změnit název volané metody z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.

2.  Protože `SumPageSizesAsync` je metodou asynchronní kód v obslužné rutině události await pro čekání výsledek.

     Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`. Volání se vrátí `Task`, nikoli `Task(T)`.

     Stejně jako v předchozích postupů můžete převést volání pomocí jednoho příkazu nebo dvou příkazů. Následující kód znázorňuje tyto změny.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  Chcete-li zabránit náhodnému pokuste operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **Start** tlačítko.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Můžete znovu povolit tlačítko na konci obslužné rutiny události.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Další informace o vícenásobného přístupu najdete v tématu [zpracování vícenásobného přístupu v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4.  Nakonec přidejte `async` modifikátoru deklarace tak, aby obslužná rutina události může čekat `SumPagSizesAsync`.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Obvykle se nezmění názvy obslužných rutin událostí. Návratový typ není změněn na `Task` protože obslužné rutiny událostí musí vracet `void`.

     Dokončení převodu projektu z synchronní pro asynchronní zpracování.

## <a name="test-the-asynchronous-solution"></a>Otestování asynchronního řešení

1.  Zvolte **F5** klíče ke spuštění programu a klikněte na tlačítko **Start** tlačítko.

2.  By se zobrazit výstup, který se podobá výstup synchronní řešení. Všimněte si však následující rozdíly.

    -   Výsledky všech nedojde ve stejnou dobu, po dokončení zpracování. Například obě aplikace obsahovat řádek v `startButton_Click` , který vymaže do textového pole. Naším záměrem je zrušte textové pole mezi spuštění, pokud se rozhodnete **Start** tlačítko podruhé, po jednu sadu výsledků nezobrazila. Synchronní verze do textového pole není zaškrtnuto, těsně před plánovaným začátkem zobrazují počty pro při druhém volání při dokončení stahování a vlákna uživatelského rozhraní je zdarma provádět další činnosti. V asynchronní verze, do textového pole vymaže ihned poté, co vyberete **Start** tlačítko.

    -   Co je nejdůležitější vlákno uživatelského rozhraní není blokované, soubory ke stažení. Můžete přecházet nebo změně velikosti okna, zatímco v průběhu stahování webové prostředky počítá a zobrazuje. Pokud některý z webů je pomalý nebo nereaguje, můžete zrušit operaci výběrem **Zavřít** tlačítko (x červená pole v pravém horním rohu).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework

1.  Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, stačí provedla potřebné pro tento návod. Můžete použít místo něj `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.

     Prvním krokem je vytvoření `HttpClient` objektů v metodě `SumPageSizesAsync`. Na začátek metody přidejte následující deklarace.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  V `SumPageSizesAsync,` nahraďte volání vaše `GetURLContentsAsync` pomocí volání metody `HttpClient` metody.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  Odstranit nebo okomentovat `GetURLContentsAsync` metodu, která jste napsali.

4.  Zvolte **F5** klíče ke spuštění programu a klikněte na tlačítko **Start** tlačítko.

     Chování této verze projektu by měl odpovídat chování, které popisuje postup "k otestování asynchronního řešení", ale s i menším úsilím od vás.

## <a name="example-code"></a>Příklad kódu

Následující kód obsahuje úplný příklad převod ze synchronního na asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metodu, která jste napsali. Všimněte si, že důrazně vypadá podobně jako původní, která je synchronní řešení.

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

Následující kód obsahuje úplný příklad řešení, které používá `HttpClient` metody `GetByteArrayAsync`.

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

## <a name="see-also"></a>Viz také:

- [Ukázka asynchronní metody: Přístup k webovému návodu (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Asynchronní programování založené na úlohách (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)
- [Jak: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Jak: Paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
