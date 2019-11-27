---
title: Řízení toku v asynchronních programech
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 94b2c2ea89f729e882229d4ecce7faa169c24267
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347942"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Řízení toku v asynchronních programech (Visual Basic)

K jednoduššímu psaní a údržbě asynchronních programů můžete použít klíčová slova `Async` a `Await`. Pokud ale nerozumíte tomu, jak program funguje, může se stát, že se výsledky neočekávaně neznají. Toto téma sleduje tok řízení pomocí jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesouvá z jedné metody na jinou a jaké informace se přenášejí pokaždé.

> [!NOTE]
> Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.

Obecně je třeba označit metody, které obsahují asynchronní kód, pomocí modifikátoru [Async](../../../../visual-basic/language-reference/modifiers/async.md) . V metodě, která je označena modifikátorem Async, můžete použít operátor [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) , chcete-li určit, kde metoda pozastaví čekání na dokončení volaného asynchronního procesu. Další informace naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězce a k zobrazení délky řetězce. Příklad obsahuje následující dvě metody.

- `startButton_Click`, která volá `AccessTheWebAsync` a zobrazí výsledek.

- `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync` používá asynchronní metodu <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>ke stažení obsahu.

Číslované zobrazené řádky se zobrazí ve strategických bodech v rámci programu, které vám pomůžou pochopit, jak se program spouští, a vysvětlit, co se stane v každém označeném místě. Zobrazované řádky jsou označeny "ONE" až "šest". Popisky znázorňují pořadí, ve kterém program dosáhne těchto řádků kódu.

Následující kód ukazuje osnovu programu.

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

Každé z označených umístění, "jedna" až "šest", zobrazí informace o aktuálním stavu programu. Vytvoří se následující výstup:

```console
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a>Vytvoření programu

Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si ho můžete vytvořit sami.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

### <a name="download-the-program"></a>Stažení programu

Aplikaci pro toto téma si můžete stáhnout z tématu [asynchronní vzorek: tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Následující kroky otevřete a spusťte v programu.

1. Rozbalte stažený soubor a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

3. Přejděte do složky, která obsahuje vzorový kód Get, otevřete soubor řešení (. sln) a pak zvolte klávesu F5 pro sestavení a spuštění projektu.

### <a name="build-the-program-yourself"></a>Vytvoření programu vlastními silami

Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.

Chcete-li spustit projekt, proveďte následující kroky:

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

    Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** zvolte možnost **Visual Basic**a v seznamu typů projektů zvolte možnost **aplikace WPF** .

4. Jako název projektu zadejte `AsyncTracer` a pak klikněte na tlačítko **OK** .

    Nový projekt se zobrazí v **Průzkumník řešení**.

5. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

    Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.

6. V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.

7. Přidejte odkaz na <xref:System.Net.Http>.

8. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.

9. V souboru MainWindow. XAML. vb nahraďte kód následujícím kódem.

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

    Měl by se zobrazit následující výstup:

    ```console
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a>Trasování programu

### <a name="steps-one-and-two"></a>Kroky 1 a 2

První dva zobrazené řádky sledují cestu jako `startButton_Click` volá `AccessTheWebAsync`a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek znázorňuje volání metody z metody do metody.

