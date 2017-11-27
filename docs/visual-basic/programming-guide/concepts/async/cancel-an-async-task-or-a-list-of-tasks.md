---
title: "Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 916577107bd65559aed71dc9bb2921969a117e90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="ab93d-102">Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab93d-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="ab93d-103">Můžete nastavit tlačítko, které můžete zrušit asynchronní aplikace, pokud nechcete čekat na dokončení.</span><span class="sxs-lookup"><span data-stu-id="ab93d-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="ab93d-104">Pomocí následujících příkladech v tomto tématu, můžete přidat tlačítko zrušení k aplikaci, která stahuje obsah jeden web nebo seznam webů.</span><span class="sxs-lookup"><span data-stu-id="ab93d-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="ab93d-105">Příklady pomocí uživatelského rozhraní, [Fine-Tuning vaše asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) popisuje.</span><span class="sxs-lookup"><span data-stu-id="ab93d-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab93d-106">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ab93d-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="ab93d-107"><a name="BKMK_CancelaTask"></a>Zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="ab93d-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="ab93d-108">V prvním příkladu přidruží **zrušit** tlačítka s jeden stahování.</span><span class="sxs-lookup"><span data-stu-id="ab93d-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="ab93d-109">Pokud si zvolíte tlačítko, zatímco aplikace je stahování obsahu, stahování je zrušeno.</span><span class="sxs-lookup"><span data-stu-id="ab93d-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="ab93d-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="ab93d-110">Downloading the Example</span></span>  
 <span data-ttu-id="ab93d-111">Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="ab93d-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="ab93d-112">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab93d-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ab93d-113">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="ab93d-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="ab93d-114">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="ab93d-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="ab93d-115">V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelATask** projektu a potom vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="ab93d-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="ab93d-116">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="ab93d-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="ab93d-117">Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.</span><span class="sxs-lookup"><span data-stu-id="ab93d-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="ab93d-118">Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubory MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="ab93d-119">Vytváření v příkladu</span><span class="sxs-lookup"><span data-stu-id="ab93d-119">Building the Example</span></span>  
 <span data-ttu-id="ab93d-120">Přidejte následující změny **zrušit** tlačítko aplikace, která soubory ke stažení webu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="ab93d-121">Pokud nechcete, aby stáhnout nebo sestavení v příkladu, můžete zkontrolovat poslední produktu v části "Dokončení příklady" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="ab93d-122">Hvězdičky označit změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="ab93d-123">K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **StarterCode** jako **spouštěný projekt** místo **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="ab93d-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="ab93d-124">Přidejte následující změny do souboru MainWindow.xaml.vb tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="ab93d-125">Deklarace `CancellationTokenSource` proměnnou, `cts`, který je v oboru pro všechny metody, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="ab93d-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="ab93d-126">Přidejte následující obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ab93d-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="ab93d-127">Obslužné rutiny události se používá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda oznámit `cts` Pokud uživatel požaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="ab93d-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="ab93d-128">Zkontrolujte následující změny v obslužné rutiny **spustit** tlačítko `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ab93d-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="ab93d-129">Vytvoření instance `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="ab93d-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="ab93d-130">Ve volání `AccessTheWebAsync`, který stáhne obsah zadaného webu, odesílání <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="ab93d-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="ab93d-131">`Token` Vlastnost rozšíří zprávu, pokud se vyžaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="ab93d-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="ab93d-132">Přidáte blok catch, který zobrazí zprávu, pokud uživatel vybere možnost zrušit operaci stahování.</span><span class="sxs-lookup"><span data-stu-id="ab93d-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="ab93d-133">Následující kód ukazuje změny.</span><span class="sxs-lookup"><span data-stu-id="ab93d-133">The following code shows the changes.</span></span>  
  
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
  
