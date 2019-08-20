---
title: Zrušení asynchronní úlohy nebo seznamu úkolů (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595718"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="453a6-102">Zrušení asynchronní úlohy nebo seznamu úkolů (C#)</span><span class="sxs-lookup"><span data-stu-id="453a6-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="453a6-103">Můžete nastavit tlačítko, které můžete použít k zrušení asynchronní aplikace, pokud nechcete čekat na jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="453a6-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="453a6-104">Podle příkladů v tomto tématu můžete přidat tlačítko zrušení do aplikace, která stáhne obsah jednoho webu nebo seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="453a6-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="453a6-105">V příkladech se používá uživatelské rozhraní, které popisuje [vyladění asynchronníC#aplikace ()](./fine-tuning-your-async-application.md) .</span><span class="sxs-lookup"><span data-stu-id="453a6-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-106">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="453a6-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="453a6-107">Zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="453a6-107">Cancel a task</span></span>

<span data-ttu-id="453a6-108">První příklad přidruží tlačítko **Zrušit** k jedné úloze stažení.</span><span class="sxs-lookup"><span data-stu-id="453a6-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="453a6-109">Pokud zvolíte tlačítko, zatímco aplikace stahuje obsah, stahování se zruší.</span><span class="sxs-lookup"><span data-stu-id="453a6-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="453a6-110">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="453a6-110">Download the example</span></span>

<span data-ttu-id="453a6-111">Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="453a6-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="453a6-112">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="453a6-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="453a6-113">Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="453a6-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="453a6-114">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="453a6-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="453a6-115">V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelATask** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="453a6-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="453a6-116">Zvolte klávesu **F5** ke spuštění projektu (nebo stiskněte klávesovou **zkratku**+**F5** pro spuštění projektu bez ladění).</span><span class="sxs-lookup"><span data-stu-id="453a6-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="453a6-117">Pokud nechcete stáhnout projekt, můžete si prohlédnout soubory MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="453a6-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="453a6-118">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="453a6-118">Build the example</span></span>
 <span data-ttu-id="453a6-119">Následující změny přidají tlačítko **Storno** do aplikace, která stáhne Web.</span><span class="sxs-lookup"><span data-stu-id="453a6-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="453a6-120">Pokud nechcete stáhnout nebo sestavit příklad, můžete si prohlédnout konečný produkt v části "kompletní příklady" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="453a6-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="453a6-121">Hvězdičky označují změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="453a6-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="453a6-122">Pokud chcete sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt** vyberte **StarterCode** namísto **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="453a6-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="453a6-123">Pak přidejte následující změny do souboru MainWindow.xaml.cs tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="453a6-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="453a6-124">Deklarujte `CancellationTokenSource` `cts`proměnnou,, která je v oboru pro všechny metody, které k ní přistupují.</span><span class="sxs-lookup"><span data-stu-id="453a6-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="453a6-125">Přidejte následující obslužnou rutinu události pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="453a6-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="453a6-126">Obslužná rutina události používá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu k oznamování `cts` , když uživatel požaduje zrušení.</span><span class="sxs-lookup"><span data-stu-id="453a6-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

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

3. <span data-ttu-id="453a6-127">Proveďte následující změny v obslužné rutině události pro `startButton_Click`tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="453a6-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="453a6-128">Vytvořte instanci `cts`,. `CancellationTokenSource`</span><span class="sxs-lookup"><span data-stu-id="453a6-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="453a6-129">V volání metody `AccessTheWebAsync`, která stahuje obsah zadaného webu, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> odešlete vlastnost `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="453a6-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="453a6-130">Tato `Token` vlastnost šíří zprávu, pokud je požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="453a6-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="453a6-131">Přidejte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit operaci stahování.</span><span class="sxs-lookup"><span data-stu-id="453a6-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="453a6-132">Následující kód ukazuje změny.</span><span class="sxs-lookup"><span data-stu-id="453a6-132">The following code shows the changes.</span></span>

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

4. <span data-ttu-id="453a6-133">V `AccessTheWebAsync` použijte`GetAsync` přetížení metody v<xref:System.Net.Http.HttpClient> typu ke stažení obsahu webu. <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="453a6-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="453a6-134">Pass `ct`– parametr`AccessTheWebAsync`jakodruhýargument. <xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="453a6-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="453a6-135">Pokud uživatel klikne na tlačítko **Storno** , tento token zprávu přenese.</span><span class="sxs-lookup"><span data-stu-id="453a6-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="453a6-136">Následující kód ukazuje změny v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="453a6-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

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

5. <span data-ttu-id="453a6-137">Pokud program nerušíte, vytvoří se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="453a6-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="453a6-138">Pokud zvolíte tlačítko **Storno** před tím, než program dokončí stahování obsahu, program vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="453a6-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="453a6-139">Zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="453a6-139">Cancel a list of tasks</span></span>

<span data-ttu-id="453a6-140">Předchozí příklad můžete roztáhnout tak, aby bylo možné zrušit mnoho úloh přiřazením `CancellationTokenSource` stejné instance ke každému úkolu.</span><span class="sxs-lookup"><span data-stu-id="453a6-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="453a6-141">Pokud zvolíte tlačítko **Zrušit** , zrušíte tím všechny úlohy, které ještě nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="453a6-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="453a6-142">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="453a6-142">Download the example</span></span>

<span data-ttu-id="453a6-143">Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="453a6-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="453a6-144">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="453a6-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="453a6-145">Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="453a6-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="453a6-146">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="453a6-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="453a6-147">V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAListOfTasks** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="453a6-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="453a6-148">Kliknutím na klávesu **F5** spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="453a6-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="453a6-149">Vyberte klávesy **CTRL**+**F5** pro spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="453a6-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="453a6-150">Pokud nechcete stáhnout projekt, můžete si prohlédnout soubory MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="453a6-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="453a6-151">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="453a6-151">Build the example</span></span>

<span data-ttu-id="453a6-152">Chcete-li tento příklad roztáhnout sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="453a6-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="453a6-153">Do tohoto projektu přidejte následující změny.</span><span class="sxs-lookup"><span data-stu-id="453a6-153">Add the following changes to that project.</span></span> <span data-ttu-id="453a6-154">Hvězdičky označují změny v programu.</span><span class="sxs-lookup"><span data-stu-id="453a6-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="453a6-155">Přidejte metodu pro vytvoření seznamu webových adres.</span><span class="sxs-lookup"><span data-stu-id="453a6-155">Add a method to create a list of web addresses.</span></span>

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

2. <span data-ttu-id="453a6-156">Zavolejte metodu v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="453a6-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="453a6-157">Přidejte následující smyčku `AccessTheWebAsync` do pro zpracování každé webové adresy v seznamu.</span><span class="sxs-lookup"><span data-stu-id="453a6-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

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

4. <span data-ttu-id="453a6-158">Vzhledem `AccessTheWebAsync` k tomu, že se zobrazí délka, metoda nemusí vracet cokoli.</span><span class="sxs-lookup"><span data-stu-id="453a6-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="453a6-159">Odeberte příkaz return a změňte návratový typ metody na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>místo.</span><span class="sxs-lookup"><span data-stu-id="453a6-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="453a6-160">Volejte metodu z `startButton_Click` pomocí příkazu namísto výrazu.</span><span class="sxs-lookup"><span data-stu-id="453a6-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="453a6-161">Pokud program nerušíte, vytvoří se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="453a6-161">If you don’t cancel the program, it produces the following output.</span></span>

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

     <span data-ttu-id="453a6-162">Pokud zvolíte tlačítko **Zrušit** před dokončením stahování, bude výstup obsahovat délky stahování, která byla dokončena před zrušením.</span><span class="sxs-lookup"><span data-stu-id="453a6-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="453a6-163">Kompletní příklady</span><span class="sxs-lookup"><span data-stu-id="453a6-163">Complete examples</span></span>

<span data-ttu-id="453a6-164">Následující části obsahují kód pro každý z předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="453a6-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="453a6-165">Všimněte si, že je nutné přidat odkaz <xref:System.Net.Http>pro.</span><span class="sxs-lookup"><span data-stu-id="453a6-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="453a6-166">Projekty si můžete stáhnout z [Async Sample: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span><span class="sxs-lookup"><span data-stu-id="453a6-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="453a6-167">Příklad – zrušení úlohy</span><span class="sxs-lookup"><span data-stu-id="453a6-167">Example - Cancel a task</span></span>

<span data-ttu-id="453a6-168">Následující kód je úplný soubor MainWindow.xaml.cs pro příklad, který zruší jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="453a6-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="453a6-169">Příklad – zrušení seznamu úloh</span><span class="sxs-lookup"><span data-stu-id="453a6-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="453a6-170">Následující kód je úplný soubor MainWindow.xaml.cs pro příklad, který zruší seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="453a6-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="453a6-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="453a6-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="453a6-172">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="453a6-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="453a6-173">Vyladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="453a6-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="453a6-174">Asynchronní Ukázka: Jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="453a6-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