![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`je TResult celé číslo. Pro `GetStringAsync`je TResult řetězec. Další informace o návratových typech asynchronní metody naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

Asynchronní metoda vracející úlohu vrátí instanci úlohy, pokud se ovládací prvek posune zpět na volajícího. Řízení se vrátí z asynchronní metody volajícímu buď v případě, že se v volané metodě objevil operátor `Await`, nebo když volaná metoda skončí. V této části procesu jsou zobrazené řádky s označením "tři" až "šest".

### <a name="step-three"></a>Krok 3

V `AccessTheWebAsync`je volána asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> pro stažení obsahu cílové webové stránky. Ovládací prvek se vrátí z `client.GetStringAsync` do `AccessTheWebAsync`, když `client.GetStringAsync` vrátí.

Metoda `client.GetStringAsync` vrací úkol typu String, který je přiřazen k proměnné `getStringTask` v `AccessTheWebAsync`. Následující řádek v ukázkovém programu zobrazuje volání `client.GetStringAsync` a přiřazení.

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Úkol můžete představit jako příslib tím, že `client.GetStringAsync` vytvořit skutečný řetězec nakonec. Pokud `AccessTheWebAsync` má za následek práci, která nezávisí na přislíbeném řetězci z `client.GetStringAsync`, může tato práce pokračovat, i když `client.GetStringAsync` čeká. V příkladu představují následující řádky výstupu, které jsou označeny "tři", možnost provést nezávislou práci.

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Následující příkaz pozastaví průběh `AccessTheWebAsync`, když `getStringTask` očekává.

```vb
Dim urlContents As String = Await getStringTask
```

Následující obrázek ukazuje tok řízení od `client.GetStringAsync` k přiřazení `getStringTask` a vytváření `getStringTask` k použití operátoru await.

![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace – tři")

Výraz Await pozastaví `AccessTheWebAsync`, dokud `client.GetStringAsync` nevrátí. Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> Obvykle očekáváte okamžité volání asynchronní metody. Například následující přiřazení může nahradit předchozí kód, který vytvoří a následně očekává `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> V tomto tématu se použije operátor await později, aby se vešel na výstupní řádky, které označují tok řízení přes program.

### <a name="step-four"></a>Krok 4

Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`. Proto když je pozastavena `AccessTheWebAsync`, vrátí úlohu celé číslo do `startButton_Click`. Měli byste pochopit, že vrácená úloha není `getStringTask`. Vrácený úkol je nový úkol na celé číslo, který představuje to, co je potřeba udělat v pozastavené metodě, `AccessTheWebAsync`. Úkol je příslib od `AccessTheWebAsync` a vytvoří celé číslo po dokončení úkolu.

Následující příkaz přiřadí tuto úlohu k proměnné `getLengthTask`.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

Jak je uvedeno v `AccessTheWebAsync`, `startButton_Click` může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`), až do doby, kdy je úloha očekávána. Následující výstupní řádky označují, že fungují:

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

Průběh v `startButton_Click` je pozastavený, když se `getLengthTask` očekává. Následující příkaz přiřazení pozastaví `startButton_Click` až do dokončení `AccessTheWebAsync`.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Na následujícím obrázku šipky ukazují tok řízení z výrazu await v `AccessTheWebAsync` k přiřazení hodnoty `getLengthTask`a následováno normálním zpracováním v `startButton_Click`, dokud `getLengthTask` neočekává.

![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace – čtyři")

### <a name="step-five"></a>Krok 5

Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat za příkazem await. Následující řádky výstupu reprezentují pokračování zpracování:

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

Operand příkazu return, `urlContents.Length`, je uložen v úkolu, který `AccessTheWebAsync` vrací. Výraz Await načte tuto hodnotu z `getLengthTask` v `startButton_Click`.

Následující obrázek znázorňuje přenos řízení po dokončení `client.GetStringAsync` (a `getStringTask`).

![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace – pět")

`AccessTheWebAsync` běží na dokončení a řízení se vrátí do `startButton_Click`, což čeká na dokončení.

### <a name="step-six"></a>Krok 6

Když `AccessTheWebAsync` signalizuje, že je dokončeno, zpracování může pokračovat za příkazem await v `startButton_Async`. Ve skutečnosti program nemá nic dalšího.

Následující řádky výstupu reprezentují pokračování zpracování v `startButton_Async`:

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

Výraz Await načte z `getLengthTask` celočíselnou hodnotu, která je operandem příkazu return v `AccessTheWebAsync`. Následující příkaz přiřadí tuto hodnotu k proměnné `contentLength`.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Následující obrázek ukazuje vrácení ovládacího prvku z `AccessTheWebAsync` k `startButton_Click`.

![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace – šest")

## <a name="see-also"></a>Viz také:

- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní vzorek: tok řízení v asynchronních programechC# (a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
