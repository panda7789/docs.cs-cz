---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: c13e592eb155d14c2e7cb2388a96925a7f1fa413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349094"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)

Asynchronní programy můžete napsat snadněji a intuitivnější pomocí funkcí Async/await. Můžete napsat asynchronní kód, který vypadá jako synchronní kód, a nechat kompilátor zpracovávat obtížné funkce zpětného volání a pokračování, které obvykle zahrnuje asynchronní kód.

Další informace o funkci Async naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Tento návod začíná s aplikací synchronní Windows Presentation Foundation (WPF), která sečte počet bajtů v seznamu webů. Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.

Pokud nechcete sestavovat aplikace sami, můžete si stáhnout "asynchronní vzorek: přístup k webovému návodu (C# a Visual Basic)" z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

V tomto návodu provedete následující úlohy:

> [!div class="checklist"]
>
> - [Vytvoření aplikace WPF](#create-a-wpf-application)
> - [Návrh jednoduchého MainWindow WPF](#design-a-simple-wpf-mainwindow)
> - [Přidat odkaz](#add-a-reference)
> - [Přidat nezbytné příkazy Imports](#add-necessary-imports-statements)
> - [Vytvoření synchronní aplikace](#create-a-synchronous-application)
> - [Test synchronního řešení](#test-the-synchronous-solution)
> - [Převést GetURLContents na asynchronní metodu](#convert-geturlcontents-to-an-asynchronous-method)
> - [Převést SumPageSizes na asynchronní metodu](#convert-sumpagesizes-to-an-asynchronous-method)
> - [Převést startButton_Click na asynchronní metodu](#convert-startbutton_click-to-an-asynchronous-method)
> - [Testování asynchronního řešení](#test-the-asynchronous-solution)
> - [Nahraďte metodu GetURLContentsAsync metodou .NET Framework.](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

Kompletní asynchronní příklad najdete v části [příklad](#example) .

## <a name="prerequisites"></a>Požadavky

V počítači musí být nainstalována aplikace Visual Studio 2012 nebo novější. Další informace najdete na stránce [soubory ke stažení](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro Visual Studio.

## <a name="create-a-wpf-application"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

    Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** zvolte možnost Visual Basic a v seznamu typů projektů zvolte možnost **aplikace WPF** .

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

2. V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.

    Zobrazí se dialogové okno **Správce odkazů** .

3. V horní části dialogového okna ověřte, zda je projekt cílen na .NET Framework 4,5 nebo vyšší.

4. V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.

5. V seznamu názvů vyberte zaškrtávací políčko **System .NET. http** .

6. Kliknutím na tlačítko **OK** zavřete dialogové okno.

## <a name="add-necessary-imports-statements"></a>Přidat nezbytné příkazy Imports

1. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.

2. Přidejte následující příkazy `Imports` v horní části souboru kódu, pokud již nejsou přítomny.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Vytvoření synchronní aplikace

1. V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko **Start** a vytvořte obslužnou rutinu události `startButton_Click` v souboru MainWindow. XAML. vb.

2. V souboru MainWindow. XAML. vb zkopírujte následující kód do textu `startButton_Click`:

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    Kód volá metodu, která aplikaci zařídí, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí do `startButton_Click`.

3. Kód pro synchronní řešení obsahuje následující čtyři metody:

    - `SumPageSizes`, který získá seznam adres URL webových stránek z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` ke zpracování každé adresy URL.

    - `SetUpURLList`, která vytvoří a vrátí seznam webových adres.

    - `GetURLContents`, který stáhne obsah jednotlivých webů a vrátí obsah jako bajtové pole.

    - `DisplayResults`, která zobrazuje počet bajtů v bajtovém poli pro každou adresu URL.

    Zkopírujte následující čtyři metody a pak je vložte pod obslužnou rutinu události `startButton_Click` v souboru MainWindow. XAML. vb:

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a>Test synchronního řešení

1. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

    Měl by se zobrazit výstup, který se podobá následujícímu seznamu:

    ```console
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

1. Chcete-li převést synchronní řešení na asynchronní řešení, je nejlepším místem, kde začít, je `GetURLContents`, protože volání metody <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> a metody <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> jsou, kde aplikace přistupuje k webu. .NET Framework usnadňuje převod tím, že poskytuje asynchronní verze obou metod.

    Další informace o metodách, které se používají v `GetURLContents`, najdete v tématu <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Při provedení kroků v tomto návodu se zobrazí několik chyb kompilátoru. Můžete je ignorovat a pokračovat v tomto návodu.

    Změňte metodu, která je volána ve třetí řádce `GetURLContents` z `GetResponse` na asynchronní metodu <xref:System.Net.WebRequest.GetResponseAsync%2A> založenou na úlohách.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě má *vrácená proměnná úlohy*`TResult`typ <xref:System.Net.WebResponse>. Úkol je příslib k vytvoření skutečného `WebResponse` objektu po stažení požadovaných dat a dokončení úlohy.

    Pro načtení `WebResponse` hodnoty z úlohy, použijte operátor [await](../../../../visual-basic/language-reference/operators/await-operator.md) pro volání `GetResponseAsync`, jak ukazuje následující kód.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    Operátor `Await` pozastaví provádění aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol. Mezitím se ovládací prvek vrátí volajícímu aktuální metody. V tomto příkladu je aktuální metoda `GetURLContents`a volající je `SumPageSizes`. Po dokončení úkolu se přislíbený `WebResponse` objekt vytvoří jako hodnota očekávaného úkolu a přiřazený k proměnné `response`.

    Předchozí příkaz může být rozdělen do následujících dvou příkazů k objasnění toho, co se stane.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Pak se pro úlohu použije operátor `Await`, aby se načetla hodnota `WebResponse`.

    Pokud vaše asynchronní metoda funguje na to, že nezávisí na dokončení úlohy, může metoda pokračovat v práci s těmito dvěma příkazy po volání asynchronní metody a před použitím operátoru await. Příklady naleznete v tématu [How to: Revícenásobné webové požadavky paralelně pomocí Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [Postupy: rozšíříte-li asynchronní návod pomocí Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Protože jste přidali operátor `Await` v předchozím kroku, dojde k chybě kompilátoru. Operátor lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) . Ignorovat chybu při opakování kroků převodu a nahradit volání `CopyTo` voláním `CopyToAsync`.

    - Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.

    - Metoda `CopyTo` nebo `CopyToAsync` kopíruje bajty do svého argumentu, `content`a nevrací smysluplnou hodnotu. V synchronní verzi je volání `CopyTo` jednoduchý příkaz, který nevrací hodnotu. Asynchronní verze, `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úkol funguje jako "Task (void)" a umožňuje, aby metoda byla očekávána. Použijte `Await` nebo `await` pro volání `CopyToAsync`, jak ukazuje následující kód.

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         Předchozí příkaz zkracuje následující dva řádky kódu.

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. Vše, co je potřeba udělat v `GetURLContents`, je upravit signaturu metody. Operátor `Await` lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) . Přidejte modifikátor k označení metody jako *asynchronní metody*, jak ukazuje následující kód.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. V Visual Basic metoda musí být `Function`, která vrací `Task` nebo `Task(Of T)`, nebo musí být metoda `Sub`. Obvykle se `Sub` metoda používá pouze v asynchronní obslužné rutině události, kde je `Sub` požadováno. V ostatních případech použijete `Task(T)`, pokud metoda Completed má [návratový](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrací hodnotu typu t, a použijete `Task`, pokud metoda Completed nevrátí smysluplnou hodnotu.

    Další informace naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

    Metoda `GetURLContents` obsahuje příkaz return a příkaz vrátí bajtové pole. Proto návratový typ asynchronní verze je Task (T), kde T je pole bajtů. V signatuře metody proveďte následující změny:

    - Změňte návratový typ na `Task(Of Byte())`.

    - Podle konvence mají asynchronní metody názvy, které končí "Async", proto přejmenujte metodu `GetURLContentsAsync`.

    Následující kód tyto změny znázorňuje.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    U těchto změn je převod `GetURLContents` na asynchronní metodu dokončen.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Převést SumPageSizes na asynchronní metodu

1. Opakujte kroky z předchozího postupu pro `SumPageSizes`. Nejprve změňte volání `GetURLContents` na asynchronní volání.

    - Změňte název metody, která je volána z `GetURLContents` na `GetURLContentsAsync`, pokud jste tak již neučinili.

    - Použijte `Await` u úkolu, který `GetURLContentsAsync` vrátí k získání hodnoty bajtového pole.

    Následující kód tyto změny znázorňuje.

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    Předchozí přiřazení zkracuje následující dva řádky kódu.

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. V signatuře metody proveďte následující změny:

    - Označte metodu pomocí modifikátoru `Async`.

    - Do názvu metody přidejte "Async".

    - V tuto chvíli neexistuje žádná vrácená proměnná úlohy, T, protože `SumPageSizesAsync` nevrací hodnotu pro T. (metoda nemá žádný příkaz `Return`.) Metoda však musí vracet `Task`, aby bylo možné očekávat. Proto změňte typ metody z `Sub` na `Function`. Návratový typ funkce je `Task`.

    Následující kód tyto změny znázorňuje.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    Převod `SumPageSizes` na `SumPageSizesAsync` je dokončený.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Převést startButton_Click na asynchronní metodu

1. V obslužné rutině události změňte název volané metody z `SumPageSizes` na `SumPageSizesAsync`, pokud jste to ještě neudělali.

2. Vzhledem k tomu, že `SumPageSizesAsync` je asynchronní metoda, změňte kód v obslužné rutině události tak, aby čekal na výsledek.

    Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`. Volání vrátí `Task`, nikoli `Task(T)`.

    Stejně jako v předchozích postupech lze volání převést pomocí jednoho příkazu nebo dvou příkazů. Následující kód tyto změny znázorňuje.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. Chcete-li zabránit nechtěnému znovu zadat operaci, přidejte do horní části `startButton_Click` následující příkaz, kterým zakážete tlačítko **Start** .

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    Tlačítko lze znovu povolit na konci obslužné rutiny události.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    Další informace o Vícenásobný přístup najdete v tématu [zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4. Nakonec přidejte modifikátor `Async` k deklaraci, aby mohla obslužná rutina události očekávat `SumPagSizesAsync`.

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    Názvy obslužných rutin událostí se typicky nemění. Návratový typ se nezměnil na `Task`, protože obslužné rutiny události musí být `Sub` procedurami v Visual Basic.

    Převod projektu z synchronního na asynchronní zpracování je dokončen.

## <a name="test-the-asynchronous-solution"></a>Testování asynchronního řešení

1. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

2. Měl by se zobrazit výstup, který se podobá výstupu synchronního řešení. Všimněte si ale následujících rozdílů.

    - Po dokončení zpracování se všechny výsledky neprojeví ve stejnou dobu. Oba programy například obsahují řádek v `startButton_Click`, který vymaže textové pole. Záměrem je vymazat textové pole mezi spuštěním, pokud zvolíte tlačítko **Spustit** pro druhý čas, poté, co se objeví jedna sada výsledků. V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, po dokončení stahování a vlákno uživatelského rozhraní je volné pro další práci. V asynchronní verzi se textové pole vymaže ihned po kliknutí na tlačítko **Start** .

    - Ve většině případů není vlákno UI během stahování zablokované. Během stahování, počítání a zobrazování webových prostředků můžete okno přesunout nebo změnit jeho velikost. Pokud je jeden z webů pomalý nebo neodpovídá, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v poli červené v pravém horním rohu).

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>Nahraďte metodu GetURLContentsAsync metodou .NET Framework.

1. .NET Framework poskytuje mnoho asynchronních metod, které můžete použít. Jedna z nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> metoda, dělá přesně to, co potřebujete pro tento návod. Místo metody `GetURLContentsAsync`, kterou jste vytvořili v předchozím postupu, ji můžete použít.

    Prvním krokem je vytvoření objektu <xref:System.Net.Http.HttpClient> v metodě `SumPageSizesAsync`. Přidejte následující deklaraci na začátek metody.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. V `SumPageSizesAsync,` nahraďte volání metody `GetURLContentsAsync` voláním metody `HttpClient`.

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Odeberte nebo Odkomentujte metodu `GetURLContentsAsync`, kterou jste napsali.

4. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

    Chování této verze projektu by se mělo shodovat s chováním, které popisuje postup testování asynchronního řešení, ale s ještě menším úsilím.

## <a name="example"></a>Příklad

Následuje úplný příklad převedeného asynchronního řešení, které používá asynchronní metodu `GetURLContentsAsync`. Všimněte si, že se silně podobá původnímu synchronnímu řešení.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

Následující kód obsahuje úplný příklad řešení, které používá metodu `HttpClient`, `GetByteArrayAsync`.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a>Viz také:

- [Asynchronní Ukázka: přístup k webovému návoduC# (a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Asynchronní programování založené na úlohách (klepnutím)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
