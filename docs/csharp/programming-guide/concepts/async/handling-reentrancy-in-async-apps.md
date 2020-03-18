---
title: Zpracování reentrancy v asynchronních aplikacích (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451860"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="c5430-102">Zpracování reentrancy v asynchronních aplikacích (C#)</span><span class="sxs-lookup"><span data-stu-id="c5430-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="c5430-103">Když do aplikace zahrnete asynchronní kód, měli byste zvážit a případně zabránit reentrancy, což se týká opětovného zadání asynchronní operace před dokončením.</span><span class="sxs-lookup"><span data-stu-id="c5430-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="c5430-104">Pokud neidentifikujete a nezpracováváte možnosti reentrancy, může to způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="c5430-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="c5430-105">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="c5430-105">**In this topic**</span></span>

- [<span data-ttu-id="c5430-106">Rozpoznání reentrancy</span><span class="sxs-lookup"><span data-stu-id="c5430-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="c5430-107">Manipulace s reentrancy</span><span class="sxs-lookup"><span data-stu-id="c5430-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="c5430-108">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="c5430-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="c5430-109">Zrušit a restartovat operaci</span><span class="sxs-lookup"><span data-stu-id="c5430-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="c5430-110">Spuštění více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="c5430-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="c5430-111">Kontrola a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="c5430-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="c5430-112">Chcete-li spustit příklad, musíte mít v počítači nainstalovanou visual studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="c5430-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="c5430-113">Zabezpečení transportní vrstvy (TLS) verze 1.2 je nyní minimální verze, která se má použít ve vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5430-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="c5430-114">Pokud vaše aplikace cílí na verzi rozhraní .NET Framework starší než 4.7, přečtěte si následující článek o [doporučených postupech zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](../../../../framework/network-programming/tls.md).</span><span class="sxs-lookup"><span data-stu-id="c5430-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="c5430-115">Rozpoznání reentrancy</span><span class="sxs-lookup"><span data-stu-id="c5430-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="c5430-116">V příkladu v tomto tématu uživatelé zvolí tlačítko **Start** pro spuštění asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů.</span><span class="sxs-lookup"><span data-stu-id="c5430-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="c5430-117">Synchronní verze příkladu by reagovat stejným způsobem bez ohledu na to, kolikrát uživatel zvolí tlačítko, protože po prvním, vlákno uživatelského rozhraní ignoruje tyto události, dokud aplikace dokončí spuštění.</span><span class="sxs-lookup"><span data-stu-id="c5430-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="c5430-118">V asynchronní aplikaci však vlákno uživatelského rozhraní nadále reaguje a můžete znovu zadat asynchronní operaci před dokončením.</span><span class="sxs-lookup"><span data-stu-id="c5430-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="c5430-119">Následující příklad ukazuje očekávaný výstup, pokud uživatel zvolí tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c5430-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="c5430-120">Zobrazí se seznam stažených webů s velikostí jednotlivých webů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c5430-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="c5430-121">Celkový počet bajtů se zobrazí na konci.</span><span class="sxs-lookup"><span data-stu-id="c5430-121">The total number of bytes appears at the end.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="c5430-122">Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je pokaždé znovu zadán.</span><span class="sxs-lookup"><span data-stu-id="c5430-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="c5430-123">Výsledkem je několik asynchronních operací současně, výstup propojí výsledky a celkový počet bajtů je matoucí.</span><span class="sxs-lookup"><span data-stu-id="c5430-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="c5430-124">Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c5430-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="c5430-125">Můžete experimentovat s kódem stažením řešení do místního počítače a spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu.</span><span class="sxs-lookup"><span data-stu-id="c5430-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="c5430-126">Další informace a pokyny naleznete v [tématu Revize a spuštění aplikace Example .](#BKMD_SettingUpTheExample)</span><span class="sxs-lookup"><span data-stu-id="c5430-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="c5430-127">Manipulace s reentrancy</span><span class="sxs-lookup"><span data-stu-id="c5430-127">Handling Reentrancy</span></span>

<span data-ttu-id="c5430-128">Reentrancy můžete zpracovat různými způsoby v závislosti na tom, co chcete, aby vaše aplikace dělat.</span><span class="sxs-lookup"><span data-stu-id="c5430-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="c5430-129">Toto téma uvádí následující příklady:</span><span class="sxs-lookup"><span data-stu-id="c5430-129">This topic presents the following examples:</span></span>

- [<span data-ttu-id="c5430-130">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="c5430-130">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="c5430-131">Zakažte tlačítko **Start,** když je operace spuštěna, aby ji uživatel nemohl přerušit.</span><span class="sxs-lookup"><span data-stu-id="c5430-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="c5430-132">Zrušit a restartovat operaci</span><span class="sxs-lookup"><span data-stu-id="c5430-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="c5430-133">Zrušte všechny operace, které jsou stále spuštěny, když uživatel znovu vybere tlačítko **Start,** a potom nechte naposledy požadovanou operaci pokračovat.</span><span class="sxs-lookup"><span data-stu-id="c5430-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="c5430-134">Spuštění více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="c5430-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="c5430-135">Povolit všechny požadované operace spustit asynchronně, ale koordinovat zobrazení výstupu tak, aby výsledky z každé operace se zobrazí společně a v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c5430-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="c5430-136">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="c5430-136">Disable the Start Button</span></span>

<span data-ttu-id="c5430-137">Tlačítko **Start** můžete blokovat v době, kdy je spuštěna operace, zakázáním tlačítka v horní části obslužné rutiny `StartButton_Click` události.</span><span class="sxs-lookup"><span data-stu-id="c5430-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="c5430-138">Po dokončení operace pak můžete `finally` znovu povolit tlačítko z bloku, aby uživatelé mohli aplikaci znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="c5430-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="c5430-139">Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [revizi a spuštění aplikace Příklad](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="c5430-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="c5430-140">Hotovou aplikaci si také můžete stáhnout z [aplikace Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="c5430-140">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="c5430-141">Název projektu je DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="c5430-141">The name of the project is DisableStartButton.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

<span data-ttu-id="c5430-142">V důsledku změn tlačítko nereaguje při `AccessTheWebAsync` stahování webových stránek, takže proces nelze znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="c5430-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="c5430-143">Zrušit a restartovat operaci</span><span class="sxs-lookup"><span data-stu-id="c5430-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="c5430-144">Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko znovu zvolí, zrušte operaci, která je již spuštěna, a nechte pokračovat v naposledy zahájené operaci.</span><span class="sxs-lookup"><span data-stu-id="c5430-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="c5430-145">Další informace o zrušení naleznete v [tématu Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="c5430-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="c5430-146">Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [revizi a spuštění aplikace Příklad](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="c5430-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="c5430-147">Hotovou aplikaci si také můžete stáhnout z [aplikace Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="c5430-147">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="c5430-148">Název projektu je CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="c5430-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="c5430-149">Deklarovat proměnnou <xref:System.Threading.CancellationTokenSource> , `cts`která je v oboru pro všechny metody.</span><span class="sxs-lookup"><span data-stu-id="c5430-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="c5430-150">V `StartButton_Click`aplikaci určete, zda operace již probíhá.</span><span class="sxs-lookup"><span data-stu-id="c5430-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="c5430-151">Pokud `cts` je hodnota null, žádná operace je již aktivní.</span><span class="sxs-lookup"><span data-stu-id="c5430-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="c5430-152">Pokud hodnota není null, operace, která je již spuštěna, je zrušena.</span><span class="sxs-lookup"><span data-stu-id="c5430-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="c5430-153">Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c5430-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="c5430-154">Na konci `StartButton_Click`, aktuální proces je dokončen, takže `cts` nastavte hodnotu zpět na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5430-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="c5430-155">Následující kód zobrazuje všechny `StartButton_Click`změny v .</span><span class="sxs-lookup"><span data-stu-id="c5430-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="c5430-156">Přídavky jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="c5430-156">The additions are marked with asterisks.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

<span data-ttu-id="c5430-157">V `AccessTheWebAsync`, proveďte následující změny.</span><span class="sxs-lookup"><span data-stu-id="c5430-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="c5430-158">Přidejte parametr pro přijetí `StartButton_Click`tokenu zrušení z .</span><span class="sxs-lookup"><span data-stu-id="c5430-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="c5430-159">Pomocí <xref:System.Net.Http.HttpClient.GetAsync%2A> této metody stáhněte `GetAsync` weby, protože přijímá <xref:System.Threading.CancellationToken> argument.</span><span class="sxs-lookup"><span data-stu-id="c5430-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="c5430-160">Před `DisplayResults` voláním za účelem zobrazení výsledků `ct` pro každý stažený web zkontrolujte, zda nebyla aktuální operace zrušena.</span><span class="sxs-lookup"><span data-stu-id="c5430-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

<span data-ttu-id="c5430-161">Následující kód ukazuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="c5430-161">The following code shows these changes, which are marked with asterisks.</span></span>

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

<span data-ttu-id="c5430-162">Pokud zvolíte tlačítko **Start** několikrát, zatímco tato aplikace běží, by měla přinést výsledky, které se podobají následující výstup.</span><span class="sxs-lookup"><span data-stu-id="c5430-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="c5430-163">Chcete-li odstranit částečné seznamy, odkomentujte první řádek `StartButton_Click` kódu, abyste zrušili textové pole při každém restartování operace uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c5430-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="c5430-164">Spuštění více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="c5430-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="c5430-165">Tento třetí příklad je nejsložitější v tom, že aplikace spustí další asynchronní operaci pokaždé, když uživatel zvolí tlačítko **Start** a všechny operace spustit až do konce.</span><span class="sxs-lookup"><span data-stu-id="c5430-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="c5430-166">Všechny požadované operace stáhnout weby ze seznamu asynchronně, ale výstup z operací je prezentován akvenční.</span><span class="sxs-lookup"><span data-stu-id="c5430-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="c5430-167">To znamená, že skutečná aktivita stahování je prokládána, jak ukazuje výstup v [rozpoznávání reentrancy,](#BKMK_RecognizingReentrancy) ale seznam výsledků pro každou skupinu je uveden samostatně.</span><span class="sxs-lookup"><span data-stu-id="c5430-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="c5430-168">Operace sdílejí globální <xref:System.Threading.Tasks.Task> `pendingWork`, , který slouží jako gatekeeper pro proces zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c5430-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="c5430-169">Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [revizi a spuštění aplikace Příklad](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="c5430-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="c5430-170">Hotovou aplikaci si také můžete stáhnout z [aplikace Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="c5430-170">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="c5430-171">Název projektu je QueueResults.</span><span class="sxs-lookup"><span data-stu-id="c5430-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="c5430-172">Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c5430-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="c5430-173">Popisek písmene A označuje, že výsledek je od prvního výběru tlačítka **Start.**</span><span class="sxs-lookup"><span data-stu-id="c5430-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="c5430-174">Čísla zobrazují pořadí adres URL v seznamu cílů stahování.</span><span class="sxs-lookup"><span data-stu-id="c5430-174">The numbers show the order of the URLs in the list of download targets.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

<span data-ttu-id="c5430-175">Pokud uživatel třikrát zvolí tlačítko **Start,** aplikace vytvoří výstup, který se podobá následujícím řádkům.</span><span class="sxs-lookup"><span data-stu-id="c5430-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="c5430-176">Informační řádky, které začínají znakem libry (#), sledují průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5430-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

<span data-ttu-id="c5430-177">Skupiny B a C začínají před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně.</span><span class="sxs-lookup"><span data-stu-id="c5430-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="c5430-178">Nejprve se zobrazí veškerý výstup pro skupinu A následovaný veškerým výstupem pro skupinu B a potom veškerým výstupem pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.</span><span class="sxs-lookup"><span data-stu-id="c5430-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="c5430-179">Nelze však předpovědět pořadí, ve kterém ke stažení skutečně dochází.</span><span class="sxs-lookup"><span data-stu-id="c5430-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="c5430-180">Po spuštění více skupin jsou všechny úlohy stahování, které generují, aktivní.</span><span class="sxs-lookup"><span data-stu-id="c5430-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="c5430-181">Nemůžete předpokládat, že A-1 bude stažen před B-1, a nemůžete předpokládat, že A-1 bude staženpřed A-2.</span><span class="sxs-lookup"><span data-stu-id="c5430-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="c5430-182">Globální definice</span><span class="sxs-lookup"><span data-stu-id="c5430-182">Global Definitions</span></span>

<span data-ttu-id="c5430-183">Ukázkový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.</span><span class="sxs-lookup"><span data-stu-id="c5430-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="c5430-184">Proměnná `Task` `pendingWork`, dohlíží na proces zobrazení a zabraňuje jakékoli skupině přerušit operaci zobrazení jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="c5430-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="c5430-185">Znaková proměnná , `group`označuje výstup z různých skupin, aby ověřila, že se výsledky zobrazí v očekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c5430-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="c5430-186">Obslužná rutina události kliknutí</span><span class="sxs-lookup"><span data-stu-id="c5430-186">The Click Event Handler</span></span>

<span data-ttu-id="c5430-187">Obslužná rutina události , `StartButton_Click`zintáží skupinové písmeno pokaždé, když uživatel zvolí tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="c5430-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="c5430-188">Potom obslužná rutina volá `AccessTheWebAsync` ke spuštění operace stahování.</span><span class="sxs-lookup"><span data-stu-id="c5430-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="c5430-189">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="c5430-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="c5430-190">Tento příklad `AccessTheWebAsync` se rozdělí na dvě metody.</span><span class="sxs-lookup"><span data-stu-id="c5430-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="c5430-191">První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro `pendingWork` skupinu a nastaví řízení procesu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c5430-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="c5430-192">Metoda používá jazyk integrovaný dotaz (dotaz <xref:System.Linq.Enumerable.ToArray%2A> LINQ) a spustit všechny úlohy stahování ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="c5430-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="c5430-193">`AccessTheWebAsync`pak `FinishOneGroupAsync` volá čekat na dokončení každého stažení a zobrazit jeho délku.</span><span class="sxs-lookup"><span data-stu-id="c5430-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="c5430-194">`FinishOneGroupAsync`vrátí úkol, který je `pendingWork` `AccessTheWebAsync`přiřazen v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="c5430-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="c5430-195">Tato hodnota zabraňuje přerušení jinou operací před dokončením úlohy.</span><span class="sxs-lookup"><span data-stu-id="c5430-195">That value prevents interruption by another operation before the task is complete.</span></span>

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="c5430-196">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="c5430-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="c5430-197">Tato metoda cyklicky prochází úlohy stahování ve skupině, čeká na každou z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.</span><span class="sxs-lookup"><span data-stu-id="c5430-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="c5430-198">První příkaz `FinishOneGroupAsync` v `pendingWork` používá k ujistěte se, že zadání metody není v rozporu s operací, která je již v procesu zobrazení nebo který je již čeká.</span><span class="sxs-lookup"><span data-stu-id="c5430-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="c5430-199">Pokud taková operace probíhá, musí zadávacího řízení počkat, až přijde na řadu.</span><span class="sxs-lookup"><span data-stu-id="c5430-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a><span data-ttu-id="c5430-200">Body zájmu</span><span class="sxs-lookup"><span data-stu-id="c5430-200">Points of Interest</span></span>

<span data-ttu-id="c5430-201">Informační řádky, které začínají znakem libry (#) ve výstupu, objasňují, jak tento příklad funguje.</span><span class="sxs-lookup"><span data-stu-id="c5430-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="c5430-202">Výstup ukazuje následující vzory.</span><span class="sxs-lookup"><span data-stu-id="c5430-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="c5430-203">Skupinu lze spustit, zatímco předchozí skupina zobrazuje svůj výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.</span><span class="sxs-lookup"><span data-stu-id="c5430-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- <span data-ttu-id="c5430-204">Úloha `pendingWork` má hodnotu `FinishOneGroupAsync` null na začátku pouze pro skupinu A, která byla spuštěna jako první.</span><span class="sxs-lookup"><span data-stu-id="c5430-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="c5430-205">Skupina A ještě nedokončila výraz čekání, `FinishOneGroupAsync`jakmile dosáhne .</span><span class="sxs-lookup"><span data-stu-id="c5430-205">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="c5430-206">Proto ovládací prvek nebyl `AccessTheWebAsync`vrácen do , `pendingWork` a první přiřazení do nedošlo.</span><span class="sxs-lookup"><span data-stu-id="c5430-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="c5430-207">Následující dva řádky se vždy zobrazí společně ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="c5430-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="c5430-208">Kód není nikdy přerušen mezi spuštěním `StartButton_Click` operace skupiny v aplikaci `pendingWork`a přiřazením úkolu pro skupinu .</span><span class="sxs-lookup"><span data-stu-id="c5430-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="c5430-209">Po zadání skupiny `StartButton_Click`operace nedokončí výraz čekání, dokud operace `FinishOneGroupAsync`nevstoupí .</span><span class="sxs-lookup"><span data-stu-id="c5430-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="c5430-210">Proto žádná jiná operace může získat kontrolu během tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="c5430-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="c5430-211">Kontrola a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="c5430-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="c5430-212">Chcete-li lépe porozumět ukázkové aplikaci, můžete si ji stáhnout, vytvořit sami nebo zkontrolovat kód na konci tohoto tématu bez implementace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5430-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="c5430-213">Chcete-li spustit příklad jako desktopovou aplikaci WPF (Windows Presentation Foundation), musíte mít v počítači nainstalovanou visual studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="c5430-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="c5430-214">Stažení aplikace</span><span class="sxs-lookup"><span data-stu-id="c5430-214">Downloading the App</span></span>

1. <span data-ttu-id="c5430-215">Stáhněte si komprimovaný soubor z [ukázky asynchronní: Reentrancy v .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="c5430-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="c5430-216">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5430-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="c5430-217">Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.</span><span class="sxs-lookup"><span data-stu-id="c5430-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="c5430-218">Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a otevřete soubor řešení (.sln).</span><span class="sxs-lookup"><span data-stu-id="c5430-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="c5430-219">V **Průzkumníku řešení**otevřete místní nabídku projektu, který chcete spustit, a pak zvolte **Nastavit jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="c5430-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="c5430-220">Zvolte klávesy CTRL+F5 pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="c5430-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="c5430-221">Vytváření aplikace</span><span class="sxs-lookup"><span data-stu-id="c5430-221">Building the App</span></span>

<span data-ttu-id="c5430-222">Následující část obsahuje kód pro sestavení příkladu jako aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="c5430-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="c5430-223">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c5430-223">To build a WPF app</span></span>

1. <span data-ttu-id="c5430-224">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5430-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="c5430-225">Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="c5430-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="c5430-226">Otevře se dialogové okno **Nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="c5430-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="c5430-227">V podokně **Nainstalované šablony** rozbalte **položku Visual C#** a potom rozbalte **položku Windows**.</span><span class="sxs-lookup"><span data-stu-id="c5430-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="c5430-228">V seznamu typů projektů zvolte **WPF Aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c5430-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="c5430-229">Pojmenujte `WebsiteDownloadWPF`projekt , zvolte verzi rozhraní .NET Framework verze 4.6 nebo vyšší a klepněte na tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="c5430-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="c5430-230">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="c5430-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="c5430-231">V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="c5430-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="c5430-232">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c5430-232">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="c5430-233">V zobrazení **XAML** MainWindow.xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="c5430-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     <span data-ttu-id="c5430-234">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhovém** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c5430-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="c5430-235">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **odkaz odkazy** a vyberte přidat **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="c5430-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="c5430-236">Přidejte odkaz <xref:System.Net.Http>pro , pokud ještě není vybrán.</span><span class="sxs-lookup"><span data-stu-id="c5430-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="c5430-237">V **Průzkumníku řešení**otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c5430-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="c5430-238">V MainWindow.xaml.cs nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="c5430-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

    // Add the following using directives, and add a reference for System.Net.Http.
    using System.Net.Http;
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. <span data-ttu-id="c5430-239">Chcete-li spustit program, zvolte klávesy CTRL+F5 a pak několikrát zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="c5430-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="c5430-240">Proveďte změny z [funkce Zakázat tlačítko Start](#BKMK_DisableTheStartButton), Zrušit a [restartovat operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a zařazujte výstup](#BKMK_RunMultipleOperations) do fronty, abyste zpracovat reentrancy.</span><span class="sxs-lookup"><span data-stu-id="c5430-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5430-241">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5430-241">See also</span></span>

- [<span data-ttu-id="c5430-242">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="c5430-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="c5430-243">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="c5430-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
