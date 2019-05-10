---
title: Tok řízení v asynchronních programech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: c6afd7e166e08ea30637bd3f05026ef71d781ab6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624763"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Tok řízení v asynchronních programech (Visual Basic)
Můžete napsat a snadněji udržovat asynchronní programy pomocí `Async` a `Await` klíčová slova. Ale výsledků možná vás překvapí Pokud nevíte, jak program pracuje. Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu k zobrazení, když se ovládací prvek přesune z jedné metody na jinou a jaké informace jsou pokaždé přeneseny.  
  
> [!NOTE]
>  Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.  
  
 Obecně označujete metody, které obsahují asynchronní kód s [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. V metodě, která je označena asynchronním modifikátorem, můžete použít [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operátor k určení, kde Metoda počká na dokončení volaného asynchronního procesu. Další informace najdete v tématu [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Následující příklad používá asynchronní metody ke stahování obsahu zadaného webu jako řetězec a zobrazí délku řetězce. Tento příklad obsahuje následující dvě metody.  
  
- `startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.  
  
- `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync` používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, chcete-li stáhnout obsah.  
  
 Číslované řádky se zobrazí strategická místa v celém programu, které vám pomohou pochopit, jak program funguje a co se stane v každém bodu, který je označen jako zobrazení. Zobrazené řádky jsou označeny "Jedna"až "šest." Popisky představují pořadí, ve kterém dosáhne program tyto řádky kódu.  
  
 Následující kód ukazuje osnovu třídy program.  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
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
  
 Každé z označených míst "Jedna"až "šest" zobrazí informace o aktuálním stavu programu. Následující výstup je vytvořen.  
  
```  
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
 Kód, který se používá v tomto tématu si můžete stáhnout z webu MSDN nebo si ho můžete vytvořit sami.  
  
> [!NOTE]
>  Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
### <a name="download-the-program"></a>Stažení programu  
 Můžete stáhnout aplikaci pro toto téma z [asynchronní vzorek: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Následující postup otevře a spustí program.  
  
1. Rozbalte stažený soubor a poté spusťte Visual Studio.  
  
2. V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.  
  
3. Přejděte do složky obsahující dekomprimovaný ukázkový kód, otevřete soubor řešení (.sln) a pak zvolte klávesu F5 sestavte a spusťte projekt.  
  
### <a name="build-the-program-yourself"></a>Vytvoření programu vlastními silami  
 Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.  
  
 Spusťte projekt, proveďte následující kroky:  
  
1. Spusťte Visual Studio.  
  
2. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3. V **nainstalované šablony** podokně zvolte **jazyka Visual Basic**a klikněte na tlačítko **aplikace WPF** ze seznamu typů projektů.  
  
4. Zadejte `AsyncTracer` jako název projektu a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
5. V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.  
  
     Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.  
  
6. V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.  
  
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
  
     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.  
  
7. Přidat odkaz pro <xref:System.Net.Http>.  
  
8. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.  
  
9. V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.  
  
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
  
10. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     By se zobrazit následující výstup.  
  
    ```  
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
 První dva zobrazené řádky sledují cestu jako `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek popisuje volání z metody do metody.  
  
 ![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`, je TResult celé číslo. Pro `GetStringAsync`, TResult je řetězec. Další informace o asynchronních návratových typech metod naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Asynchronní metody vracející úlohy vrátí instance úlohy, když ovládací prvek přepne zpět do volajícího. Se řízení vrací z asynchronní metodu jeho volajícímu buď pokud `Await` se střetne s operátorem ve volané metodě, nebo po ukončení volané metody. Zobrazené řádky, které jsou označeny jako "Tři"až "šest" trasují tuto část procesu.  
  
### <a name="step-three"></a>Krok 3  
 V `AccessTheWebAsync`, asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> volána ke stažení obsahu cílové webové stránky. Ovládací prvek vrátí `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.  
  
 `client.GetStringAsync` Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`. Následující řádek v příkladu programu ukazuje volání do `client.GetStringAsync` a přiřazení.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 Úlohy si můžete představit jako za příslib od `client.GetStringAsync` nakonec vytvoří vytvoření skutečného řetězce. Do té doby Pokud `AccessTheWebAsync` má pracovní postup, která není závislá na přislíbeném řetězci z `client.GetStringAsync`, této práci pokračovat během `client.GetStringAsync` čeká. V tomto příkladu představují následující řádky výstupu, které nesou označení "Tři", příležitost k nezávislé práci.  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Následující obrázek znázorňuje tok řízení z `client.GetStringAsync` k přiřazení na `getStringTask` a od vytvoření `getStringTask` k použití operátoru Await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")  
  
 Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí. Do té doby se ovládací prvek vrátí volajícímu metody `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Obvykle můžete očekávat volání asynchronní metody okamžitě. Například následující přiřazení může nahradit předchozí kód, který vytvoří a poté očekává `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`  
>   
>  V tomto tématu je později použit operátor await pro výstupní řádky, které označí tok řízení programem.  
  
### <a name="step-four"></a>Krok 4  
 Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`. Proto když `AccessTheWebAsync` je pozastaven, vrátí úkol čísla do `startButton_Click`. Měli byste pochopit, že vrácená úloha není `getStringTask`. Vrácený úkol je nový úkol celého čísla, která představuje, co je ještě třeba provést v pozastavené metodě `AccessTheWebAsync`. Úkol je příslib z `AccessTheWebAsync` k vytvoření celého čísla po dokončení úkolu.  
  
 Následující příkaz přiřadí tuto úlohu `getLengthTask` proměnné.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Stejně jako v `AccessTheWebAsync`, `startButton_Click` může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`) dokud je na úkol čekáno. Následující řádky výstupu představují tuto práci.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 V průběhu `startButton_Click` se pozastavuje, když `getLengthTask` je očekáváno. Přiřazovací příkaz pozastaví `startButton_Click` dokud `AccessTheWebAsync` je dokončena.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Na následujícím obrázku šipky zobrazují tok řízení z výrazu await v metodě `AccessTheWebAsync` k přiřazení hodnoty ke `getLengthTask`, následované běžným zpracováním v `startButton_Click` dokud `getLengthTask` je očekáváno.  
  
 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace čtyři")  
  
### <a name="step-five"></a>Krok 5  
 Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat po příkazu await. Následující řádky výstupu představují opětovné zpracování.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Operanda příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrátí. Výraz await získá tuto hodnotu z `getLengthTask` v `startButton_Click`.  
  
 Následující obrázek znázorňuje přenos ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace pěti")  
  
 `AccessTheWebAsync` spuštění a dokončení, ovládací prvek vrátí na `startButton_Click`, který čeká na dokončení.  
  
### <a name="step-six"></a>Krok 6  
 Když `AccessTheWebAsync` oznamuje, že je dokončeno, zpracování může pokračovat po příkazu await v `startButton_Async`. Program ve skutečnosti nemá žádnou další akci nelze provést.  
  
 Následující řádky výstupu představují opětovné zpracování ve službě `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Výraz await získá z `getLengthTask` celočíselnou hodnotu, která je operandou příkazu return v `AccessTheWebAsync`. Následující příkaz přiřadí tuto hodnotu `contentLength` proměnné.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Následující obrázek znázorňuje návrat ovládacího prvku z `AccessTheWebAsync` k `startButton_Click`.  
  
 ![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Ukázka asynchronní metody: Řízení toku v asynchronních programech (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
