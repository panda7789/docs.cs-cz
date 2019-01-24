---
title: Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: e4e0fcb1d706fef09233543487aebdeb01cdfbcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695890"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="031b0-102">Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="031b0-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="031b0-103">Můžete nastavit tlačítko, které můžete použít pro zrušení asynchronní aplikace, pokud nechcete čekat na dokončení.</span><span class="sxs-lookup"><span data-stu-id="031b0-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="031b0-104">Podle příkladů v tomto tématu můžete přidat tlačítko pro zrušení do aplikace, která stahuje obsah z jednoho webu nebo seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="031b0-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="031b0-105">V příkladech se používá uživatelské rozhraní, která [asynchronní aplikace Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) popisuje.</span><span class="sxs-lookup"><span data-stu-id="031b0-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="031b0-106">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="031b0-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a> <span data-ttu-id="031b0-107">Zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="031b0-107">Cancel a Task</span></span>  
 <span data-ttu-id="031b0-108">V prvním příkladu **zrušit** tlačítko s jeden úkol stahování.</span><span class="sxs-lookup"><span data-stu-id="031b0-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="031b0-109">Pokud tlačítko použijete, když aplikace stahuje obsah, stahování bude zrušeno.</span><span class="sxs-lookup"><span data-stu-id="031b0-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="031b0-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="031b0-110">Downloading the Example</span></span>  
 <span data-ttu-id="031b0-111">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="031b0-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="031b0-112">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="031b0-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="031b0-113">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="031b0-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="031b0-114">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="031b0-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="031b0-115">V **Průzkumníka řešení**, otevřete místní nabídku **CancelATask** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="031b0-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="031b0-116">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="031b0-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="031b0-117">Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="031b0-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="031b0-118">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubory MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="031b0-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="031b0-119">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="031b0-119">Building the Example</span></span>  
 <span data-ttu-id="031b0-120">Následující změny přidají **zrušit** tlačítko aplikace, která stahuje Web.</span><span class="sxs-lookup"><span data-stu-id="031b0-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="031b0-121">Pokud nechcete stahovat či sestavovat příklad, můžete zkontrolovat konečný produkt v části "Kompletní příklady" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="031b0-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="031b0-122">Hvězdičky označují změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="031b0-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="031b0-123">Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **StarterCode** jako **spouštěný projekt** místo **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="031b0-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="031b0-124">Pak přidejte následující změny do souboru MainWindow.xaml.vb tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="031b0-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="031b0-125">Deklarovat `CancellationTokenSource` proměnnou, `cts`, která je v oboru pro všechny metody, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="031b0-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="031b0-126">Přidejte následující obslužnou rutinu události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="031b0-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="031b0-127">Obslužná rutina události používá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda oznámit `cts` Pokud uživatel požaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="031b0-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="031b0-128">Proveďte následující změny v obslužné rutiny **Start** tlačítko `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="031b0-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="031b0-129">Vytvoření instance `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="031b0-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="031b0-130">Při volání funkce `AccessTheWebAsync`, která stahuje obsah zadaného webu, odešlete <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="031b0-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="031b0-131">`Token` Vlastnost šíří zprávy, pokud je požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="031b0-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="031b0-132">Přidáte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit stahování.</span><span class="sxs-lookup"><span data-stu-id="031b0-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="031b0-133">Následující kód ukazuje změny.</span><span class="sxs-lookup"><span data-stu-id="031b0-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="031b0-134">V `AccessTheWebAsync`, použijte <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> přetížení `GetAsync` metoda ve <xref:System.Net.Http.HttpClient> typ pro stažení obsahu webu.</span><span class="sxs-lookup"><span data-stu-id="031b0-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="031b0-135">Předejte `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="031b0-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="031b0-136">Token přenáší zprávy, pokud uživatel klikne **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="031b0-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="031b0-137">Následující kód ukazuje změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="031b0-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="031b0-138">Pokud nezrušíte program, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="031b0-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="031b0-139">Pokud se rozhodnete **zrušit** dříve, než program dokončí stahování obsahu, program vygeneruje následující výstup.</span><span class="sxs-lookup"><span data-stu-id="031b0-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="031b0-140">Zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="031b0-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="031b0-141">Můžete rozšířit předchozí příklad zrušit tak řadu úkolů propojením stejné `CancellationTokenSource` instance s jednotlivými úkoly.</span><span class="sxs-lookup"><span data-stu-id="031b0-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="031b0-142">Pokud se rozhodnete **zrušit** , zrušíte všechny úlohy, které ještě nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="031b0-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="031b0-143">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="031b0-143">Downloading the Example</span></span>  
 <span data-ttu-id="031b0-144">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="031b0-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="031b0-145">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="031b0-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="031b0-146">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="031b0-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="031b0-147">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="031b0-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="031b0-148">V **Průzkumníka řešení**, otevřete místní nabídku **CancelAListOfTasks** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="031b0-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="031b0-149">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="031b0-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="031b0-150">Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="031b0-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="031b0-151">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubory MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="031b0-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="031b0-152">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="031b0-152">Building the Example</span></span>  
 <span data-ttu-id="031b0-153">Pokud chcete rozšířit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelATask** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="031b0-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="031b0-154">Přidejte následující změny do tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="031b0-154">Add the following changes to that project.</span></span> <span data-ttu-id="031b0-155">Hvězdičky označují změny v programu.</span><span class="sxs-lookup"><span data-stu-id="031b0-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="031b0-156">Přidejte metodu pro vytvoření seznamu webových adres.</span><span class="sxs-lookup"><span data-stu-id="031b0-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  <span data-ttu-id="031b0-157">Volání metody `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="031b0-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="031b0-158">Přidejte následující smyčku v `AccessTheWebAsync` pro zpracování každé webové adresy v seznamu.</span><span class="sxs-lookup"><span data-stu-id="031b0-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="031b0-159">Protože `AccessTheWebAsync` zobrazí délky, metoda nemusí nic vrátit.</span><span class="sxs-lookup"><span data-stu-id="031b0-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="031b0-160">Odeberte příkaz return a změňte návratový typ metody, která <xref:System.Threading.Tasks.Task> místo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="031b0-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="031b0-161">Volejte metodu z `startButton_Click` pomocí příkazu namísto výrazu.</span><span class="sxs-lookup"><span data-stu-id="031b0-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="031b0-162">Pokud nezrušíte program, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="031b0-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="031b0-163">Pokud se rozhodnete **zrušit** tlačítko předtím, než se stahování dokončí, obsahuje výstup rozsah stahování, které dokončen před zrušením.</span><span class="sxs-lookup"><span data-stu-id="031b0-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="031b0-164">Kompletní příklady</span><span class="sxs-lookup"><span data-stu-id="031b0-164">Complete Examples</span></span>  
 <span data-ttu-id="031b0-165">Následující části obsahují kód pro každý z předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="031b0-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="031b0-166">Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="031b0-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="031b0-167">Můžete si stáhnout projektů z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="031b0-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="031b0-168">Příklad zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="031b0-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="031b0-169">Následující kód je celý soubor MainWindow.xaml.vb pro příklad, který zruší jednu úlohu.</span><span class="sxs-lookup"><span data-stu-id="031b0-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="031b0-170">Příklad zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="031b0-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="031b0-171">Následující kód je celý soubor MainWindow.xaml.vb pro příklad, který zruší seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="031b0-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="031b0-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="031b0-172">See also</span></span>
- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="031b0-173">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="031b0-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="031b0-174">Doladění aplikace s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="031b0-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="031b0-175">Ukázka asynchronní metody: Vyladění aplikace</span><span class="sxs-lookup"><span data-stu-id="031b0-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
