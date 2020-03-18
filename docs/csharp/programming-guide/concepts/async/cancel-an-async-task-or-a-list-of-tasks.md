---
title: Zrušení asynchronní úlohy nebo seznamu úkolů (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595718"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="4b83b-102">Zrušení asynchronní úlohy nebo seznamu úkolů (C#)</span><span class="sxs-lookup"><span data-stu-id="4b83b-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="4b83b-103">Můžete nastavit tlačítko, které můžete použít ke zrušení asynchronní aplikace, pokud nechcete čekat na dokončení.</span><span class="sxs-lookup"><span data-stu-id="4b83b-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="4b83b-104">Podle příkladů v tomto tématu můžete přidat tlačítko zrušení do aplikace, která stáhne obsah jednoho webu nebo seznam webových stránek.</span><span class="sxs-lookup"><span data-stu-id="4b83b-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="4b83b-105">Příklady používají ui, které [fine-tuning vaše asynchronní aplikace (C#)](./fine-tuning-your-async-application.md) popisuje.</span><span class="sxs-lookup"><span data-stu-id="4b83b-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="4b83b-106">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="4b83b-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="4b83b-107">Zrušení úkolu</span><span class="sxs-lookup"><span data-stu-id="4b83b-107">Cancel a task</span></span>

<span data-ttu-id="4b83b-108">První příklad přidruží tlačítko **Storno** k jedné úloze stahování.</span><span class="sxs-lookup"><span data-stu-id="4b83b-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="4b83b-109">Pokud zvolíte tlačítko, když aplikace stahuje obsah, stahování se zruší.</span><span class="sxs-lookup"><span data-stu-id="4b83b-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="4b83b-110">Stáhněte si příklad</span><span class="sxs-lookup"><span data-stu-id="4b83b-110">Download the example</span></span>

<span data-ttu-id="4b83b-111">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="4b83b-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="4b83b-112">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b83b-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="4b83b-113">Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="4b83b-114">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="4b83b-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="4b83b-115">V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelATask** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="4b83b-116">Zvolte klávesu **F5** pro spuštění projektu (nebo stisknutím **klávesy Ctrl**+**F5** spusťte projekt bez ladění).</span><span class="sxs-lookup"><span data-stu-id="4b83b-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="4b83b-117">Pokud nechcete projekt stáhnout, můžete zkontrolovat MainWindow.xaml.cs soubory na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="4b83b-118">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="4b83b-118">Build the example</span></span>
 <span data-ttu-id="4b83b-119">Následující změny přidávají tlačítko **Storno** do aplikace, která stáhne web.</span><span class="sxs-lookup"><span data-stu-id="4b83b-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="4b83b-120">Pokud nechcete stáhnout nebo vytvořit příklad, můžete zkontrolovat konečný produkt v části "Kompletní příklady" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="4b83b-121">Hvězdičky označují změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="4b83b-122">Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **StarterCode** jako **projekt spuštění** namísto **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="4b83b-123">Potom přidejte následující změny do MainWindow.xaml.cs souboru tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="4b83b-124">Deklarovat proměnnou `CancellationTokenSource` , `cts`která je v oboru pro všechny metody, které k ní přistupují.</span><span class="sxs-lookup"><span data-stu-id="4b83b-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="4b83b-125">Přidejte následující obslužnou rutinu události pro tlačítko **Storno.**</span><span class="sxs-lookup"><span data-stu-id="4b83b-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="4b83b-126">Obslužná <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> rutina `cts` události používá metodu upozornit, když uživatel požaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="4b83b-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

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

3. <span data-ttu-id="4b83b-127">Proveďte následující změny v obslužné rutině události pro tlačítko **Start** . `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="4b83b-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="4b83b-128">Vytvořte suktivku `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="4b83b-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="4b83b-129">Ve volání `AccessTheWebAsync`, který stáhne obsah zadaného webu, odešlete <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="4b83b-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="4b83b-130">Vlastnost `Token` rozšíří zprávu, pokud je požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="4b83b-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="4b83b-131">Přidejte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit operaci stahování.</span><span class="sxs-lookup"><span data-stu-id="4b83b-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="4b83b-132">Následující kód ukazuje změny.</span><span class="sxs-lookup"><span data-stu-id="4b83b-132">The following code shows the changes.</span></span>

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

4. <span data-ttu-id="4b83b-133">V `AccessTheWebAsync`aplikaci <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> použijte `GetAsync` přetížení metody <xref:System.Net.Http.HttpClient> v typu ke stažení obsahu webu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="4b83b-134">Pass `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="4b83b-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="4b83b-135">Token nese zprávu, pokud uživatel zvolí **tlačítko Storno.**</span><span class="sxs-lookup"><span data-stu-id="4b83b-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="4b83b-136">Následující kód ukazuje změny `AccessTheWebAsync`v .</span><span class="sxs-lookup"><span data-stu-id="4b83b-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

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

5. <span data-ttu-id="4b83b-137">Pokud program nezrušíte, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4b83b-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="4b83b-138">Pokud zvolíte tlačítko **Storno** před dokončením stahování obsahu programem, program vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4b83b-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="4b83b-139">Zrušení seznamu úkolů</span><span class="sxs-lookup"><span data-stu-id="4b83b-139">Cancel a list of tasks</span></span>

<span data-ttu-id="4b83b-140">Předchozí příklad můžete rozšířit tak, aby zrušil mnoho úkolů, a to tak, že přisuzujete stejnou `CancellationTokenSource` instanci ke každému úkolu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="4b83b-141">Pokud zvolíte tlačítko **Storno,** zrušíte všechny úkoly, které ještě nejsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="4b83b-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="4b83b-142">Stáhněte si příklad</span><span class="sxs-lookup"><span data-stu-id="4b83b-142">Download the example</span></span>

<span data-ttu-id="4b83b-143">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="4b83b-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="4b83b-144">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b83b-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="4b83b-145">Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="4b83b-146">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="4b83b-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="4b83b-147">V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAListOfTasks** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="4b83b-148">Zvolte klávesu **F5** pro spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="4b83b-149">Zvolte **klávesy Ctrl**+**F5** pro spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="4b83b-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="4b83b-150">Pokud nechcete projekt stáhnout, můžete zkontrolovat MainWindow.xaml.cs soubory na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="4b83b-151">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="4b83b-151">Build the example</span></span>

<span data-ttu-id="4b83b-152">Chcete-li příklad rozšířit sami, krok za krokem postupujte podle pokynů v části Stažení příkladu, ale zvolte **CancelATask** jako **projekt spuštění**.</span><span class="sxs-lookup"><span data-stu-id="4b83b-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="4b83b-153">Přidejte do tohoto projektu následující změny.</span><span class="sxs-lookup"><span data-stu-id="4b83b-153">Add the following changes to that project.</span></span> <span data-ttu-id="4b83b-154">Hvězdičky označují změny v programu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="4b83b-155">Přidejte metodu pro vytvoření seznamu webových adres.</span><span class="sxs-lookup"><span data-stu-id="4b83b-155">Add a method to create a list of web addresses.</span></span>

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

2. <span data-ttu-id="4b83b-156">Volání metody `AccessTheWebAsync`v .</span><span class="sxs-lookup"><span data-stu-id="4b83b-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="4b83b-157">Přidejte následující `AccessTheWebAsync` smyčku do zpracování každé webové adresy v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

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

4. <span data-ttu-id="4b83b-158">Vzhledem k tomu, `AccessTheWebAsync` že zobrazuje délky, metoda není nutné vrátit nic.</span><span class="sxs-lookup"><span data-stu-id="4b83b-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="4b83b-159">Odeberte příkaz return a změňte návratový typ metody namísto <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4b83b-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="4b83b-160">Volání metody `startButton_Click` z pomocí příkazu namísto výrazu.</span><span class="sxs-lookup"><span data-stu-id="4b83b-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="4b83b-161">Pokud program nezrušíte, vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4b83b-161">If you don’t cancel the program, it produces the following output.</span></span>

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

     <span data-ttu-id="4b83b-162">Pokud zvolíte tlačítko **Storno** před dokončením stahování, výstup obsahuje délky stahování, které byly dokončeny před zrušením.</span><span class="sxs-lookup"><span data-stu-id="4b83b-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="4b83b-163">Kompletní příklady</span><span class="sxs-lookup"><span data-stu-id="4b83b-163">Complete examples</span></span>

<span data-ttu-id="4b83b-164">Následující části obsahují kód pro každý z předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="4b83b-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="4b83b-165">Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .</span><span class="sxs-lookup"><span data-stu-id="4b83b-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="4b83b-166">Projekty si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="4b83b-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="4b83b-167">Příklad - Zrušení úkolu</span><span class="sxs-lookup"><span data-stu-id="4b83b-167">Example - Cancel a task</span></span>

<span data-ttu-id="4b83b-168">Následující kód je kompletní MainWindow.xaml.cs soubor pro příklad, který zruší jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="4b83b-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="4b83b-169">Příklad – Zrušení seznamu úkolů</span><span class="sxs-lookup"><span data-stu-id="4b83b-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="4b83b-170">Následující kód je kompletní soubor MainWindow.xaml.cs pro příklad, který zruší seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="4b83b-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4b83b-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b83b-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="4b83b-172">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="4b83b-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="4b83b-173">Jemné doladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="4b83b-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="4b83b-174">Asynchronní ukázka: Jemné doladění aplikace</span><span class="sxs-lookup"><span data-stu-id="4b83b-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
