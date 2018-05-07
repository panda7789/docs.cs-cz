---
title: Multithreading s komponentou BackgroundWorker (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)
Tento návod ukazuje, jak vytvořit vícevláknové aplikace Windows Forms, která hledá textového souboru pro výskytů slova. Ukazuje:  
  
-   Definování třídy pomocí metody, která může být volána <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
-   Zpracování událostí vyvolaných <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
-   Spuštění <xref:System.ComponentModel.BackgroundWorker> součást, kterou metodu spustit.  
  
-   Implementace `Cancel` tlačítko, která ukončí <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1.  Otevřete nový projekt aplikace Windows Forms jazyka Visual Basic a vytvořit s názvem `Form1`.  
  
2.  Přidat dvě tlačítka a čtyři textová pole na `Form1`.  
  
3.  Název objekty, jak je znázorněno v následující tabulce.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |První tlačítko|`Name`, `Text`|Spuštění, spuštění|  
    |Druhý tlačítko|`Name`, `Text`|Zrušit, zrušit|  
    |První textové pole|`Name`, `Text`|Zdrojový soubor, ""|  
    |Druhý textového pole|`Name`, `Text`|CompareString, ""|  
    |Třetí textové pole|`Name`, `Text`|WordsCounted "0"|  
    |Čtvrtý textového pole|`Name`, `Text`|LinesCounted "0"|  
  
4.  Přidání štítku vedle každého textového pole. Nastavte `Text` vlastnost pro každý štítek, jak je znázorněno v následující tabulce.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |První popisek|`Text`|Zdrojový soubor|  
    |Druhý popisek|`Text`|Porovnat řetězec|  
    |Třetí popisek|`Text`|Klíčových slov|  
    |Čtvrtý popisek|`Text`|Řádky, na které se mají spočítat|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>K vytvoření BackgroundWorker – komponenta a přihlásit se k události  
  
1.  Přidat <xref:System.ComponentModel.BackgroundWorker> součásti z **součásti** části **sada nástrojů** do formuláře. Zobrazí se na panelu součást formuláře.  
  
2.  Nastavte následující vlastnosti pro objekt BackgroundWorker1.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|Hodnota TRUE|  
    |`WorkerSupportsCancellation`|Hodnota TRUE|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Chcete-li definovat metody, která se spustí na samostatné vlákna  
  
1.  Z **projektu** nabídce zvolte **přidat třídu** přidat třídu do projektu. **Přidat novou položku** se zobrazí dialogové okno.  
  
2.  Vyberte **třída** z šablony a zadejte `Words.vb` v poli název.  
  
3.  Klikněte na tlačítko **přidat**. `Words` Třídy se zobrazí.  
  
4.  Přidejte následující kód, který `Words` třídy:  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>Zpracování událostí z vlákna  
  
-   Přidejte následující obslužné rutiny událostí do svého formuláře hlavní:  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Spuštění a volání nové vlákno používající metodu WordCount  
  
1.  Přidáte do programu následujících postupů:  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  Volání `StartThread` metoda z `Start` tlačítko ve formuláři:  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>K implementaci tlačítko Zrušit, která ukončí vlákno  
  
-   Volání `StopThread` procedury `Click` obslužné rutiny události pro `Cancel` tlačítko.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>Testování  
 Nyní můžete otestovat aplikace a ujistěte se, že funguje správně.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte aplikaci.  
  
2.  Když je formulář zobrazen, zadejte cestu k souboru pro soubor, který chcete otestovat v `sourceFile` pole. Za předpokladu, že testovací soubor je s názvem Test.txt, zadejte například C:\Test.txt.  
  
3.  Do textového pole druhý zadejte slovo nebo frázi pro aplikace pro vyhledání v textovém souboru.  
  
4.  Klikněte `Start` tlačítko. `LinesCounted` Tlačítko by měl začínat zvyšování okamžitě. Aplikace zobrazí zpráva "Počítání dokončeno", pokud se provádí.  
  
#### <a name="to-test-the-cancel-button"></a>K testování na tlačítko Storno  
  
1.  Stisknutím klávesy F5 spusťte aplikaci a zadat soubor název a hledání slovo jak je popsáno v předchozím postupu. Ujistěte se, zda je soubor, který zvolíte dostatečně velký, ujistěte se, že bude mít čas zrušit postupu před dokončením.  
  
2.  Klikněte `Start` tlačítko spustit aplikaci.  
  
3.  Klikněte `Cancel` tlačítko. Aplikace by se měla zastavit počítání okamžitě.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace obsahuje některé základní chyba zpracování. Zjistí prázdné řetězce. Robustnější tento program můžete provést pomocí jiné chyby, například překračuje maximální počet slova nebo řádky, které mohou být započítány zpracování.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Návod: Vytvoření jednoduché vícevláknové komponenty v jazyce Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [Postupy: Přihlášení a odhlášení odběru událostí](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
