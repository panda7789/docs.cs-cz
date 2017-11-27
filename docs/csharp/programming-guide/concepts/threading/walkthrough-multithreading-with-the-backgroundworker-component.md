---
title: "Návod: Multithreading s komponentou BackgroundWorker (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>Návod: Multithreading s komponentou BackgroundWorker (C#)
Tento návod ukazuje, jak vytvořit vícevláknové aplikace Windows Forms, která hledá textového souboru pro výskytů slova. Ukazuje:  
  
-   Definování třídy pomocí metody, která může být volána <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
-   Zpracování událostí vyvolaných <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
-   Spuštění <xref:System.ComponentModel.BackgroundWorker> součást, kterou metodu spustit.  
  
-   Implementace `Cancel` tlačítko, která ukončí <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1.  Otevřete nový projekt C# aplikaci Windows Forms a vytvořit s názvem `Form1`.  
  
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
  
2.  Nastavte následující vlastnosti pro objekt backgroundWorker1.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|Hodnota TRUE|  
    |`WorkerSupportsCancellation`|Hodnota TRUE|  
  
3.  Přihlásit k událostem, které backgroundWorker1 objektu. V horní části **vlastnosti** okně klikněte na tlačítko **události** ikonu. Dvakrát klikněte `RunWorkerCompleted` událost, která má vytvořte obslužnou rutinu události. Totéž proveďte pro `ProgressChanged` a `DoWork` události.  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Chcete-li definovat metody, která se spustí na samostatné vlákna  
  
1.  Z **projektu** nabídce zvolte **přidat třídu** přidat třídu do projektu. **Přidat novou položku** se zobrazí dialogové okno.  
  
2.  Vyberte **třída** z šablony a zadejte `Words.cs` v poli název.  
  
3.  Klikněte na tlačítko **přidat**. `Words` Třídy se zobrazí.  
  
4.  Přidejte následující kód, který `Words` třídy:  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>Zpracování událostí z vlákna  
  
-   Přidejte následující obslužné rutiny událostí do svého formuláře hlavní:  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Spuštění a volání nové vlákno používající metodu WordCount  
  
1.  Přidáte do programu následujících postupů:  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  Volání `StartThread` metoda z `Start` tlačítko ve formuláři:  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>K implementaci tlačítko Zrušit, která ukončí vlákno  
  
    -   Volání `StopThread` procedury `Click` obslužné rutiny události pro `Cancel` tlačítko.  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
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
 [Dělení na vlákna (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Postupy: přihlášení a odhlášení odběru událostí](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
