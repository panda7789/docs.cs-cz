---
title: Zrušení asynchronní úlohy nebo seznamu úloh (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 01557bf80f40d4197d29ab05cfb4838f5d993a82
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295741"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="e0d56-102">Zrušení asynchronní úlohy nebo seznamu úloh (C#)</span><span class="sxs-lookup"><span data-stu-id="e0d56-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="e0d56-103">Můžete nastavit tlačítko, které můžete použít pro zrušení asynchronní aplikace, pokud nechcete čekat na dokončení.</span><span class="sxs-lookup"><span data-stu-id="e0d56-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="e0d56-104">Podle příkladů v tomto tématu můžete přidat tlačítko pro zrušení do aplikace, která stahuje obsah z jednoho webu nebo seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="e0d56-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="e0d56-105">V příkladech se používá uživatelské rozhraní, která [Fine-Tuning asynchronní aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) popisuje.</span><span class="sxs-lookup"><span data-stu-id="e0d56-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="e0d56-106">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="e0d56-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="e0d56-107">Zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="e0d56-107">Cancel a task</span></span>

<span data-ttu-id="e0d56-108">V prvním příkladu **zrušit** tlačítko s jeden úkol stahování.</span><span class="sxs-lookup"><span data-stu-id="e0d56-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="e0d56-109">Pokud tlačítko použijete, když aplikace stahuje obsah, stahování bude zrušeno.</span><span class="sxs-lookup"><span data-stu-id="e0d56-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="e0d56-110">Stáhnout příklad</span><span class="sxs-lookup"><span data-stu-id="e0d56-110">Download the example</span></span>

<span data-ttu-id="e0d56-111">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="e0d56-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e0d56-112">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0d56-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e0d56-113">V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="e0d56-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e0d56-114">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="e0d56-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="e0d56-115">V **Průzkumníka řešení**, otevřete místní nabídku **CancelATask** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e0d56-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e0d56-116">Zvolte **F5** spusťte projekt (nebo stiskněte klávesu **Ctrl**+**F5** ke spuštění projektu bez ladění).</span><span class="sxs-lookup"><span data-stu-id="e0d56-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="e0d56-117">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="e0d56-118">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="e0d56-118">Build the example</span></span>
 <span data-ttu-id="e0d56-119">Následující změny přidají **zrušit** tlačítko aplikace, která stahuje Web.</span><span class="sxs-lookup"><span data-stu-id="e0d56-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="e0d56-120">Pokud nechcete stahovat či sestavovat příklad, můžete zkontrolovat konečný produkt v části "Kompletní příklady" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="e0d56-121">Hvězdičky označují změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="e0d56-122">Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **StarterCode** jako **spouštěný projekt** místo **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="e0d56-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="e0d56-123">Pak přidejte následující změny do souboru MainWindow.xaml.cs tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="e0d56-124">Deklarovat `CancellationTokenSource` proměnnou, `cts`, která je v oboru pro všechny metody, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="e0d56-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="e0d56-125">Přidejte následující obslužnou rutinu události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e0d56-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="e0d56-126">Obslužná rutina události používá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda oznámit `cts` Pokud uživatel požaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="e0d56-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="e0d56-127">Proveďte následující změny v obslužné rutiny **Start** tlačítko `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="e0d56-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    -   <span data-ttu-id="e0d56-128">Vytvoření instance `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="e0d56-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    -   <span data-ttu-id="e0d56-129">Při volání funkce `AccessTheWebAsync`, která stahuje obsah zadaného webu, odešlete <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="e0d56-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="e0d56-130">`Token` Vlastnost šíří zprávy, pokud je požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="e0d56-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="e0d56-131">Přidáte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit stahování.</span><span class="sxs-lookup"><span data-stu-id="e0d56-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="e0d56-132">Následující kód ukazuje změny.</span><span class="sxs-lookup"><span data-stu-id="e0d56-132">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="e0d56-133">V `AccessTheWebAsync`, použijte <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> přetížení `GetAsync` metoda ve <xref:System.Net.Http.HttpClient> typ pro stažení obsahu webu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="e0d56-134">Předejte `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="e0d56-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="e0d56-135">Token přenáší zprávy, pokud uživatel klikne **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e0d56-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="e0d56-136">Následující kód ukazuje změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e0d56-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="e0d56-137">Pokud nezrušíte program, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="e0d56-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="e0d56-138">Pokud se rozhodnete **zrušit** dříve, než program dokončí stahování obsahu, program vygeneruje následující výstup.</span><span class="sxs-lookup"><span data-stu-id="e0d56-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="e0d56-139">Zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="e0d56-139">Cancel a list of tasks</span></span>

<span data-ttu-id="e0d56-140">Můžete rozšířit předchozí příklad zrušit tak řadu úkolů propojením stejné `CancellationTokenSource` instance s jednotlivými úkoly.</span><span class="sxs-lookup"><span data-stu-id="e0d56-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="e0d56-141">Pokud se rozhodnete **zrušit** , zrušíte všechny úlohy, které ještě nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="e0d56-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="e0d56-142">Stáhnout příklad</span><span class="sxs-lookup"><span data-stu-id="e0d56-142">Download the example</span></span>

<span data-ttu-id="e0d56-143">Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="e0d56-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e0d56-144">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0d56-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e0d56-145">V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="e0d56-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e0d56-146">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="e0d56-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="e0d56-147">V **Průzkumníka řešení**, otevřete místní nabídku **CancelAListOfTasks** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e0d56-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e0d56-148">Zvolte **F5** spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e0d56-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="e0d56-149">Zvolte **Ctrl**+**F5** klíče ke spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="e0d56-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="e0d56-150">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="e0d56-151">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="e0d56-151">Build the example</span></span>

<span data-ttu-id="e0d56-152">Pokud chcete rozšířit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelATask** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e0d56-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="e0d56-153">Přidejte následující změny do tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-153">Add the following changes to that project.</span></span> <span data-ttu-id="e0d56-154">Hvězdičky označují změny v programu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="e0d56-155">Přidejte metodu pro vytvoření seznamu webových adres.</span><span class="sxs-lookup"><span data-stu-id="e0d56-155">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. <span data-ttu-id="e0d56-156">Volání metody `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e0d56-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="e0d56-157">Přidejte následující smyčku v `AccessTheWebAsync` pro zpracování každé webové adresy v seznamu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="e0d56-158">Protože `AccessTheWebAsync` zobrazí délky, metoda nemusí nic vrátit.</span><span class="sxs-lookup"><span data-stu-id="e0d56-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="e0d56-159">Odeberte příkaz return a změňte návratový typ metody, která <xref:System.Threading.Tasks.Task> místo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e0d56-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="e0d56-160">Volejte metodu z `startButton_Click` pomocí příkazu namísto výrazu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="e0d56-161">Pokud nezrušíte program, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="e0d56-161">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="e0d56-162">Pokud se rozhodnete **zrušit** tlačítko předtím, než se stahování dokončí, obsahuje výstup rozsah stahování, které dokončen před zrušením.</span><span class="sxs-lookup"><span data-stu-id="e0d56-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="e0d56-163">Kompletní příklady</span><span class="sxs-lookup"><span data-stu-id="e0d56-163">Complete examples</span></span>

<span data-ttu-id="e0d56-164">Následující části obsahují kód pro každý z předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="e0d56-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="e0d56-165">Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e0d56-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="e0d56-166">Můžete si stáhnout projektů z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e0d56-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="e0d56-167">Příklad: zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="e0d56-167">Example - Cancel a task</span></span>

<span data-ttu-id="e0d56-168">Následující kód je celý soubor MainWindow.xaml.cs pro příklad, který zruší jednu úlohu.</span><span class="sxs-lookup"><span data-stu-id="e0d56-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="e0d56-169">Příklad – zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="e0d56-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="e0d56-170">Následující kód je celý soubor MainWindow.xaml.cs pro příklad, který zruší seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="e0d56-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="e0d56-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0d56-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="e0d56-172">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="e0d56-172">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e0d56-173">Doladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="e0d56-173">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="e0d56-174">Ukázka asynchronní metody: Vyladění aplikace</span><span class="sxs-lookup"><span data-stu-id="e0d56-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
