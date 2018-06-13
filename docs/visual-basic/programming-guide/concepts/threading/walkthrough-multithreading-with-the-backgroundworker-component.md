---
title: Multithreading s komponentou BackgroundWorker (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654288"
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="d838e-102">Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d838e-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="d838e-103">Tento návod ukazuje, jak vytvořit vícevláknové aplikace Windows Forms, která hledá textového souboru pro výskytů slova.</span><span class="sxs-lookup"><span data-stu-id="d838e-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="d838e-104">Ukazuje:</span><span class="sxs-lookup"><span data-stu-id="d838e-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="d838e-105">Definování třídy pomocí metody, která může být volána <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="d838e-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="d838e-106">Zpracování událostí vyvolaných <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="d838e-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="d838e-107">Spuštění <xref:System.ComponentModel.BackgroundWorker> součást, kterou metodu spustit.</span><span class="sxs-lookup"><span data-stu-id="d838e-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="d838e-108">Implementace `Cancel` tlačítko, která ukončí <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="d838e-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="d838e-109">Vytvoření uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d838e-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="d838e-110">Otevřete nový projekt aplikace Windows Forms jazyka Visual Basic a vytvořit s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d838e-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="d838e-111">Přidat dvě tlačítka a čtyři textová pole na `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d838e-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="d838e-112">Název objekty, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d838e-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="d838e-113">Objekt</span><span class="sxs-lookup"><span data-stu-id="d838e-113">Object</span></span>|<span data-ttu-id="d838e-114">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d838e-114">Property</span></span>|<span data-ttu-id="d838e-115">Nastavení</span><span class="sxs-lookup"><span data-stu-id="d838e-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="d838e-116">První tlačítko</span><span class="sxs-lookup"><span data-stu-id="d838e-116">First button</span></span>|<span data-ttu-id="d838e-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-117">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-118">Spuštění, spuštění</span><span class="sxs-lookup"><span data-stu-id="d838e-118">Start, Start</span></span>|  
    |<span data-ttu-id="d838e-119">Druhý tlačítko</span><span class="sxs-lookup"><span data-stu-id="d838e-119">Second button</span></span>|<span data-ttu-id="d838e-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-120">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-121">Zrušit, zrušit</span><span class="sxs-lookup"><span data-stu-id="d838e-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="d838e-122">První textové pole</span><span class="sxs-lookup"><span data-stu-id="d838e-122">First text box</span></span>|<span data-ttu-id="d838e-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-123">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-124">Zdrojový soubor, ""</span><span class="sxs-lookup"><span data-stu-id="d838e-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="d838e-125">Druhý textového pole</span><span class="sxs-lookup"><span data-stu-id="d838e-125">Second text box</span></span>|<span data-ttu-id="d838e-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-126">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="d838e-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="d838e-128">Třetí textové pole</span><span class="sxs-lookup"><span data-stu-id="d838e-128">Third text box</span></span>|<span data-ttu-id="d838e-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-129">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-130">WordsCounted "0"</span><span class="sxs-lookup"><span data-stu-id="d838e-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="d838e-131">Čtvrtý textového pole</span><span class="sxs-lookup"><span data-stu-id="d838e-131">Fourth text box</span></span>|<span data-ttu-id="d838e-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d838e-132">`Name`, `Text`</span></span>|<span data-ttu-id="d838e-133">LinesCounted "0"</span><span class="sxs-lookup"><span data-stu-id="d838e-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="d838e-134">Přidání štítku vedle každého textového pole.</span><span class="sxs-lookup"><span data-stu-id="d838e-134">Add a label next to each text box.</span></span> <span data-ttu-id="d838e-135">Nastavte `Text` vlastnost pro každý štítek, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d838e-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="d838e-136">Objekt</span><span class="sxs-lookup"><span data-stu-id="d838e-136">Object</span></span>|<span data-ttu-id="d838e-137">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d838e-137">Property</span></span>|<span data-ttu-id="d838e-138">Nastavení</span><span class="sxs-lookup"><span data-stu-id="d838e-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="d838e-139">První popisek</span><span class="sxs-lookup"><span data-stu-id="d838e-139">First label</span></span>|`Text`|<span data-ttu-id="d838e-140">Zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="d838e-140">Source File</span></span>|  
    |<span data-ttu-id="d838e-141">Druhý popisek</span><span class="sxs-lookup"><span data-stu-id="d838e-141">Second label</span></span>|`Text`|<span data-ttu-id="d838e-142">Porovnat řetězec</span><span class="sxs-lookup"><span data-stu-id="d838e-142">Compare String</span></span>|  
    |<span data-ttu-id="d838e-143">Třetí popisek</span><span class="sxs-lookup"><span data-stu-id="d838e-143">Third label</span></span>|`Text`|<span data-ttu-id="d838e-144">Klíčových slov</span><span class="sxs-lookup"><span data-stu-id="d838e-144">Matching Words</span></span>|  
    |<span data-ttu-id="d838e-145">Čtvrtý popisek</span><span class="sxs-lookup"><span data-stu-id="d838e-145">Fourth label</span></span>|`Text`|<span data-ttu-id="d838e-146">Řádky, na které se mají spočítat</span><span class="sxs-lookup"><span data-stu-id="d838e-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="d838e-147">K vytvoření BackgroundWorker – komponenta a přihlásit se k události</span><span class="sxs-lookup"><span data-stu-id="d838e-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="d838e-148">Přidat <xref:System.ComponentModel.BackgroundWorker> součásti z **součásti** části **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d838e-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="d838e-149">Zobrazí se na panelu součást formuláře.</span><span class="sxs-lookup"><span data-stu-id="d838e-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="d838e-150">Nastavte následující vlastnosti pro objekt BackgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="d838e-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="d838e-151">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d838e-151">Property</span></span>|<span data-ttu-id="d838e-152">Nastavení</span><span class="sxs-lookup"><span data-stu-id="d838e-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="d838e-153">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="d838e-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="d838e-154">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="d838e-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="d838e-155">Chcete-li definovat metody, která se spustí na samostatné vlákna</span><span class="sxs-lookup"><span data-stu-id="d838e-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="d838e-156">Z **projektu** nabídce zvolte **přidat třídu** přidat třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="d838e-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="d838e-157">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d838e-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="d838e-158">Vyberte **třída** z šablony a zadejte `Words.vb` v poli název.</span><span class="sxs-lookup"><span data-stu-id="d838e-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="d838e-159">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="d838e-159">Click **Add**.</span></span> <span data-ttu-id="d838e-160">`Words` Třídy se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d838e-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="d838e-161">Přidejte následující kód, který `Words` třídy:</span><span class="sxs-lookup"><span data-stu-id="d838e-161">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="d838e-162">Zpracování událostí z vlákna</span><span class="sxs-lookup"><span data-stu-id="d838e-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="d838e-163">Přidejte následující obslužné rutiny událostí do svého formuláře hlavní:</span><span class="sxs-lookup"><span data-stu-id="d838e-163">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="d838e-164">Spuštění a volání nové vlákno používající metodu WordCount</span><span class="sxs-lookup"><span data-stu-id="d838e-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="d838e-165">Přidáte do programu následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="d838e-165">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="d838e-166">Volání `StartThread` metoda z `Start` tlačítko ve formuláři:</span><span class="sxs-lookup"><span data-stu-id="d838e-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="d838e-167">K implementaci tlačítko Zrušit, která ukončí vlákno</span><span class="sxs-lookup"><span data-stu-id="d838e-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="d838e-168">Volání `StopThread` procedury `Click` obslužné rutiny události pro `Cancel` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d838e-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="d838e-169">Testování</span><span class="sxs-lookup"><span data-stu-id="d838e-169">Testing</span></span>  
 <span data-ttu-id="d838e-170">Nyní můžete otestovat aplikace a ujistěte se, že funguje správně.</span><span class="sxs-lookup"><span data-stu-id="d838e-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="d838e-171">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="d838e-171">To test the application</span></span>  
  
1.  <span data-ttu-id="d838e-172">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d838e-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="d838e-173">Když je formulář zobrazen, zadejte cestu k souboru pro soubor, který chcete otestovat v `sourceFile` pole.</span><span class="sxs-lookup"><span data-stu-id="d838e-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="d838e-174">Za předpokladu, že testovací soubor je s názvem Test.txt, zadejte například C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="d838e-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="d838e-175">Do textového pole druhý zadejte slovo nebo frázi pro aplikace pro vyhledání v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="d838e-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="d838e-176">Klikněte `Start` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d838e-176">Click the `Start` button.</span></span> <span data-ttu-id="d838e-177">`LinesCounted` Tlačítko by měl začínat zvyšování okamžitě.</span><span class="sxs-lookup"><span data-stu-id="d838e-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="d838e-178">Aplikace zobrazí zpráva "Počítání dokončeno", pokud se provádí.</span><span class="sxs-lookup"><span data-stu-id="d838e-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="d838e-179">K testování na tlačítko Storno</span><span class="sxs-lookup"><span data-stu-id="d838e-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="d838e-180">Stisknutím klávesy F5 spusťte aplikaci a zadat soubor název a hledání slovo jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="d838e-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="d838e-181">Ujistěte se, zda je soubor, který zvolíte dostatečně velký, ujistěte se, že bude mít čas zrušit postupu před dokončením.</span><span class="sxs-lookup"><span data-stu-id="d838e-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="d838e-182">Klikněte `Start` tlačítko spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d838e-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="d838e-183">Klikněte `Cancel` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d838e-183">Click the `Cancel` button.</span></span> <span data-ttu-id="d838e-184">Aplikace by se měla zastavit počítání okamžitě.</span><span class="sxs-lookup"><span data-stu-id="d838e-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d838e-185">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d838e-185">Next Steps</span></span>  
 <span data-ttu-id="d838e-186">Tato aplikace obsahuje některé základní chyba zpracování.</span><span class="sxs-lookup"><span data-stu-id="d838e-186">This application contains some basic error handling.</span></span> <span data-ttu-id="d838e-187">Zjistí prázdné řetězce.</span><span class="sxs-lookup"><span data-stu-id="d838e-187">It detects blank search strings.</span></span> <span data-ttu-id="d838e-188">Robustnější tento program můžete provést pomocí jiné chyby, například překračuje maximální počet slova nebo řádky, které mohou být započítány zpracování.</span><span class="sxs-lookup"><span data-stu-id="d838e-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d838e-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="d838e-189">See Also</span></span>  
 [<span data-ttu-id="d838e-190">Dělení na vlákna (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d838e-190">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="d838e-191">Návod: Vytvoření jednoduché vícevláknové komponenty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d838e-191">Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic</span></span>](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [<span data-ttu-id="d838e-192">Postupy: Přihlášení a odhlášení odběru událostí</span><span class="sxs-lookup"><span data-stu-id="d838e-192">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
