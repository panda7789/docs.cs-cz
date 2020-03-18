---
title: 'Návod: Přístup k webu pomocí asynchronní a čeká (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281782"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="cbe40-102">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe40-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="cbe40-103">Asynchronní programy můžete psát snadněji a intuitivně pomocí funkcí async/await.</span><span class="sxs-lookup"><span data-stu-id="cbe40-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="cbe40-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kód a nechat kompilátor zpracovat obtížné funkce zpětného volání a pokračování, které obvykle znamená asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="cbe40-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="cbe40-105">Další informace o funkci Async naleznete [v tématu Asynchronní programování s asynchronní a čeká (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="cbe40-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="cbe40-106">Tento návod začíná synchronní windows presentation foundation (WPF) aplikace, která sečte počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="cbe40-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="cbe40-107">Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="cbe40-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="cbe40-108">Pokud nechcete vytvářet aplikace sami, můžete si stáhnout [ukázku asynchronní: Přístup k webovému návodu (C# a Visual Basic).](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)</span><span class="sxs-lookup"><span data-stu-id="cbe40-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="cbe40-109">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="cbe40-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="cbe40-110">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="cbe40-110">Create a WPF application</span></span>

1. <span data-ttu-id="cbe40-111">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbe40-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="cbe40-112">Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="cbe40-113">Otevře se dialogové okno **Nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="cbe40-114">V podokně **Nainstalované šablony** zvolte Visual C# a ze seznamu typů projektů zvolte **WPF Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="cbe40-115">Do **Name** textového pole `AsyncExampleWPF`Název zadejte a pak zvolte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="cbe40-116">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="cbe40-117">Navrhněte jednoduchý WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="cbe40-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="cbe40-118">V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="cbe40-119">Pokud okno **Panel u nástrojů** není viditelné, otevřete nabídku **Zobrazení** a pak zvolte **Panel nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="cbe40-120">Přidejte **Button** button ovládací prvek a **textbox** ovládací prvek **mainwindow** okna.</span><span class="sxs-lookup"><span data-stu-id="cbe40-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="cbe40-121">Zvýrazněte ovládací prvek **TextBox** a v okně **Vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="cbe40-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="cbe40-122">Nastavte **Name** vlastnost Name `resultsTextBox`na .</span><span class="sxs-lookup"><span data-stu-id="cbe40-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="cbe40-123">Nastavte **Height** vlastnost 250.</span><span class="sxs-lookup"><span data-stu-id="cbe40-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="cbe40-124">Nastavte **width** vlastnost 500.</span><span class="sxs-lookup"><span data-stu-id="cbe40-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="cbe40-125">Na kartě **Text** zadejte neproporcionované písmo, například Lucida Console nebo Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="cbe40-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="cbe40-126">Zvýrazněte ovládací prvek **Button** a v okně **Vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="cbe40-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="cbe40-127">Nastavte **Name** vlastnost Name `startButton`na .</span><span class="sxs-lookup"><span data-stu-id="cbe40-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="cbe40-128">Změňte hodnotu vlastnosti **Content** z **tlačítka** na **start**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="cbe40-129">Umístěte textové pole a tlačítko tak, aby se obě zobrazily v okně **MainWindow.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="cbe40-130">Další informace o Návrháři WPF XAML naleznete [v tématu Vytvoření uživatelského uživatelského panelu pomocí návrháře XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cbe40-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="cbe40-131">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="cbe40-131">Add a reference</span></span>

1. <span data-ttu-id="cbe40-132">V **Průzkumníku řešení**zvýrazněte název projektu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="cbe40-133">Na řádku nabídek zvolte **Project** > **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="cbe40-134">Zobrazí se dialogové okno **Správce odkazů.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="cbe40-135">V horní části dialogového okna ověřte, zda projekt cílí na rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cbe40-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="cbe40-136">V kategorii **Sestavení** zvolte **Framework,** pokud ještě není vybrána.</span><span class="sxs-lookup"><span data-stu-id="cbe40-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="cbe40-137">V seznamu názvů zaškrtněte políčko **System.Net.Http.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="cbe40-138">Zvolte tlačítko **OK,** chcete-li zavřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="cbe40-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="cbe40-139">Přidat potřebné pomocí směrnic</span><span class="sxs-lookup"><span data-stu-id="cbe40-139">Add necessary using directives</span></span>

