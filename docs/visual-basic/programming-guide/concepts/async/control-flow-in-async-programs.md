---
title: Řízení toku v asynchronních programech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: a6783373f4b556694fd79401546665b09f55919d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728502"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Řízení toku v asynchronních programech (Visual Basic)
Můžete napsat a udržovat asynchronní programy snadněji pomocí `Async` a `Await` klíčová slova. Ale výsledky může ať vás překvapí Pokud nevíte, jak funguje vašeho programu. Toto téma trasování, které toku řízení prostřednictvím programu jednoduché asynchronní tak, aby zobrazovalo při řízení přechází z jedné metody na jiný a jaké informace se přenáší pokaždé, když.  
  
> [!NOTE]
>  Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.  
  
 Obecně platí, označit metody, které obsahují asynchronní kódu pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Metoda, která je označena modifikátorem async, můžete použít [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operátor na dobu, kdy metodu pro čekání na dokončení procesu volané asynchronní. Další informace najdete v tématu [asynchronní programování s Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Následující příklad používá asynchronní metody pro stažení obsahu webu, zadaný jako řetězec a zobrazíte délka řetězce. V příkladu obsahuje následující dvě metody.  
  
-   `startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.  
  
-   `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync` používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pro stažení obsahu.  
  
 Číslované zobrazení řádky se zobrazí v strategické body v rámci programu, které vám pomohou pochopit, jak program se spustí a vysvětlit, co se stane, že v každém bodu, který je označen. Zobrazení řádků, které jsou označeny "Jeden"pomocí "šest." Popisky jasné, v pořadí, ve kterém program dosáhne tyto řádky kódu.  
  
 Následující kód ukazuje přehled programu.  
  
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
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
```  
  
 Každý místa s popiskem, "Jeden"pomocí "PŮL," zobrazí informace o aktuální stav programu. Následující výsledek.  
  
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
 Kód, který používá v tomto tématu můžete stáhnout z webu MSDN nebo je možné ho vytvořit sami.  
  
> [!NOTE]
>  Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.  
  
### <a name="download-the-program"></a>Stažení programu  
 Si můžete stáhnout aplikaci pro toto téma z [asynchronní ukázka: řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Následující kroky otevřete a spusťte program.  
  
1.  Rozbalte stažený soubor a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  Přejděte do složky, která obsahuje rozbalené ukázkový kód, otevřete soubor řešení (.sln) a potom vyberte klávesy F5 sestavení a spuštění projektu.  
  
### <a name="build-the-program-yourself"></a>Vytvoření programu vlastními silami  
 Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.  
  
 Pokud chcete spustit projekt, proveďte následující kroky:  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně vyberte **jazyka Visual Basic**a potom zvolte **aplikaci WPF** ze seznamu typy projektů.  
  
4.  Zadejte `AsyncTracer` jako název projektu a klikněte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
     Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.  
  
6.  V **XAML** zobrazení MainWindow.xaml, nahraďte kód následujícím kódem.  
  
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
  
     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** zobrazení MainWindow.xaml.  
  
7.  Přidat odkaz pro <xref:System.Net.Http>.  
  
8.  V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.  
  
9. V MainWindow.xaml.vb nahraďte kód následujícím kódem.  
  
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
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
10. Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
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
 Zobrazení první dva řádky trasování cesty k `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek znázorňuje volání z metoda.  
  
 ![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Návratový typ i `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`, TResult je celé číslo. Pro `GetStringAsync`, TResult je řetězec. Další informace o asynchronní metoda návratové typy najdete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Asynchronní metody vrácení úkolů vrátí instance úlohy při řízení posune zpět k volajícímu. Vrátí ovládací prvek z asynchronní metody jeho volajícího buď když `Await` operátor se vyskytuje v volané metody nebo při ukončení zavolat metodu. Zobrazení řádků, které jsou označeny "Tři"pomocí "PŮL" trasování tuto část procesu.  
  
### <a name="step-three"></a>Krok 3  
 V `AccessTheWebAsync`, asynchronní metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> je volána pro stažení obsahu cílové webové stránky. Vrátí ovládací prvek z `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.  
  
 `client.GetStringAsync` Metoda vrátí úlohu, řetězce, který je přiřazen k `getStringTask` proměnné v `AccessTheWebAsync`. Následující řádek v programu příklad ukazuje volání `client.GetStringAsync` a přiřazení.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
```  
  
 Úlohy si můžete představit jako promise podle `client.GetStringAsync` k vytvoření nakonec konkrétní řetězec. Do té doby Pokud `AccessTheWebAsync` má práce uděláte, které nezávisí na přislíbeném řetězec z `client.GetStringAsync`, že můžete pokračovat v práci při `client.GetStringAsync` čeká. V příkladu představují následující řádky výstupu, které jsou označeny "3", tento krok provést nezávislou práci  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Následující obrázek zobrazuje tok řízení z `client.GetStringAsync` k přiřazení `getStringTask` a od vytvoření `getStringTask` do aplikace operátoru Await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")  
  
 Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí. Do té doby, vrátí ovládací prvek do volajícího `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Obvykle můžete await volání asynchronní metodu okamžitě. Například následující přiřazení může nahradit předchozí kód, který vytvoří a pak čeká `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  V tomto tématu platí operátoru await pro umístění výstupní řádky, které označit toku řízení prostřednictvím programu později.  
  
### <a name="step-four"></a>Krok 4  
 Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`. Proto když `AccessTheWebAsync` je pozastavený, vrátí úlohu celého `startButton_Click`. Byste měli vědět, že vrácený úloh není `getStringTask`. Vrácená úloha je novou úlohu celé číslo, které představuje, co je ještě provést v metodě pozastavenou `AccessTheWebAsync`. Tato úloha je promise z `AccessTheWebAsync` k vytvoření celé po dokončení úlohy.  
  
 Následující příkaz přiřadí této úlohy můžete `getLengthTask` proměnné.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Jako v `AccessTheWebAsync`, `startButton_Click` můžete pokračovat v práci, kterou nezávisí na výsledky asynchronní úlohy (`getLengthTask`) dokud úloha je očekáváno. Následující výstup řádky představují svou práci.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 V průběhu `startButton_Click` je pozastaven, když `getLengthTask` je očekáváno. Následující příkaz přiřazení pozastaví `startButton_Click` dokud `AccessTheWebAsync` dokončení.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Na následujícím obrázku, šipky zobrazují toku řízení z výrazu await v `AccessTheWebAsync` přiřazení hodnoty k `getLengthTask`, za nímž následují normálním zpracování v `startButton_Click` dokud `getLengthTask` je očekáváno.  
  
 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace ČTYŘMI")  
  
### <a name="step-five"></a>Krok 5  
 Když `client.GetStringAsync` signalizuje, že se jedná o dokončení zpracování v `AccessTheWebAsync` vydání z pozastavení a můžete pokračovat přes příkaz await. Následující řádky výstupu představují obnovení zpracování.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Operand příkaz return `urlContents.Length`, je uložen v úloze, `AccessTheWebAsync` vrátí. Výraz await načte tuto hodnotu z `getLengthTask` v `startButton_Click`.  
  
 Následující obrázek ukazuje ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace PĚT")  
  
 `AccessTheWebAsync` používá pro dokončení a řízení vrátí do `startButton_Click`, která čeká na dokončení.  
  
### <a name="step-six"></a>Krok 6  
 Když `AccessTheWebAsync` signály, které je dokončená, zpracování, můžete pokračovat přes příkaz await v `startButton_Async`. Ve skutečnosti program nijak nesouvisí Další.  
  
 Následující řádky výstupu představují obnovení zpracování v `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Výraz await načte z `getLengthTask` celočíselná hodnota, která je operand příkaz return v `AccessTheWebAsync`. Tuto hodnotu přiřadí do následujícího příkazu `contentLength` proměnné.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Následující obrázek ukazuje návratový řízení z `AccessTheWebAsync` k `startButton_Click`.  
  
 ![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace šest")  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Ukázka asynchronního: Řízení toku v asynchronních programech (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
