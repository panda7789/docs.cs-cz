---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 0c80bb079e66a56d6bbc30ba43269aee7ac4ab5b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168362"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="ca873-102">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ca873-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="ca873-103">Asynchronní programy můžete napsat snadněji a intuitivnější pomocí funkcí Async/await.</span><span class="sxs-lookup"><span data-stu-id="ca873-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="ca873-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kód, a nechat kompilátor zpracovávat obtížné funkce zpětného volání a pokračování, které obvykle zahrnuje asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="ca873-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="ca873-105">Další informace o funkci Async naleznete v tématu [asynchronní programování s Async a awaitC#()](./index.md).</span><span class="sxs-lookup"><span data-stu-id="ca873-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="ca873-106">Tento návod začíná s aplikací synchronní Windows Presentation Foundation (WPF), která sečte počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="ca873-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="ca873-107">Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="ca873-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="ca873-108">Pokud nechcete sestavovat aplikace sami, můžete si stáhnout [asynchronní vzorek: Přístup k webovému návoduC# (a Visual Basic](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)).</span><span class="sxs-lookup"><span data-stu-id="ca873-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="ca873-109">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ca873-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="ca873-110">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="ca873-110">Create a WPF application</span></span>

1. <span data-ttu-id="ca873-111">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca873-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="ca873-112">V panelu nabídky zvolte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ca873-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="ca873-113">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ca873-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ca873-114">V podokně **Nainstalované šablony** zvolte možnost Visual C#a v seznamu typů projektů zvolte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="ca873-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="ca873-115">Do textového pole **název** zadejte `AsyncExampleWPF`a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="ca873-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="ca873-116">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="ca873-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="ca873-117">Návrh jednoduchého MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="ca873-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="ca873-118">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="ca873-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="ca873-119">Pokud není okno **panelu nástrojů** viditelné, otevřete nabídku **zobrazení** a zvolte možnost **Sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="ca873-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="ca873-120">Přidejte ovládací prvek **tlačítko** a ovládací prvek **TextBox** do okna **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="ca873-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="ca873-121">Zvýrazněte ovládací prvek **TextBox** a v okně **vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ca873-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="ca873-122">Nastavte vlastnost **název** na `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="ca873-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="ca873-123">Nastavte vlastnost **Height** na 250.</span><span class="sxs-lookup"><span data-stu-id="ca873-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="ca873-124">Nastavte vlastnost **Width** na 500.</span><span class="sxs-lookup"><span data-stu-id="ca873-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="ca873-125">Na kartě **text** zadejte Neproporcionální písmo, například Lucida konzolu nebo globální neproporcionální.</span><span class="sxs-lookup"><span data-stu-id="ca873-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="ca873-126">Zvýrazněte ovládací prvek **tlačítko** a v okně **vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ca873-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="ca873-127">Nastavte vlastnost **název** na `startButton`.</span><span class="sxs-lookup"><span data-stu-id="ca873-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="ca873-128">Změňte hodnotu vlastnosti **obsah** z **tlačítka** na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="ca873-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="ca873-129">Umístěte textové pole a tlačítko tak, aby se obě zobrazily v okně **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="ca873-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="ca873-130">Další informace o Návrhář XAML WPF naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ca873-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="ca873-131">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="ca873-131">Add a reference</span></span>

1. <span data-ttu-id="ca873-132">V **Průzkumník řešení**zvýrazněte název svého projektu.</span><span class="sxs-lookup"><span data-stu-id="ca873-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="ca873-133">Na panelu nabídek vyberte **projekt** > **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="ca873-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="ca873-134">Zobrazí se dialogové okno **Správce odkazů** .</span><span class="sxs-lookup"><span data-stu-id="ca873-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="ca873-135">V horní části dialogového okna ověřte, zda je projekt cílen na .NET Framework 4,5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="ca873-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="ca873-136">V kategorii **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.</span><span class="sxs-lookup"><span data-stu-id="ca873-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="ca873-137">V seznamu názvů vyberte zaškrtávací políčko **System .NET. http** .</span><span class="sxs-lookup"><span data-stu-id="ca873-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="ca873-138">Kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ca873-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="ca873-139">Přidat nezbytné direktivy using</span><span class="sxs-lookup"><span data-stu-id="ca873-139">Add necessary using directives</span></span>

1. <span data-ttu-id="ca873-140">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow.XAML.cs a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="ca873-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="ca873-141">Přidejte následující `using` direktivy v horní části souboru kódu, pokud již nejsou přítomny.</span><span class="sxs-lookup"><span data-stu-id="ca873-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="ca873-142">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="ca873-142">Create a synchronous app</span></span>

1. <span data-ttu-id="ca873-143">V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko **Start** a vytvořte `startButton_Click` obslužnou rutinu události v MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="ca873-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="ca873-144">V MainWindow.xaml.cs zkopírujte následující kód do těla `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="ca873-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="ca873-145">Kód volá metodu, která řídí aplikaci, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí do. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="ca873-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="ca873-146">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="ca873-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="ca873-147">`SumPageSizes`, který získá seznam adres URL webových stránek z `SetUpURLList` a potom zavolá `DisplayResults` `GetURLContents` a zpracuje každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ca873-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="ca873-148">`SetUpURLList`, který provede a vrátí seznam webových adres.</span><span class="sxs-lookup"><span data-stu-id="ca873-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="ca873-149">`GetURLContents`, který stáhne obsah jednotlivých webů a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="ca873-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="ca873-150">`DisplayResults`zobrazuje počet bajtů v bajtovém poli pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ca873-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="ca873-151">Zkopírujte následující čtyři metody a pak je vložte pod `startButton_Click` obslužnou rutinu události v MainWindow.XAML.cs:</span><span class="sxs-lookup"><span data-stu-id="ca873-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="ca873-152">Test synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="ca873-152">Test the synchronous solution</span></span>

<span data-ttu-id="ca873-153">Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="ca873-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="ca873-154">Měl by se zobrazit výstup, který se podobá následujícímu seznamu:</span><span class="sxs-lookup"><span data-stu-id="ca873-154">Output that resembles the following list should appear:</span></span>

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

<span data-ttu-id="ca873-155">Všimněte si, že pro zobrazení počtů trvá několik sekund.</span><span class="sxs-lookup"><span data-stu-id="ca873-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="ca873-156">Během této doby je vlákno uživatelského rozhraní blokované při čekání na stažení požadovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca873-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="ca873-157">V důsledku toho nebudete moct okno zobrazení po kliknutí na tlačítko **Start** přesunout, maximalizovat, minimalizovat ani ani zavřít.</span><span class="sxs-lookup"><span data-stu-id="ca873-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="ca873-158">Tato snaha selže, dokud se nezobrazují počty bajtů.</span><span class="sxs-lookup"><span data-stu-id="ca873-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="ca873-159">Pokud web neodpovídá, nemusíte mít žádné informace o tom, který web selhal.</span><span class="sxs-lookup"><span data-stu-id="ca873-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="ca873-160">Je obtížné dokonce ukončit čekání a ukončit program.</span><span class="sxs-lookup"><span data-stu-id="ca873-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="ca873-161">Převést GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="ca873-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="ca873-162">Chcete-li převést synchronní řešení na asynchronní řešení, je nejlepší místo `GetURLContents` , ve kterém je spuštěno, protože volání <xref:System.Net.HttpWebRequest> metody <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metody <xref:System.IO.Stream.CopyTo%2A> jsou místo, kde aplikace přistupuje k webu .</span><span class="sxs-lookup"><span data-stu-id="ca873-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="ca873-163">.NET Framework usnadňuje převod tím, že poskytuje asynchronní verze obou metod.</span><span class="sxs-lookup"><span data-stu-id="ca873-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="ca873-164">Další informace o metodách, které jsou používány v `GetURLContents`nástroji, <xref:System.Net.WebRequest>naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="ca873-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca873-165">Při provedení kroků v tomto návodu se zobrazí několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ca873-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="ca873-166">Můžete je ignorovat a pokračovat v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="ca873-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="ca873-167">Změňte metodu, která je volána na třetím řádku `GetURLContents` od `GetResponse` do asynchronní metody založené <xref:System.Net.WebRequest.GetResponseAsync%2A> na úlohách.</span><span class="sxs-lookup"><span data-stu-id="ca873-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="ca873-168">`GetResponseAsync`<xref:System.Threading.Tasks.Task%601>vrátí.</span><span class="sxs-lookup"><span data-stu-id="ca873-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ca873-169">V tomto případě má `TResult` *vrácená proměnná úlohy*typ. <xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="ca873-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ca873-170">Úkol je příslib k vytvoření skutečného `WebResponse` objektu po stažení požadovaných dat a dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="ca873-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="ca873-171">Chcete-li `WebResponse` načíst hodnotu z úkolu, použijte operátor [await](../../../language-reference/operators/await.md) `GetResponseAsync`pro volání metody, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="ca873-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="ca873-172">Operátor pozastaví provádění aktuální `GetURLContents`metody, dokud není dokončen očekávaný úkol. `await`</span><span class="sxs-lookup"><span data-stu-id="ca873-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="ca873-173">Mezitím se ovládací prvek vrátí volajícímu aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="ca873-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="ca873-174">V tomto příkladu je `GetURLContents`aktuální metoda a volající je. `SumPageSizes`</span><span class="sxs-lookup"><span data-stu-id="ca873-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="ca873-175">Po dokončení úkolu je přislíbený `WebResponse` objekt vytvořen jako hodnota očekávaného úkolu a přiřazený k proměnné. `response`</span><span class="sxs-lookup"><span data-stu-id="ca873-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="ca873-176">Předchozí příkaz může být rozdělen do následujících dvou příkazů k objasnění toho, co se stane.</span><span class="sxs-lookup"><span data-stu-id="ca873-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="ca873-177">Volání `webReq.GetResponseAsync` funkcevrátí`Task<WebResponse>`nebo. `Task(Of WebResponse)`</span><span class="sxs-lookup"><span data-stu-id="ca873-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="ca873-178">Pak se pro úlohu použije operátor await, aby se načetla `WebResponse` hodnota.</span><span class="sxs-lookup"><span data-stu-id="ca873-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="ca873-179">Pokud vaše asynchronní metoda funguje tak, že nezávisí na dokončení úlohy, může metoda pokračovat v práci s těmito dvěma příkazy po volání asynchronní metody a před `await` použitím operátoru.</span><span class="sxs-lookup"><span data-stu-id="ca873-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="ca873-180">Příklady naleznete v tématu [How to: Paralelní provádění více webových požadavků s použitím modifikátoru Async a operátoru](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) await [(C#) a postupy: Pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)rozšíříte asynchronní návod.</span><span class="sxs-lookup"><span data-stu-id="ca873-180">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="ca873-181">Protože jste přidali `await` operátor v předchozím kroku, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ca873-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="ca873-182">Operátor lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ca873-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ca873-183">Ignorujte chybu při opakování kroků převodu k nahrazení volání `CopyTo` `CopyToAsync`voláním metody.</span><span class="sxs-lookup"><span data-stu-id="ca873-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="ca873-184">Změňte název metody, na <xref:System.IO.Stream.CopyToAsync%2A>kterou se volá.</span><span class="sxs-lookup"><span data-stu-id="ca873-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="ca873-185">Metoda `CopyTo` `content`nebo `CopyToAsync` kopíruje bajty do svého argumentu, a nevrací smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca873-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="ca873-186">V synchronní verzi je volání na `CopyTo` jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca873-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="ca873-187">Asynchronní verze, `CopyToAsync`vrátí a <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="ca873-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="ca873-188">Úkol funguje jako "Task (void)" a umožňuje, aby metoda byla očekávána.</span><span class="sxs-lookup"><span data-stu-id="ca873-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="ca873-189">Použijte `Await` nebo `await` na volání`CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="ca873-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="ca873-190">Předchozí příkaz zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="ca873-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="ca873-191">Vše, co je potřeba udělat v `GetURLContents` nástroji, je úprava signatury metody.</span><span class="sxs-lookup"><span data-stu-id="ca873-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="ca873-192">`await` Operátor lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ca873-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ca873-193">Přidejte modifikátor k označení metody jako *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="ca873-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="ca873-194">Návratový typ asynchronní <xref:System.Threading.Tasks.Task>metody může být pouze, <xref:System.Threading.Tasks.Task%601>, nebo `void` v. C#</span><span class="sxs-lookup"><span data-stu-id="ca873-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="ca873-195">Návratový typ `void` se obvykle používá pouze v asynchronní obslužné rutině události, kde je to `void` požadováno.</span><span class="sxs-lookup"><span data-stu-id="ca873-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="ca873-196">V ostatních případech použijete `Task(T)` , pokud má metoda Completed [návratový](../../../language-reference/keywords/return.md) příkaz, který vrací hodnotu typu T, a použijete `Task` , pokud metoda Completed nevrátí smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca873-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="ca873-197">`Task` Návratový typ si můžete představit jako "Task (void)".</span><span class="sxs-lookup"><span data-stu-id="ca873-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="ca873-198">Další informace naleznete v tématu [Async Return TypesC#()](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ca873-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="ca873-199">Metoda `GetURLContents` obsahuje příkaz return a příkaz vrátí bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="ca873-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="ca873-200">Proto návratový typ asynchronní verze je Task (T), kde T je pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="ca873-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="ca873-201">V signatuře metody proveďte následující změny:</span><span class="sxs-lookup"><span data-stu-id="ca873-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="ca873-202">Změňte návratový typ na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="ca873-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="ca873-203">Podle konvence mají asynchronní metody názvy, které končí na "Async", proto přejmenujte metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="ca873-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="ca873-204">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="ca873-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="ca873-205">U těchto několika změn je převod `GetURLContents` na asynchronní metodu dokončen.</span><span class="sxs-lookup"><span data-stu-id="ca873-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="ca873-206">Převést SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="ca873-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="ca873-207">Opakujte kroky z předchozího postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="ca873-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="ca873-208">Nejprve změňte volání `GetURLContents` na asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="ca873-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="ca873-209">Změňte název metody, která je volána z `GetURLContents` na `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="ca873-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="ca873-210">Použijte `await` u úlohy, která `GetURLContentsAsync` se vrátí k získání hodnoty bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="ca873-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="ca873-211">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="ca873-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="ca873-212">Předchozí přiřazení zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="ca873-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="ca873-213">V signatuře metody proveďte následující změny:</span><span class="sxs-lookup"><span data-stu-id="ca873-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="ca873-214">Označte metodu `async` modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="ca873-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="ca873-215">Do názvu metody přidejte "Async".</span><span class="sxs-lookup"><span data-stu-id="ca873-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="ca873-216">V tuto chvíli neexistuje žádná vrácená proměnná úlohy, t, protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metoda nemá žádný `return` příkaz.) Metoda však musí vracet `Task` , aby bylo možné očekávat.</span><span class="sxs-lookup"><span data-stu-id="ca873-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="ca873-217">Proto změňte návratový typ metody z `void` na. `Task`</span><span class="sxs-lookup"><span data-stu-id="ca873-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="ca873-218">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="ca873-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="ca873-219">Převod `SumPageSizes` na`SumPageSizesAsync` je dokončen.</span><span class="sxs-lookup"><span data-stu-id="ca873-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="ca873-220">Převést startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="ca873-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="ca873-221">V obslužné rutině události změňte název volané metody z `SumPageSizes` na `SumPageSizesAsync`, pokud jste to ještě neudělali.</span><span class="sxs-lookup"><span data-stu-id="ca873-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="ca873-222">Vzhledem `SumPageSizesAsync` k tomu, že je asynchronní metoda, změňte kód v obslužné rutině události tak, aby čekal na výsledek.</span><span class="sxs-lookup"><span data-stu-id="ca873-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="ca873-223">Volání `SumPageSizesAsync` zrcadlí `CopyToAsync` volání do v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="ca873-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="ca873-224">Volání vrátí a `Task`, `Task(T)`nikoli.</span><span class="sxs-lookup"><span data-stu-id="ca873-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="ca873-225">Stejně jako v předchozích postupech lze volání převést pomocí jednoho příkazu nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="ca873-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="ca873-226">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="ca873-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="ca873-227">Chcete-li zabránit nechtěnému znovu zadat operaci, přidejte následující příkaz v horní části `startButton_Click` , čímž zakážete tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="ca873-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="ca873-228">Tlačítko lze znovu povolit na konci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ca873-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="ca873-229">Další informace o Vícenásobný přístup najdete v tématu [zpracování Vícenásobný přístup v asynchronních aplikacíchC#()](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ca873-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="ca873-230">Nakonec přidejte `async` modifikátor do deklarace tak, aby mohla obslužná rutina události očekávat `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="ca873-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="ca873-231">Názvy obslužných rutin událostí se typicky nemění.</span><span class="sxs-lookup"><span data-stu-id="ca873-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="ca873-232">Návratový typ se nezměnil na `Task` , protože obslužné rutiny `void`událostí musí vracet.</span><span class="sxs-lookup"><span data-stu-id="ca873-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="ca873-233">Převod projektu z synchronního na asynchronní zpracování je dokončen.</span><span class="sxs-lookup"><span data-stu-id="ca873-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="ca873-234">Testování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="ca873-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="ca873-235">Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="ca873-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="ca873-236">Měl by se zobrazit výstup, který se podobá výstupu synchronního řešení.</span><span class="sxs-lookup"><span data-stu-id="ca873-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="ca873-237">Všimněte si ale následujících rozdílů.</span><span class="sxs-lookup"><span data-stu-id="ca873-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="ca873-238">Po dokončení zpracování se všechny výsledky neprojeví ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="ca873-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="ca873-239">Například oba programy obsahují řádek `startButton_Click` , který vymaže textové pole.</span><span class="sxs-lookup"><span data-stu-id="ca873-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="ca873-240">Záměrem je vymazat textové pole mezi spuštěním, pokud zvolíte tlačítko **Spustit** pro druhý čas, poté, co se objeví jedna sada výsledků.</span><span class="sxs-lookup"><span data-stu-id="ca873-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="ca873-241">V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, po dokončení stahování a vlákno uživatelského rozhraní je volné pro další práci.</span><span class="sxs-lookup"><span data-stu-id="ca873-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="ca873-242">V asynchronní verzi se textové pole vymaže ihned po kliknutí na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="ca873-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="ca873-243">Ve většině případů není vlákno UI během stahování zablokované.</span><span class="sxs-lookup"><span data-stu-id="ca873-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="ca873-244">Během stahování, počítání a zobrazování webových prostředků můžete okno přesunout nebo změnit jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="ca873-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="ca873-245">Pokud je jeden z webů pomalý nebo neodpovídá, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v poli červené v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="ca873-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="ca873-246">Nahraďte metodu GetURLContentsAsync metodou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca873-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="ca873-247">.NET Framework 4,5 poskytuje mnoho asynchronních metod, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="ca873-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="ca873-248">Jedna z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, dělá přesně to, co potřebujete pro tento návod.</span><span class="sxs-lookup"><span data-stu-id="ca873-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="ca873-249">Místo `GetURLContentsAsync` metody, kterou jste vytvořili v předchozím postupu, ji můžete použít.</span><span class="sxs-lookup"><span data-stu-id="ca873-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="ca873-250">Prvním krokem je vytvoření `HttpClient` objektu v metodě. `SumPageSizesAsync`</span><span class="sxs-lookup"><span data-stu-id="ca873-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="ca873-251">Přidejte následující deklaraci na začátek metody.</span><span class="sxs-lookup"><span data-stu-id="ca873-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="ca873-252">V `SumPageSizesAsync,` části nahraďte volání `GetURLContentsAsync` metody voláním `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="ca873-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="ca873-253">Odeberte nebo zakomentujte `GetURLContentsAsync` metodu, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="ca873-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="ca873-254">Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="ca873-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="ca873-255">Chování této verze projektu by se mělo shodovat s chováním, které popisuje postup testování asynchronního řešení, ale s ještě menším úsilím.</span><span class="sxs-lookup"><span data-stu-id="ca873-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="ca873-256">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="ca873-256">Example code</span></span>

<span data-ttu-id="ca873-257">Následující kód obsahuje úplný příklad převodu z synchronního na asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metody, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="ca873-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="ca873-258">Všimněte si, že se silně podobá původnímu synchronnímu řešení.</span><span class="sxs-lookup"><span data-stu-id="ca873-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

<span data-ttu-id="ca873-259">Následující kód obsahuje úplný příklad řešení, které používá `HttpClient` metodu,. `GetByteArrayAsync`</span><span class="sxs-lookup"><span data-stu-id="ca873-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ca873-260">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca873-260">See also</span></span>

- [<span data-ttu-id="ca873-261">Asynchronní Ukázka: Přístup k webovému návoduC# (a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca873-261">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="ca873-262">async</span><span class="sxs-lookup"><span data-stu-id="ca873-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="ca873-263">await</span><span class="sxs-lookup"><span data-stu-id="ca873-263">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="ca873-264">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="ca873-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="ca873-265">Asynchronní návratové typyC#()</span><span class="sxs-lookup"><span data-stu-id="ca873-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="ca873-266">Asynchronní programování založené na úlohách (klepnutím)</span><span class="sxs-lookup"><span data-stu-id="ca873-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="ca873-267">Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).</span><span class="sxs-lookup"><span data-stu-id="ca873-267">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="ca873-268">Postupy: Paralelní provádění více webových požadavků s použitím modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ca873-268">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