1. <span data-ttu-id="cbe40-140">V **Průzkumníku řešení**otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="cbe40-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="cbe40-141">Přidejte `using` následující direktivy v horní části souboru kódu, pokud ještě nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cbe40-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="cbe40-142">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="cbe40-142">Create a synchronous app</span></span>

1. <span data-ttu-id="cbe40-143">V okně návrhu MainWindow.xaml poklepejte na tlačítko `startButton_Click` **Start** a vytvořte obslužnou rutinu události v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cbe40-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="cbe40-144">V MainWindow.xaml.cs zkopírujte následující kód `startButton_Click`do těla :</span><span class="sxs-lookup"><span data-stu-id="cbe40-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="cbe40-145">Kód volá metodu, která `SumPageSizes`řídí aplikaci , a `startButton_Click`zobrazí zprávu při návratu ovládacího prvku do aplikace .</span><span class="sxs-lookup"><span data-stu-id="cbe40-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="cbe40-146">Kód synchronního řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="cbe40-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="cbe40-147">`SumPageSizes`, který získá seznam adres URL `SetUpURLList` webových `GetURLContents` stránek `DisplayResults` z a pak volání a zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cbe40-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="cbe40-148">`SetUpURLList`, který vytvoří a vrátí seznam webových adres.</span><span class="sxs-lookup"><span data-stu-id="cbe40-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="cbe40-149">`GetURLContents`, který stáhne obsah jednotlivých webových stránek a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="cbe40-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="cbe40-150">`DisplayResults`, který zobrazuje počet bajtů v poli bajtů pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cbe40-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="cbe40-151">Zkopírujte následující čtyři metody a vložte je pod obslužnou rutinu `startButton_Click` události v MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="cbe40-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290136.aspx",
            "https://msdn.microsoft.com/library/ee256749.aspx",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="cbe40-152">Testování synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="cbe40-152">Test the synchronous solution</span></span>

<span data-ttu-id="cbe40-153">Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="cbe40-154">Výstup, který se podobá následujícímu seznamu by se měl objevit:</span><span class="sxs-lookup"><span data-stu-id="cbe40-154">Output that resembles the following list should appear:</span></span>

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