4.  <span data-ttu-id="ab93d-134">V `AccessTheWebAsync`, použijte <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> přetížení z `GetAsync` metoda v <xref:System.Net.Http.HttpClient> typ pro stažení obsahu webu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="ab93d-135">Předat `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="ab93d-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="ab93d-136">Token představuje zprávu, pokud se uživatel rozhodne **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ab93d-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="ab93d-137">Následující kód ukazuje změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ab93d-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
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
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="ab93d-138">Pokud nemáte zrušení programu, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="ab93d-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="ab93d-139">Pokud se rozhodnete **zrušit** tlačítko před program dokončí stahování obsahu, program vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="ab93d-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="ab93d-140"><a name="BKMK_CancelaListofTasks"></a>Zrušit seznam úloh</span><span class="sxs-lookup"><span data-stu-id="ab93d-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="ab93d-141">Můžete rozšířit předchozí příklad zrušit celou řadu úloh tím, že přidružíte stejné `CancellationTokenSource` instance s každý úkol.</span><span class="sxs-lookup"><span data-stu-id="ab93d-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="ab93d-142">Pokud se rozhodnete **zrušit** tlačítko Zrušit všechny úlohy, které ještě nejsou úplné.</span><span class="sxs-lookup"><span data-stu-id="ab93d-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="ab93d-143">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="ab93d-143">Downloading the Example</span></span>  
 <span data-ttu-id="ab93d-144">Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="ab93d-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="ab93d-145">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab93d-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ab93d-146">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="ab93d-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="ab93d-147">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="ab93d-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="ab93d-148">V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAListOfTasks** projektu a potom vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="ab93d-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="ab93d-149">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="ab93d-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="ab93d-150">Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.</span><span class="sxs-lookup"><span data-stu-id="ab93d-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="ab93d-151">Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubory MainWindow.xaml.vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="ab93d-152">Vytváření v příkladu</span><span class="sxs-lookup"><span data-stu-id="ab93d-152">Building the Example</span></span>  
 <span data-ttu-id="ab93d-153">Příklad rozšířit sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelATask** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="ab93d-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="ab93d-154">Přidejte následující změny do tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-154">Add the following changes to that project.</span></span> <span data-ttu-id="ab93d-155">Hvězdičky označit změny v programu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="ab93d-156">Přidejte metodu pro vytvoření seznamu webové adresy.</span><span class="sxs-lookup"><span data-stu-id="ab93d-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  <span data-ttu-id="ab93d-157">Volání metody ve `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ab93d-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="ab93d-158">Přidejte následující zacyklení v `AccessTheWebAsync` ke zpracování jednotlivých webovou adresu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
  
4.  <span data-ttu-id="ab93d-159">Protože `AccessTheWebAsync` zobrazí délky, metoda nemusí nic vrátit.</span><span class="sxs-lookup"><span data-stu-id="ab93d-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="ab93d-160">Odeberte příkaz return a změňte návratový typ metody, která <xref:System.Threading.Tasks.Task> místo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ab93d-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="ab93d-161">Volejte metodu z `startButton_Click` za použití příkazu místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="ab93d-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="ab93d-162">Pokud nemáte zrušení programu, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="ab93d-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="ab93d-163">Pokud se rozhodnete **zrušit** tlačítko předtím, než souborům ke stažení jsou kompletní výstup obsahuje délek stahování, které byly dokončeny před zrušení.</span><span class="sxs-lookup"><span data-stu-id="ab93d-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <span data-ttu-id="ab93d-164"><a name="BKMK_CompleteExamples"></a>Dokončit příklady</span><span class="sxs-lookup"><span data-stu-id="ab93d-164"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="ab93d-165">Kód pro každou z předchozích příkladech v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="ab93d-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="ab93d-166">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="ab93d-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="ab93d-167">Si můžete stáhnout z projektů [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="ab93d-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="ab93d-168">Příklad zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="ab93d-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="ab93d-169">Následující kód je soubor MainWindow.xaml.vb kompletní příklad, který zruší jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="ab93d-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
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
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="ab93d-170">Příklad zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="ab93d-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="ab93d-171">Následující kód je soubor MainWindow.xaml.vb kompletní příklad, který zruší seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="ab93d-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="ab93d-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab93d-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="ab93d-173">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab93d-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="ab93d-174">Vyladění s modifikátorem Async aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab93d-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="ab93d-175">Ukázka asynchronního: Jemnou ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="ab93d-175">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
