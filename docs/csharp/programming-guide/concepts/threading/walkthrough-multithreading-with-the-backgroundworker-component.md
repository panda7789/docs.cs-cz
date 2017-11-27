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
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="53860-102">Návod: Multithreading s komponentou BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="53860-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="53860-103">Tento návod ukazuje, jak vytvořit vícevláknové aplikace Windows Forms, která hledá textového souboru pro výskytů slova.</span><span class="sxs-lookup"><span data-stu-id="53860-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="53860-104">Ukazuje:</span><span class="sxs-lookup"><span data-stu-id="53860-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="53860-105">Definování třídy pomocí metody, která může být volána <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="53860-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="53860-106">Zpracování událostí vyvolaných <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="53860-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="53860-107">Spuštění <xref:System.ComponentModel.BackgroundWorker> součást, kterou metodu spustit.</span><span class="sxs-lookup"><span data-stu-id="53860-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="53860-108">Implementace `Cancel` tlačítko, která ukončí <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="53860-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="53860-109">Vytvoření uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="53860-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="53860-110">Otevřete nový projekt C# aplikaci Windows Forms a vytvořit s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53860-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="53860-111">Přidat dvě tlačítka a čtyři textová pole na `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53860-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="53860-112">Název objekty, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="53860-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="53860-113">Objekt</span><span class="sxs-lookup"><span data-stu-id="53860-113">Object</span></span>|<span data-ttu-id="53860-114">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="53860-114">Property</span></span>|<span data-ttu-id="53860-115">Nastavení</span><span class="sxs-lookup"><span data-stu-id="53860-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="53860-116">První tlačítko</span><span class="sxs-lookup"><span data-stu-id="53860-116">First button</span></span>|<span data-ttu-id="53860-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-117">`Name`, `Text`</span></span>|<span data-ttu-id="53860-118">Spuštění, spuštění</span><span class="sxs-lookup"><span data-stu-id="53860-118">Start, Start</span></span>|  
    |<span data-ttu-id="53860-119">Druhý tlačítko</span><span class="sxs-lookup"><span data-stu-id="53860-119">Second button</span></span>|<span data-ttu-id="53860-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-120">`Name`, `Text`</span></span>|<span data-ttu-id="53860-121">Zrušit, zrušit</span><span class="sxs-lookup"><span data-stu-id="53860-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="53860-122">První textové pole</span><span class="sxs-lookup"><span data-stu-id="53860-122">First text box</span></span>|<span data-ttu-id="53860-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-123">`Name`, `Text`</span></span>|<span data-ttu-id="53860-124">Zdrojový soubor, ""</span><span class="sxs-lookup"><span data-stu-id="53860-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="53860-125">Druhý textového pole</span><span class="sxs-lookup"><span data-stu-id="53860-125">Second text box</span></span>|<span data-ttu-id="53860-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-126">`Name`, `Text`</span></span>|<span data-ttu-id="53860-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="53860-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="53860-128">Třetí textové pole</span><span class="sxs-lookup"><span data-stu-id="53860-128">Third text box</span></span>|<span data-ttu-id="53860-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-129">`Name`, `Text`</span></span>|<span data-ttu-id="53860-130">WordsCounted "0"</span><span class="sxs-lookup"><span data-stu-id="53860-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="53860-131">Čtvrtý textového pole</span><span class="sxs-lookup"><span data-stu-id="53860-131">Fourth text box</span></span>|<span data-ttu-id="53860-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="53860-132">`Name`, `Text`</span></span>|<span data-ttu-id="53860-133">LinesCounted "0"</span><span class="sxs-lookup"><span data-stu-id="53860-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="53860-134">Přidání štítku vedle každého textového pole.</span><span class="sxs-lookup"><span data-stu-id="53860-134">Add a label next to each text box.</span></span> <span data-ttu-id="53860-135">Nastavte `Text` vlastnost pro každý štítek, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="53860-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="53860-136">Objekt</span><span class="sxs-lookup"><span data-stu-id="53860-136">Object</span></span>|<span data-ttu-id="53860-137">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="53860-137">Property</span></span>|<span data-ttu-id="53860-138">Nastavení</span><span class="sxs-lookup"><span data-stu-id="53860-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="53860-139">První popisek</span><span class="sxs-lookup"><span data-stu-id="53860-139">First label</span></span>|`Text`|<span data-ttu-id="53860-140">Zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="53860-140">Source File</span></span>|  
    |<span data-ttu-id="53860-141">Druhý popisek</span><span class="sxs-lookup"><span data-stu-id="53860-141">Second label</span></span>|`Text`|<span data-ttu-id="53860-142">Porovnat řetězec</span><span class="sxs-lookup"><span data-stu-id="53860-142">Compare String</span></span>|  
    |<span data-ttu-id="53860-143">Třetí popisek</span><span class="sxs-lookup"><span data-stu-id="53860-143">Third label</span></span>|`Text`|<span data-ttu-id="53860-144">Klíčových slov</span><span class="sxs-lookup"><span data-stu-id="53860-144">Matching Words</span></span>|  
    |<span data-ttu-id="53860-145">Čtvrtý popisek</span><span class="sxs-lookup"><span data-stu-id="53860-145">Fourth label</span></span>|`Text`|<span data-ttu-id="53860-146">Řádky, na které se mají spočítat</span><span class="sxs-lookup"><span data-stu-id="53860-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="53860-147">K vytvoření BackgroundWorker – komponenta a přihlásit se k události</span><span class="sxs-lookup"><span data-stu-id="53860-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="53860-148">Přidat <xref:System.ComponentModel.BackgroundWorker> součásti z **součásti** části **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="53860-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="53860-149">Zobrazí se na panelu součást formuláře.</span><span class="sxs-lookup"><span data-stu-id="53860-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="53860-150">Nastavte následující vlastnosti pro objekt backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="53860-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="53860-151">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="53860-151">Property</span></span>|<span data-ttu-id="53860-152">Nastavení</span><span class="sxs-lookup"><span data-stu-id="53860-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="53860-153">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="53860-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="53860-154">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="53860-154">True</span></span>|  
  
