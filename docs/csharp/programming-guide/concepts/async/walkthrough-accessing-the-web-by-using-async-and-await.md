---
title: 'Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281782"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)

Asynchronní programy můžete napsat snadněji a intuitivnější pomocí funkcí Async/await. Můžete napsat asynchronní kód, který vypadá jako synchronní kód, a nechat kompilátor zpracovávat obtížné funkce zpětného volání a pokračování, které obvykle zahrnuje asynchronní kód.

Další informace o funkci Async naleznete v tématu [asynchronní programování s Async a awaitC#()](./index.md).

Tento návod začíná s aplikací synchronní Windows Presentation Foundation (WPF), která sečte počet bajtů v seznamu webů. Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.

Pokud nechcete sestavovat aplikace sami, můžete si stáhnout [asynchronní vzorek: přístup k webovému návodu (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

## <a name="create-a-wpf-application"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** zvolte možnost Visual C#a v seznamu typů projektů zvolte možnost **aplikace WPF** .

4. Do textového pole **název** zadejte `AsyncExampleWPF`a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

## <a name="design-a-simple-wpf-mainwindow"></a>Návrh jednoduchého MainWindow WPF

1. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

2. Pokud není okno **panelu nástrojů** viditelné, otevřete nabídku **zobrazení** a zvolte možnost **Sada nástrojů**.

3. Přidejte ovládací prvek **tlačítko** a ovládací prvek **TextBox** do okna **MainWindow** .

4. Zvýrazněte ovládací prvek **TextBox** a v okně **vlastnosti** nastavte následující hodnoty:

    - Nastavte vlastnost **název** na `resultsTextBox`.

    - Nastavte vlastnost **Height** na 250.

    - Nastavte vlastnost **Width** na 500.

    - Na kartě **text** zadejte Neproporcionální písmo, například Lucida konzolu nebo globální neproporcionální.

5. Zvýrazněte ovládací prvek **tlačítko** a v okně **vlastnosti** nastavte následující hodnoty:

    - Nastavte vlastnost **název** na `startButton`.

    - Změňte hodnotu vlastnosti **obsah** z **tlačítka** na **Spustit**.

6. Umístěte textové pole a tlačítko tak, aby se obě zobrazily v okně **MainWindow** .

     Další informace o Návrhář XAML WPF naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Přidat odkaz

1. V **Průzkumník řešení**zvýrazněte název svého projektu.

2. Na panelu nabídek vyberte možnost **projekt** > **Přidat odkaz**.

     Zobrazí se dialogové okno **Správce odkazů** .

3. V horní části dialogového okna ověřte, zda je projekt cílen na .NET Framework 4,5 nebo vyšší.

4. V kategorii **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.

5. V seznamu názvů vyberte zaškrtávací políčko **System .NET. http** .

6. Kliknutím na tlačítko **OK** zavřete dialogové okno.

## <a name="add-necessary-using-directives"></a>Přidat nezbytné direktivy using

1. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow.XAML.cs a pak zvolte **Zobrazit kód**.

2. Přidejte následující direktivy `using` v horní části souboru kódu, pokud již nejsou přítomny.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Vytvoření synchronní aplikace

1. V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko **Start** a vytvořte obslužnou rutinu události `startButton_Click` v MainWindow.XAML.cs.

2. V MainWindow.xaml.cs zkopírujte následující kód do textu `startButton_Click`:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kód volá metodu, která aplikaci zařídí, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí do `startButton_Click`.

3. Kód pro synchronní řešení obsahuje následující čtyři metody:

    - `SumPageSizes`, který získá seznam adres URL webových stránek z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` ke zpracování každé adresy URL.

    - `SetUpURLList`, která vytvoří a vrátí seznam webových adres.

    - `GetURLContents`, který stáhne obsah jednotlivých webů a vrátí obsah jako bajtové pole.

    - `DisplayResults`, která zobrazuje počet bajtů v bajtovém poli pro každou adresu URL.

    Zkopírujte následující čtyři metody a pak je vložte pod obslužnou rutinu události `startButton_Click` v MainWindow.xaml.cs:

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

## <a name="test-the-synchronous-solution"></a>Test synchronního řešení

Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .

Měl by se zobrazit výstup, který se podobá následujícímu seznamu:

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

Všimněte si, že pro zobrazení počtů trvá několik sekund. Během této doby je vlákno uživatelského rozhraní blokované při čekání na stažení požadovaných prostředků. V důsledku toho nebudete moct okno zobrazení po kliknutí na tlačítko **Start** přesunout, maximalizovat, minimalizovat ani ani zavřít. Tato snaha selže, dokud se nezobrazují počty bajtů. Pokud web neodpovídá, nemusíte mít žádné informace o tom, který web selhal. Je obtížné dokonce ukončit čekání a ukončit program.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Převést GetURLContents na asynchronní metodu

1. Chcete-li převést synchronní řešení na asynchronní řešení, je nejlepší místo spuštění v `GetURLContents`, protože volání metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> a do metody <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webu. .NET Framework usnadňuje převod tím, že poskytuje asynchronní verze obou metod.

     Další informace o metodách, které se používají v `GetURLContents`, najdete v tématu <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Při provedení kroků v tomto návodu se zobrazí několik chyb kompilátoru. Můžete je ignorovat a pokračovat v tomto návodu.

     Změňte metodu, která je volána ve třetí řádce `GetURLContents` z `GetResponse` na asynchronní metodu <xref:System.Net.WebRequest.GetResponseAsync%2A> založenou na úlohách.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync` vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě má *vrácená proměnná úlohy*`TResult`typ <xref:System.Net.WebResponse>. Úkol je příslib k vytvoření skutečného `WebResponse` objektu po stažení požadovaných dat a dokončení úlohy.

     Pro načtení `WebResponse` hodnoty z úlohy, použijte operátor [await](../../../language-reference/operators/await.md) pro volání `GetResponseAsync`, jak ukazuje následující kód.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     Operátor `await` pozastaví provádění aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol. Mezitím se ovládací prvek vrátí volajícímu aktuální metody. V tomto příkladu je aktuální metoda `GetURLContents`a volající je `SumPageSizes`. Po dokončení úkolu se přislíbený `WebResponse` objekt vytvoří jako hodnota očekávaného úkolu a přiřazený k proměnné `response`.

     Předchozí příkaz může být rozdělen do následujících dvou příkazů k objasnění toho, co se stane.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Pak se pro úlohu použije operátor await pro načtení hodnoty `WebResponse`.

     Pokud vaše asynchronní metoda funguje na to, že nezávisí na dokončení úlohy, může metoda pokračovat v práci s těmito dvěma příkazy po volání asynchronní metody a před použitím operátoru `await`. Příklady naleznete v tématu [Jak udělat více webových požadavků paralelně pomocí Async a await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [jak pomocí Task. WhenAll (C#) rozšíříte asynchronní návod](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Protože jste přidali operátor `await` v předchozím kroku, dojde k chybě kompilátoru. Operátor lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../language-reference/keywords/async.md) . Ignorovat chybu při opakování kroků převodu a nahradit volání `CopyTo` voláním `CopyToAsync`.

    - Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.

    - Metoda `CopyTo` nebo `CopyToAsync` kopíruje bajty do svého argumentu, `content`a nevrací smysluplnou hodnotu. V synchronní verzi je volání `CopyTo` jednoduchý příkaz, který nevrací hodnotu. Asynchronní verze, `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úkol funguje jako "Task (void)" a umožňuje, aby metoda byla očekávána. Použijte `Await` nebo `await` pro volání `CopyToAsync`, jak ukazuje následující kód.

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

4. Vše, co je potřeba udělat v `GetURLContents`, je upravit signaturu metody. Operátor `await` lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../language-reference/keywords/async.md) . Přidejte modifikátor k označení metody jako *asynchronní metody*, jak ukazuje následující kód.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>nebo `void` v C#. Typ vrácené `void` se obvykle používá pouze v asynchronní obslužné rutině události, kde je `void` požadováno. V ostatních případech použijete `Task(T)`, pokud metoda Completed má [návratový](../../../language-reference/keywords/return.md) příkaz, který vrací hodnotu typu t, a použijete `Task`, pokud metoda Completed nevrátí smysluplnou hodnotu. Můžete si představit `Task` návratový typ jako "Task (void)".

     Další informace naleznete v tématu [Async Return TypesC#()](./async-return-types.md).

     Metoda `GetURLContents` obsahuje příkaz return a příkaz vrátí bajtové pole. Proto návratový typ asynchronní verze je Task (T), kde T je pole bajtů. V signatuře metody proveďte následující změny:

    - Změňte návratový typ na `Task<byte[]>`.

    - Podle konvence mají asynchronní metody názvy, které končí "Async", proto přejmenujte metodu `GetURLContentsAsync`.

     Následující kód tyto změny znázorňuje.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     U těchto změn je převod `GetURLContents` na asynchronní metodu dokončen.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Převést SumPageSizes na asynchronní metodu

1. Opakujte kroky z předchozího postupu pro `SumPageSizes`. Nejprve změňte volání `GetURLContents` na asynchronní volání.

    - Změňte název metody, která je volána z `GetURLContents` na `GetURLContentsAsync`, pokud jste tak již neučinili.

    - Použijte `await` u úkolu, který `GetURLContentsAsync` vrátí k získání hodnoty bajtového pole.

     Následující kód tyto změny znázorňuje.

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

2. V signatuře metody proveďte následující změny:

    - Označte metodu pomocí modifikátoru `async`.

    - Do názvu metody přidejte "Async".

    - V tuto chvíli neexistuje žádná vrácená proměnná úlohy, T, protože `SumPageSizesAsync` nevrací hodnotu pro T. (metoda nemá žádný příkaz `return`.) Metoda však musí vracet `Task`, aby bylo možné očekávat. Proto změňte návratový typ metody z `void` na `Task`.

    Následující kód tyto změny znázorňuje.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Převod `SumPageSizes` na `SumPageSizesAsync` je dokončený.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Převést startButton_Click na asynchronní metodu

1. V obslužné rutině události změňte název volané metody z `SumPageSizes` na `SumPageSizesAsync`, pokud jste to ještě neudělali.

2. Vzhledem k tomu, že `SumPageSizesAsync` je asynchronní metoda, změňte kód v obslužné rutině události tak, aby čekal na výsledek.

     Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`. Volání vrátí `Task`, nikoli `Task(T)`.

     Stejně jako v předchozích postupech lze volání převést pomocí jednoho příkazu nebo dvou příkazů. Následující kód tyto změny znázorňuje.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. Chcete-li zabránit nechtěnému znovu zadat operaci, přidejte do horní části `startButton_Click` následující příkaz, kterým zakážete tlačítko **Start** .

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Tlačítko lze znovu povolit na konci obslužné rutiny události.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Další informace o Vícenásobný přístup najdete v tématu [zpracování Vícenásobný přístup v asynchronních aplikacíchC#()](./handling-reentrancy-in-async-apps.md).

4. Nakonec přidejte modifikátor `async` k deklaraci, aby mohla obslužná rutina události očekávat `SumPagSizesAsync`.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Názvy obslužných rutin událostí se typicky nemění. Návratový typ se nezměnil na `Task`, protože obslužné rutiny událostí musí vracet `void`.

     Převod projektu z synchronního na asynchronní zpracování je dokončen.

## <a name="test-the-asynchronous-solution"></a>Testování asynchronního řešení

1. Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .

2. Měl by se zobrazit výstup, který se podobá výstupu synchronního řešení. Všimněte si ale následujících rozdílů.

    - Po dokončení zpracování se všechny výsledky neprojeví ve stejnou dobu. Oba programy například obsahují řádek v `startButton_Click`, který vymaže textové pole. Záměrem je vymazat textové pole mezi spuštěním, pokud zvolíte tlačítko **Spustit** pro druhý čas, poté, co se objeví jedna sada výsledků. V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, po dokončení stahování a vlákno uživatelského rozhraní je volné pro další práci. V asynchronní verzi se textové pole vymaže ihned po kliknutí na tlačítko **Start** .

    - Ve většině případů není vlákno UI během stahování zablokované. Během stahování, počítání a zobrazování webových prostředků můžete okno přesunout nebo změnit jeho velikost. Pokud je jeden z webů pomalý nebo neodpovídá, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v poli červené v pravém horním rohu).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Nahraďte metodu GetURLContentsAsync metodou .NET Framework.

1. .NET Framework 4,5 poskytuje mnoho asynchronních metod, které můžete použít. Jedna z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, dělá přesně to, co potřebujete pro tento návod. Místo metody `GetURLContentsAsync`, kterou jste vytvořili v předchozím postupu, ji můžete použít.

     Prvním krokem je vytvoření objektu `HttpClient` v metodě `SumPageSizesAsync`. Přidejte následující deklaraci na začátek metody.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. V `SumPageSizesAsync,` nahraďte volání metody `GetURLContentsAsync` voláním metody `HttpClient`.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Odeberte nebo Odkomentujte metodu `GetURLContentsAsync`, kterou jste napsali.

4. Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .

     Chování této verze projektu by se mělo shodovat s chováním, které popisuje postup testování asynchronního řešení, ale s ještě menším úsilím.

## <a name="example-code"></a>Příklad kódu

Následující kód obsahuje úplný příklad převodu z synchronního na asynchronní řešení pomocí metody asynchronního `GetURLContentsAsync`, kterou jste napsali. Všimněte si, že se silně podobá původnímu synchronnímu řešení.

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

Následující kód obsahuje úplný příklad řešení, které používá metodu `HttpClient`, `GetByteArrayAsync`.

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

- [Asynchronní Ukázka: přístup k webovému návoduC# (a Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
- [Asynchronní návratové typyC#()](./async-return-types.md)
- [Asynchronní programování založené na úlohách (klepnutím)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Postup rozšiřování asynchronního návodu pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Jak zajistit paralelní více webových požadavků pomocí modifikátoru Async a operátoru awaitC#()](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