<span data-ttu-id="cbe40-155">Všimněte si, že trvá několik sekund k zobrazení počty.</span><span class="sxs-lookup"><span data-stu-id="cbe40-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="cbe40-156">Během této doby je vlákno uživatelského rozhraní blokováno, zatímco čeká na požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="cbe40-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="cbe40-157">V důsledku toho nelze po výběru tlačítka **Start** přesunout, maximalizovat, minimalizovat nebo dokonce zavřít okno zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cbe40-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="cbe40-158">Tyto snahy se nezdaří, dokud se nezačnou objevovat počty bajtů.</span><span class="sxs-lookup"><span data-stu-id="cbe40-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="cbe40-159">Pokud web neodpovídá, nemáte žádný údaj o tom, který web selhal.</span><span class="sxs-lookup"><span data-stu-id="cbe40-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="cbe40-160">Je obtížné dokonce přestat čekat a zavřít program.</span><span class="sxs-lookup"><span data-stu-id="cbe40-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="cbe40-161">Převod obsahu GetURLNa na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="cbe40-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="cbe40-162">Chcete-li převést synchronní řešení na asynchronní řešení, je `GetURLContents` nejlepší místo <xref:System.Net.HttpWebRequest> pro <xref:System.Net.HttpWebRequest.GetResponse%2A> spuštění, <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> protože volání metody a metody jsou tam, kde aplikace přistupuje k webu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="cbe40-163">Rozhraní .NET Framework usnadňuje převod poskytnutím asynchronních verzí obou metod.</span><span class="sxs-lookup"><span data-stu-id="cbe40-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="cbe40-164">Další informace o metodách, `GetURLContents`které <xref:System.Net.WebRequest>se používají v , naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="cbe40-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cbe40-165">Při postupujte podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cbe40-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="cbe40-166">Můžete je ignorovat a pokračovat v návodu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="cbe40-167">Změňte metodu, která je volána ve třetím řádku z `GetURLContents` `GetResponse` na <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchronní metodu založenou na úlohách.</span><span class="sxs-lookup"><span data-stu-id="cbe40-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="cbe40-168">`GetResponseAsync`vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="cbe40-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="cbe40-169">V tomto případě má *proměnná vrácení úkolu*, `TResult`, typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="cbe40-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="cbe40-170">Úloha je příslibem vytvoření `WebResponse` skutečného objektu po stažení požadovaných dat a dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="cbe40-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="cbe40-171">Chcete-li `WebResponse` načíst hodnotu z úkolu, použijte `GetResponseAsync`operátor [await](../../../language-reference/operators/await.md) na volání , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="cbe40-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="cbe40-172">Operátor `await` pozastaví provádění aktuální metody `GetURLContents`, dokud nebude očekávaná úloha dokončena.</span><span class="sxs-lookup"><span data-stu-id="cbe40-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="cbe40-173">Do té doby ovládací prvek vrátí volajícímu aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="cbe40-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="cbe40-174">V tomto příkladu je `GetURLContents`aktuální metoda `SumPageSizes`a volající je .</span><span class="sxs-lookup"><span data-stu-id="cbe40-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="cbe40-175">Po dokončení úkolu je přislíbený `WebResponse` objekt vytvořen jako hodnota očekávaného úkolu `response`a přiřazen proměnné .</span><span class="sxs-lookup"><span data-stu-id="cbe40-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="cbe40-176">Předchozí příkaz lze rozdělit do následujících dvou příkazů objasnit, co se stane.</span><span class="sxs-lookup"><span data-stu-id="cbe40-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="cbe40-177">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="cbe40-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="cbe40-178">Potom await operátor je použita na `WebResponse` úlohu načíst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="cbe40-179">Pokud vaše asynchronní metoda má práci, která nezávisí na dokončení úkolu, metoda může pokračovat v této práci mezi těmito `await` dvěma příkazy, po volání asynchronní metody a před operátor je použita.</span><span class="sxs-lookup"><span data-stu-id="cbe40-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="cbe40-180">Příklady naleznete v tématu [Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="cbe40-180">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="cbe40-181">Vzhledem k `await` tomu, že jste přidali operátor v předchozím kroku, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cbe40-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="cbe40-182">Operátor lze použít pouze v metodách, které jsou označeny [asynchronním](../../../language-reference/keywords/async.md) modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="cbe40-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="cbe40-183">Při opakování kroků převodu, které mají `CopyTo` být nahrazeny `CopyToAsync`voláním, ignorujte chybu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="cbe40-184">Změňte název metody, která je <xref:System.IO.Stream.CopyToAsync%2A>volána na .</span><span class="sxs-lookup"><span data-stu-id="cbe40-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="cbe40-185">Metoda `CopyTo` `CopyToAsync` nebo zkopíruje bajty do `content`svého argumentu a nevrátí smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="cbe40-186">V synchronní verzi `CopyTo` volání je jednoduchý příkaz, který nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="cbe40-187">Asynchronní verze , `CopyToAsync`vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="cbe40-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="cbe40-188">Úloha funguje jako "Task(void)" a umožňuje, aby byla metoda očekávána.</span><span class="sxs-lookup"><span data-stu-id="cbe40-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="cbe40-189">Použít `Await` `await` nebo na `CopyToAsync`volání , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="cbe40-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="cbe40-190">Předchozí příkaz zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="cbe40-191">Vše, co zbývá `GetURLContents` udělat, je upravit podpis metody.</span><span class="sxs-lookup"><span data-stu-id="cbe40-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="cbe40-192">`await` Operátor můžete použít pouze v metodách, které jsou označeny [asynchronním](../../../language-reference/keywords/async.md) modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="cbe40-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="cbe40-193">Přidejte modifikátor pro označení metody jako *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="cbe40-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="cbe40-194">Návratový typ asynchronní metody <xref:System.Threading.Tasks.Task>může <xref:System.Threading.Tasks.Task%601>být `void` pouze , nebo v c#.</span><span class="sxs-lookup"><span data-stu-id="cbe40-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="cbe40-195">Obvykle návratový typ `void` se používá pouze v obslužné rutině asynchronní události, kde `void` je požadováno.</span><span class="sxs-lookup"><span data-stu-id="cbe40-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="cbe40-196">V ostatních případech `Task(T)` se použije, pokud má dokončená metoda [příkaz return,](../../../language-reference/keywords/return.md) který vrací hodnotu typu T, a použijete, `Task` pokud dokončená metoda nevrátí smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="cbe40-197">Návratový `Task` typ si můžete myslet jako "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="cbe40-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="cbe40-198">Další informace naleznete [v tématu Asynchronní návratové typy (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="cbe40-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="cbe40-199">Metoda `GetURLContents` má příkaz return a příkaz vrátí bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="cbe40-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="cbe40-200">Proto návratový typ asynchronní verze je Task(T), kde T je bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="cbe40-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="cbe40-201">Proveďte v podpisu metody následující změny:</span><span class="sxs-lookup"><span data-stu-id="cbe40-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="cbe40-202">Změňte návratový `Task<byte[]>`typ na .</span><span class="sxs-lookup"><span data-stu-id="cbe40-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="cbe40-203">Podle konvence asynchronní metody mají názvy, které končí v `GetURLContentsAsync`"Async", takže přejmenovat metodu .</span><span class="sxs-lookup"><span data-stu-id="cbe40-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="cbe40-204">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="cbe40-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="cbe40-205">S těmito několika změnami je dokončen převod `GetURLContents` na asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="cbe40-206">Převést SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="cbe40-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="cbe40-207">Opakujte kroky z předchozího postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="cbe40-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="cbe40-208">Nejprve změňte `GetURLContents` volání na asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="cbe40-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="cbe40-209">Změňte název metody, která je `GetURLContents` `GetURLContentsAsync`volána z do , pokud jste tak ještě neučinili.</span><span class="sxs-lookup"><span data-stu-id="cbe40-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="cbe40-210">Použít `await` pro úlohu, která `GetURLContentsAsync` se vrátí k získání hodnoty bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="cbe40-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="cbe40-211">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="cbe40-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="cbe40-212">Předchozí přiřazení zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="cbe40-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="cbe40-213">V podpisu metody proveďte následující změny:</span><span class="sxs-lookup"><span data-stu-id="cbe40-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="cbe40-214">Označte metodu modifikátorem. `async`</span><span class="sxs-lookup"><span data-stu-id="cbe40-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="cbe40-215">Přidejte "Async" do názvu metody.</span><span class="sxs-lookup"><span data-stu-id="cbe40-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="cbe40-216">Neexistuje žádná proměnná vrácení úkolu, `SumPageSizesAsync` T, tentokrát, protože nevrací hodnotu `return` pro T. (Metoda nemá žádný příkaz.) Metoda však musí `Task` vrátit a být ačekatelný.</span><span class="sxs-lookup"><span data-stu-id="cbe40-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="cbe40-217">Proto změňte návratový typ `void` metody `Task`z .</span><span class="sxs-lookup"><span data-stu-id="cbe40-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="cbe40-218">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="cbe40-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="cbe40-219">Převod `SumPageSizes` na `SumPageSizesAsync` do je dokončena.</span><span class="sxs-lookup"><span data-stu-id="cbe40-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="cbe40-220">Převést startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="cbe40-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="cbe40-221">V obslužné rutině události `SumPageSizes` změňte název volané metody z na `SumPageSizesAsync`, pokud jste tak ještě neučinili.</span><span class="sxs-lookup"><span data-stu-id="cbe40-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="cbe40-222">Protože `SumPageSizesAsync` je asynchronní metoda, změňte kód v obslužné rutině události a počkejte na výsledek.</span><span class="sxs-lookup"><span data-stu-id="cbe40-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="cbe40-223">Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="cbe40-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="cbe40-224">Volání vrátí `Task`, není `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="cbe40-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="cbe40-225">Stejně jako v předchozích postupech můžete převést volání pomocí jednoho příkazu nebo dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="cbe40-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="cbe40-226">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="cbe40-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="cbe40-227">Chcete-li zabránit náhodnému opětovnému návratu do operace, přidejte do horní části `startButton_Click` následující příkaz a zakažte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="cbe40-228">Tlačítko můžete znovu povolit na konci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cbe40-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="cbe40-229">Další informace o reentrancy naleznete v [tématu Zpracování reentrancy v asynchronních aplikacích (C#)](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="cbe40-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="cbe40-230">Nakonec přidejte `async` modifikátor do deklarace tak, `SumPagSizesAsync`aby obslužná rutina události může čekat .</span><span class="sxs-lookup"><span data-stu-id="cbe40-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="cbe40-231">Obvykle názvy obslužné rutiny událostí se nezmění.</span><span class="sxs-lookup"><span data-stu-id="cbe40-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="cbe40-232">Návratový typ se nezmění `Task` na protože obslužné rutiny událostí musí vrátit `void`.</span><span class="sxs-lookup"><span data-stu-id="cbe40-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="cbe40-233">Převod projektu ze synchronního na asynchronní zpracování je dokončen.</span><span class="sxs-lookup"><span data-stu-id="cbe40-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="cbe40-234">Testování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="cbe40-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="cbe40-235">Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="cbe40-236">Výstup, který se podobá výstupu synchronní řešení by se měla zobrazit.</span><span class="sxs-lookup"><span data-stu-id="cbe40-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="cbe40-237">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="cbe40-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="cbe40-238">Výsledky nedochází všechny ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="cbe40-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="cbe40-239">Oba programy například obsahují `startButton_Click` řádek, ve které textové pole vymaže.</span><span class="sxs-lookup"><span data-stu-id="cbe40-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="cbe40-240">Záměrem je vymazat textové pole mezi spuštěními, pokud zvolíte tlačítko **Start** podruhé, po jedné sadě výsledků se objevil.</span><span class="sxs-lookup"><span data-stu-id="cbe40-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="cbe40-241">V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, když jsou dokončeny soubory ke stažení a vlákno uživatelského rozhraní může dělat jinou práci.</span><span class="sxs-lookup"><span data-stu-id="cbe40-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="cbe40-242">V asynchronní verzi se textové pole vymaže ihned po výběru tlačítka **Start.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="cbe40-243">A co je nejdůležitější, vlákno uživatelského rozhraní není blokován během stahování.</span><span class="sxs-lookup"><span data-stu-id="cbe40-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="cbe40-244">Okno můžete přesunout nebo změnit velikost během stahování, počítání a zobrazování webových prostředků.</span><span class="sxs-lookup"><span data-stu-id="cbe40-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="cbe40-245">Pokud je jeden z webů pomalý nebo nereaguje, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v červeném poli v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="cbe40-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="cbe40-246">Nahradit metodu GetURLContentsAsync metodou rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cbe40-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="cbe40-247">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronních metod, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="cbe40-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="cbe40-248">Jeden z <xref:System.Net.Http.HttpClient> nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>metoda , dělá přesně to, co potřebujete pro tento návod.</span><span class="sxs-lookup"><span data-stu-id="cbe40-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="cbe40-249">Můžete jej použít namísto metody, kterou jste vytvořili `GetURLContentsAsync` v dřívější mši.</span><span class="sxs-lookup"><span data-stu-id="cbe40-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="cbe40-250">Prvním krokem je vytvoření `HttpClient` objektu `SumPageSizesAsync`v metodě .</span><span class="sxs-lookup"><span data-stu-id="cbe40-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="cbe40-251">Na začátek metody přidejte následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="cbe40-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="cbe40-252">V `SumPageSizesAsync,` nahradit volání `GetURLContentsAsync` metody volání metody. `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="cbe40-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="cbe40-253">Odeberte nebo `GetURLContentsAsync` okomentovat metodu, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="cbe40-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="cbe40-254">Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="cbe40-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="cbe40-255">Chování této verze projektu by měla odpovídat chování, které popisuje postup "Chcete-li otestovat asynchronní řešení", ale s ještě menší námahou od vás.</span><span class="sxs-lookup"><span data-stu-id="cbe40-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="cbe40-256">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="cbe40-256">Example code</span></span>

<span data-ttu-id="cbe40-257">Následující kód obsahuje úplný příklad převodu ze synchronního na asynchronní řešení pomocí `GetURLContentsAsync` asynchronní metody, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="cbe40-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="cbe40-258">Všimněte si, že se silně podobá původnímu synchronnímu řešení.</span><span class="sxs-lookup"><span data-stu-id="cbe40-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

<span data-ttu-id="cbe40-259">Následující kód obsahuje úplný příklad řešení, `HttpClient` které `GetByteArrayAsync`používá metodu .</span><span class="sxs-lookup"><span data-stu-id="cbe40-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="cbe40-260">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbe40-260">See also</span></span>

- <span data-ttu-id="cbe40-261">[Ukázka asynchronní: Přístup k webovému návodu (C# a Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="cbe40-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="cbe40-262">async</span><span class="sxs-lookup"><span data-stu-id="cbe40-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="cbe40-263">await</span><span class="sxs-lookup"><span data-stu-id="cbe40-263">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="cbe40-264">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe40-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="cbe40-265">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe40-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="cbe40-266">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="cbe40-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="cbe40-267">Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe40-267">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="cbe40-268">Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)</span><span class="sxs-lookup"><span data-stu-id="cbe40-268">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