3.  <span data-ttu-id="53860-155">Přihlásit k událostem, které backgroundWorker1 objektu.</span><span class="sxs-lookup"><span data-stu-id="53860-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="53860-156">V horní části **vlastnosti** okně klikněte na tlačítko **události** ikonu.</span><span class="sxs-lookup"><span data-stu-id="53860-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="53860-157">Dvakrát klikněte `RunWorkerCompleted` událost, která má vytvořte obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="53860-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="53860-158">Totéž proveďte pro `ProgressChanged` a `DoWork` události.</span><span class="sxs-lookup"><span data-stu-id="53860-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="53860-159">Chcete-li definovat metody, která se spustí na samostatné vlákna</span><span class="sxs-lookup"><span data-stu-id="53860-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="53860-160">Z **projektu** nabídce zvolte **přidat třídu** přidat třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="53860-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="53860-161">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="53860-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="53860-162">Vyberte **třída** z šablony a zadejte `Words.cs` v poli název.</span><span class="sxs-lookup"><span data-stu-id="53860-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="53860-163">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="53860-163">Click **Add**.</span></span> <span data-ttu-id="53860-164">`Words` Třídy se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="53860-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="53860-165">Přidejte následující kód, který `Words` třídy:</span><span class="sxs-lookup"><span data-stu-id="53860-165">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="53860-166">Zpracování událostí z vlákna</span><span class="sxs-lookup"><span data-stu-id="53860-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="53860-167">Přidejte následující obslužné rutiny událostí do svého formuláře hlavní:</span><span class="sxs-lookup"><span data-stu-id="53860-167">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="53860-168">Spuštění a volání nové vlákno používající metodu WordCount</span><span class="sxs-lookup"><span data-stu-id="53860-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="53860-169">Přidáte do programu následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="53860-169">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="53860-170">Volání `StartThread` metoda z `Start` tlačítko ve formuláři:</span><span class="sxs-lookup"><span data-stu-id="53860-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="53860-171">K implementaci tlačítko Zrušit, která ukončí vlákno</span><span class="sxs-lookup"><span data-stu-id="53860-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="53860-172">Volání `StopThread` procedury `Click` obslužné rutiny události pro `Cancel` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="53860-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="53860-173">Testování</span><span class="sxs-lookup"><span data-stu-id="53860-173">Testing</span></span>  
 <span data-ttu-id="53860-174">Nyní můžete otestovat aplikace a ujistěte se, že funguje správně.</span><span class="sxs-lookup"><span data-stu-id="53860-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="53860-175">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="53860-175">To test the application</span></span>  
  
1.  <span data-ttu-id="53860-176">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53860-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="53860-177">Když je formulář zobrazen, zadejte cestu k souboru pro soubor, který chcete otestovat v `sourceFile` pole.</span><span class="sxs-lookup"><span data-stu-id="53860-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="53860-178">Za předpokladu, že testovací soubor je s názvem Test.txt, zadejte například C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="53860-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="53860-179">Do textového pole druhý zadejte slovo nebo frázi pro aplikace pro vyhledání v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="53860-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="53860-180">Klikněte `Start` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="53860-180">Click the `Start` button.</span></span> <span data-ttu-id="53860-181">`LinesCounted` Tlačítko by měl začínat zvyšování okamžitě.</span><span class="sxs-lookup"><span data-stu-id="53860-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="53860-182">Aplikace zobrazí zpráva "Počítání dokončeno", pokud se provádí.</span><span class="sxs-lookup"><span data-stu-id="53860-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="53860-183">K testování na tlačítko Storno</span><span class="sxs-lookup"><span data-stu-id="53860-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="53860-184">Stisknutím klávesy F5 spusťte aplikaci a zadat soubor název a hledání slovo jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="53860-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="53860-185">Ujistěte se, zda je soubor, který zvolíte dostatečně velký, ujistěte se, že bude mít čas zrušit postupu před dokončením.</span><span class="sxs-lookup"><span data-stu-id="53860-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="53860-186">Klikněte `Start` tlačítko spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53860-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="53860-187">Klikněte `Cancel` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="53860-187">Click the `Cancel` button.</span></span> <span data-ttu-id="53860-188">Aplikace by se měla zastavit počítání okamžitě.</span><span class="sxs-lookup"><span data-stu-id="53860-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="53860-189">Další kroky</span><span class="sxs-lookup"><span data-stu-id="53860-189">Next Steps</span></span>  
 <span data-ttu-id="53860-190">Tato aplikace obsahuje některé základní chyba zpracování.</span><span class="sxs-lookup"><span data-stu-id="53860-190">This application contains some basic error handling.</span></span> <span data-ttu-id="53860-191">Zjistí prázdné řetězce.</span><span class="sxs-lookup"><span data-stu-id="53860-191">It detects blank search strings.</span></span> <span data-ttu-id="53860-192">Robustnější tento program můžete provést pomocí jiné chyby, například překračuje maximální počet slova nebo řádky, které mohou být započítány zpracování.</span><span class="sxs-lookup"><span data-stu-id="53860-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53860-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="53860-193">See Also</span></span>  
 [<span data-ttu-id="53860-194">Dělení na vlákna (C#)</span><span class="sxs-lookup"><span data-stu-id="53860-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="53860-195">Postupy: přihlášení a odhlášení odběru událostí</span><span class="sxs-lookup"><span data-stu-id="53860-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
