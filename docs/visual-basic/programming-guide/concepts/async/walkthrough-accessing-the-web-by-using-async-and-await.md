---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 7f649f1f16da545c4587f0ed76b8f1a443ee8744
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715844"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="4205b-102">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="4205b-103">Asynchronní programy můžete napsat snadněji a intuitivnější pomocí funkcí Async/await.</span><span class="sxs-lookup"><span data-stu-id="4205b-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="4205b-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kód, a nechat kompilátor zpracovávat obtížné funkce zpětného volání a pokračování, které obvykle zahrnuje asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="4205b-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="4205b-105">Další informace o funkci Async naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4205b-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="4205b-106">Tento návod začíná s aplikací synchronní Windows Presentation Foundation (WPF), která sečte počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="4205b-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="4205b-107">Návod pak převede aplikaci na asynchronní řešení pomocí nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="4205b-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="4205b-108">Pokud nechcete sestavovat aplikace sami, můžete si stáhnout "asynchronní vzorek: přístup k webovému návodu (C# a Visual Basic)" z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="4205b-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="4205b-109">V tomto návodu provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="4205b-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="4205b-110">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="4205b-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="4205b-111">Návrh jednoduchého MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="4205b-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="4205b-112">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="4205b-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="4205b-113">Přidat nezbytné příkazy Imports</span><span class="sxs-lookup"><span data-stu-id="4205b-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="4205b-114">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="4205b-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="4205b-115">Test synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="4205b-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="4205b-116">Převést GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="4205b-117">Převést SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="4205b-118">Převést startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="4205b-119">Testování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="4205b-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="4205b-120">Nahraďte metodu GetURLContentsAsync metodou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4205b-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="4205b-121">Kompletní asynchronní příklad najdete v části [příklad](#example) .</span><span class="sxs-lookup"><span data-stu-id="4205b-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4205b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4205b-122">Prerequisites</span></span>

<span data-ttu-id="4205b-123">V počítači musí být nainstalována aplikace Visual Studio 2012 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4205b-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="4205b-124">Další informace najdete na stránce [soubory ke stažení](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4205b-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="4205b-125">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="4205b-125">Create a WPF application</span></span>

1. <span data-ttu-id="4205b-126">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4205b-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="4205b-127">Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="4205b-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="4205b-128">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="4205b-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="4205b-129">V podokně **Nainstalované šablony** zvolte možnost Visual Basic a v seznamu typů projektů zvolte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="4205b-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="4205b-130">Do textového pole **název** zadejte `AsyncExampleWPF`a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="4205b-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="4205b-131">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="4205b-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="4205b-132">Návrh jednoduchého MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="4205b-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="4205b-133">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="4205b-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="4205b-134">Pokud není okno **panelu nástrojů** viditelné, otevřete nabídku **zobrazení** a zvolte možnost **Sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="4205b-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="4205b-135">Přidejte ovládací prvek **tlačítko** a ovládací prvek **TextBox** do okna **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="4205b-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="4205b-136">Zvýrazněte ovládací prvek **TextBox** a v okně **vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4205b-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="4205b-137">Nastavte vlastnost **název** na `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="4205b-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="4205b-138">Nastavte vlastnost **Height** na 250.</span><span class="sxs-lookup"><span data-stu-id="4205b-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="4205b-139">Nastavte vlastnost **Width** na 500.</span><span class="sxs-lookup"><span data-stu-id="4205b-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="4205b-140">Na kartě **text** zadejte Neproporcionální písmo, například Lucida konzolu nebo globální neproporcionální.</span><span class="sxs-lookup"><span data-stu-id="4205b-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="4205b-141">Zvýrazněte ovládací prvek **tlačítko** a v okně **vlastnosti** nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4205b-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="4205b-142">Nastavte vlastnost **název** na `startButton`.</span><span class="sxs-lookup"><span data-stu-id="4205b-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="4205b-143">Změňte hodnotu vlastnosti **obsah** z **tlačítka** na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="4205b-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="4205b-144">Umístěte textové pole a tlačítko tak, aby se obě zobrazily v okně **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="4205b-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="4205b-145">Další informace o Návrhář XAML WPF naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4205b-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="4205b-146">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="4205b-146">Add a reference</span></span>

1. <span data-ttu-id="4205b-147">V **Průzkumník řešení**zvýrazněte název svého projektu.</span><span class="sxs-lookup"><span data-stu-id="4205b-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="4205b-148">V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="4205b-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="4205b-149">Zobrazí se dialogové okno **Správce odkazů** .</span><span class="sxs-lookup"><span data-stu-id="4205b-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="4205b-150">V horní části dialogového okna ověřte, zda je projekt cílen na .NET Framework 4,5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="4205b-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="4205b-151">V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.</span><span class="sxs-lookup"><span data-stu-id="4205b-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="4205b-152">V seznamu názvů vyberte zaškrtávací políčko **System .NET. http** .</span><span class="sxs-lookup"><span data-stu-id="4205b-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="4205b-153">Kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4205b-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="4205b-154">Přidat nezbytné příkazy Imports</span><span class="sxs-lookup"><span data-stu-id="4205b-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="4205b-155">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="4205b-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="4205b-156">Přidejte následující příkazy `Imports` v horní části souboru kódu, pokud již nejsou přítomny.</span><span class="sxs-lookup"><span data-stu-id="4205b-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="4205b-157">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="4205b-157">Create a synchronous application</span></span>

1. <span data-ttu-id="4205b-158">V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko **Start** a vytvořte obslužnou rutinu události `startButton_Click` v souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="4205b-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="4205b-159">V souboru MainWindow. XAML. vb zkopírujte následující kód do textu `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="4205b-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="4205b-160">Kód volá metodu, která aplikaci zařídí, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4205b-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="4205b-161">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="4205b-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="4205b-162">`SumPageSizes`, který získá seznam adres URL webových stránek z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` ke zpracování každé adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4205b-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="4205b-163">`SetUpURLList`, která vytvoří a vrátí seznam webových adres.</span><span class="sxs-lookup"><span data-stu-id="4205b-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="4205b-164">`GetURLContents`, který stáhne obsah jednotlivých webů a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="4205b-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="4205b-165">`DisplayResults`, která zobrazuje počet bajtů v bajtovém poli pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="4205b-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="4205b-166">Zkopírujte následující čtyři metody a pak je vložte pod obslužnou rutinu události `startButton_Click` v souboru MainWindow. XAML. vb:</span><span class="sxs-lookup"><span data-stu-id="4205b-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="4205b-167">Test synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="4205b-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="4205b-168">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="4205b-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="4205b-169">Měl by se zobrazit výstup, který se podobá následujícímu seznamu:</span><span class="sxs-lookup"><span data-stu-id="4205b-169">Output that resembles the following list should appear:</span></span>

    ```console
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

    <span data-ttu-id="4205b-170">Všimněte si, že pro zobrazení počtů trvá několik sekund.</span><span class="sxs-lookup"><span data-stu-id="4205b-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="4205b-171">Během této doby je vlákno uživatelského rozhraní blokované při čekání na stažení požadovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="4205b-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="4205b-172">V důsledku toho nebudete moct okno zobrazení po kliknutí na tlačítko **Start** přesunout, maximalizovat, minimalizovat ani ani zavřít.</span><span class="sxs-lookup"><span data-stu-id="4205b-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="4205b-173">Tato snaha selže, dokud se nezobrazují počty bajtů.</span><span class="sxs-lookup"><span data-stu-id="4205b-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="4205b-174">Pokud web neodpovídá, nemusíte mít žádné informace o tom, který web selhal.</span><span class="sxs-lookup"><span data-stu-id="4205b-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="4205b-175">Je obtížné dokonce ukončit čekání a ukončit program.</span><span class="sxs-lookup"><span data-stu-id="4205b-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="4205b-176">Převést GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="4205b-177">Chcete-li převést synchronní řešení na asynchronní řešení, je nejlepším místem, kde začít, je `GetURLContents`, protože volání metody <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> a metody <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> jsou, kde aplikace přistupuje k webu.</span><span class="sxs-lookup"><span data-stu-id="4205b-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="4205b-178">.NET Framework usnadňuje převod tím, že poskytuje asynchronní verze obou metod.</span><span class="sxs-lookup"><span data-stu-id="4205b-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="4205b-179">Další informace o metodách, které se používají v `GetURLContents`, najdete v tématu <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="4205b-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4205b-180">Při provedení kroků v tomto návodu se zobrazí několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4205b-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="4205b-181">Můžete je ignorovat a pokračovat v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="4205b-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="4205b-182">Změňte metodu, která je volána ve třetí řádce `GetURLContents` z `GetResponse` na asynchronní metodu <xref:System.Net.WebRequest.GetResponseAsync%2A> založenou na úlohách.</span><span class="sxs-lookup"><span data-stu-id="4205b-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="4205b-183">`GetResponseAsync` vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4205b-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4205b-184">V takovém případě má *vrácená proměnná úlohy*`TResult`typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="4205b-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="4205b-185">Úkol je příslib k vytvoření skutečného `WebResponse` objektu po stažení požadovaných dat a dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="4205b-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="4205b-186">Pro načtení `WebResponse` hodnoty z úlohy, použijte operátor [await](../../../../visual-basic/language-reference/operators/await-operator.md) pro volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="4205b-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="4205b-187">Operátor `Await` pozastaví provádění aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="4205b-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="4205b-188">Mezitím se ovládací prvek vrátí volajícímu aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="4205b-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="4205b-189">V tomto příkladu je aktuální metoda `GetURLContents`a volající je `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="4205b-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="4205b-190">Po dokončení úkolu se přislíbený `WebResponse` objekt vytvoří jako hodnota očekávaného úkolu a přiřazený k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="4205b-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="4205b-191">Předchozí příkaz může být rozdělen do následujících dvou příkazů k objasnění toho, co se stane.</span><span class="sxs-lookup"><span data-stu-id="4205b-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="4205b-192">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="4205b-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="4205b-193">Pak se pro úlohu použije operátor `Await`, aby se načetla hodnota `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="4205b-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="4205b-194">Pokud vaše asynchronní metoda funguje na to, že nezávisí na dokončení úlohy, může metoda pokračovat v práci s těmito dvěma příkazy po volání asynchronní metody a před použitím operátoru await.</span><span class="sxs-lookup"><span data-stu-id="4205b-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="4205b-195">Příklady naleznete v tématu [How to: Revícenásobné webové požadavky paralelně pomocí Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [Postupy: rozšíříte-li asynchronní návod pomocí Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="4205b-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="4205b-196">Protože jste přidali operátor `Await` v předchozím kroku, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4205b-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="4205b-197">Operátor lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="4205b-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="4205b-198">Ignorovat chybu při opakování kroků převodu a nahradit volání `CopyTo` voláním `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="4205b-199">Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="4205b-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="4205b-200">Metoda `CopyTo` nebo `CopyToAsync` kopíruje bajty do svého argumentu, `content`a nevrací smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4205b-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="4205b-201">V synchronní verzi je volání `CopyTo` jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4205b-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="4205b-202">Asynchronní verze, `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="4205b-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4205b-203">Úkol funguje jako "Task (void)" a umožňuje, aby metoda byla očekávána.</span><span class="sxs-lookup"><span data-stu-id="4205b-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="4205b-204">Použijte `Await` nebo `await` pro volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="4205b-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="4205b-205">Předchozí příkaz zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="4205b-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="4205b-206">Vše, co je potřeba udělat v `GetURLContents`, je upravit signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="4205b-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="4205b-207">Operátor `Await` lze použít pouze v metodách, které jsou označeny modifikátorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="4205b-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="4205b-208">Přidejte modifikátor k označení metody jako *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="4205b-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="4205b-209">Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4205b-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4205b-210">V Visual Basic metoda musí být `Function`, která vrací `Task` nebo `Task(Of T)`, nebo musí být metoda `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4205b-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="4205b-211">Obvykle se `Sub` metoda používá pouze v asynchronní obslužné rutině události, kde je `Sub` požadováno.</span><span class="sxs-lookup"><span data-stu-id="4205b-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="4205b-212">V ostatních případech použijete `Task(T)`, pokud metoda Completed má [návratový](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrací hodnotu typu t, a použijete `Task`, pokud metoda Completed nevrátí smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4205b-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="4205b-213">Další informace naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4205b-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

    <span data-ttu-id="4205b-214">Metoda `GetURLContents` obsahuje příkaz return a příkaz vrátí bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="4205b-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="4205b-215">Proto návratový typ asynchronní verze je Task (T), kde T je pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="4205b-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="4205b-216">V signatuře metody proveďte následující změny:</span><span class="sxs-lookup"><span data-stu-id="4205b-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="4205b-217">Změňte návratový typ na `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="4205b-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="4205b-218">Podle konvence mají asynchronní metody názvy, které končí "Async", proto přejmenujte metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="4205b-219">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="4205b-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="4205b-220">U těchto změn je převod `GetURLContents` na asynchronní metodu dokončen.</span><span class="sxs-lookup"><span data-stu-id="4205b-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="4205b-221">Převést SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="4205b-222">Opakujte kroky z předchozího postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="4205b-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="4205b-223">Nejprve změňte volání `GetURLContents` na asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="4205b-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="4205b-224">Změňte název metody, která je volána z `GetURLContents` na `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="4205b-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="4205b-225">Použijte `Await` u úkolu, který `GetURLContentsAsync` vrátí k získání hodnoty bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="4205b-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="4205b-226">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="4205b-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="4205b-227">Předchozí přiřazení zkracuje následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="4205b-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="4205b-228">V signatuře metody proveďte následující změny:</span><span class="sxs-lookup"><span data-stu-id="4205b-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="4205b-229">Označte metodu pomocí modifikátoru `Async`.</span><span class="sxs-lookup"><span data-stu-id="4205b-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="4205b-230">Do názvu metody přidejte "Async".</span><span class="sxs-lookup"><span data-stu-id="4205b-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="4205b-231">V tuto chvíli neexistuje žádná vrácená proměnná úlohy, T, protože `SumPageSizesAsync` nevrací hodnotu pro T. (metoda nemá žádný příkaz `Return`.) Metoda však musí vracet `Task`, aby bylo možné očekávat.</span><span class="sxs-lookup"><span data-stu-id="4205b-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="4205b-232">Proto změňte typ metody z `Sub` na `Function`.</span><span class="sxs-lookup"><span data-stu-id="4205b-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="4205b-233">Návratový typ funkce je `Task`.</span><span class="sxs-lookup"><span data-stu-id="4205b-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="4205b-234">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="4205b-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="4205b-235">Převod `SumPageSizes` na `SumPageSizesAsync` je dokončený.</span><span class="sxs-lookup"><span data-stu-id="4205b-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="4205b-236">Převést startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="4205b-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="4205b-237">V obslužné rutině události změňte název volané metody z `SumPageSizes` na `SumPageSizesAsync`, pokud jste to ještě neudělali.</span><span class="sxs-lookup"><span data-stu-id="4205b-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="4205b-238">Vzhledem k tomu, že `SumPageSizesAsync` je asynchronní metoda, změňte kód v obslužné rutině události tak, aby čekal na výsledek.</span><span class="sxs-lookup"><span data-stu-id="4205b-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="4205b-239">Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="4205b-240">Volání vrátí `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="4205b-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="4205b-241">Stejně jako v předchozích postupech lze volání převést pomocí jednoho příkazu nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="4205b-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="4205b-242">Následující kód tyto změny znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="4205b-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="4205b-243">Chcete-li zabránit nechtěnému znovu zadat operaci, přidejte do horní části `startButton_Click` následující příkaz, kterým zakážete tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="4205b-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="4205b-244">Tlačítko lze znovu povolit na konci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4205b-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="4205b-245">Další informace o Vícenásobný přístup najdete v tématu [zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="4205b-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="4205b-246">Nakonec přidejte modifikátor `Async` k deklaraci, aby mohla obslužná rutina události očekávat `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="4205b-247">Názvy obslužných rutin událostí se typicky nemění.</span><span class="sxs-lookup"><span data-stu-id="4205b-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="4205b-248">Návratový typ se nezměnil na `Task`, protože obslužné rutiny události musí být `Sub` procedurami v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4205b-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="4205b-249">Převod projektu z synchronního na asynchronní zpracování je dokončen.</span><span class="sxs-lookup"><span data-stu-id="4205b-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="4205b-250">Testování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="4205b-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="4205b-251">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="4205b-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="4205b-252">Měl by se zobrazit výstup, který se podobá výstupu synchronního řešení.</span><span class="sxs-lookup"><span data-stu-id="4205b-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="4205b-253">Všimněte si ale následujících rozdílů.</span><span class="sxs-lookup"><span data-stu-id="4205b-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="4205b-254">Po dokončení zpracování se všechny výsledky neprojeví ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="4205b-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="4205b-255">Oba programy například obsahují řádek v `startButton_Click`, který vymaže textové pole.</span><span class="sxs-lookup"><span data-stu-id="4205b-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="4205b-256">Záměrem je vymazat textové pole mezi spuštěním, pokud zvolíte tlačítko **Spustit** pro druhý čas, poté, co se objeví jedna sada výsledků.</span><span class="sxs-lookup"><span data-stu-id="4205b-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="4205b-257">V synchronní verzi je textové pole vymazáno těsně před tím, než se počty zobrazí podruhé, po dokončení stahování a vlákno uživatelského rozhraní je volné pro další práci.</span><span class="sxs-lookup"><span data-stu-id="4205b-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="4205b-258">V asynchronní verzi se textové pole vymaže ihned po kliknutí na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="4205b-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="4205b-259">Ve většině případů není vlákno UI během stahování zablokované.</span><span class="sxs-lookup"><span data-stu-id="4205b-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="4205b-260">Během stahování, počítání a zobrazování webových prostředků můžete okno přesunout nebo změnit jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="4205b-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="4205b-261">Pokud je jeden z webů pomalý nebo neodpovídá, můžete operaci zrušit výběrem tlačítka **Zavřít** (x v poli červené v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="4205b-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="4205b-262">Nahraďte metodu GetURLContentsAsync metodou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4205b-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="4205b-263">.NET Framework poskytuje mnoho asynchronních metod, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="4205b-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="4205b-264">Jedna z nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> metoda, dělá přesně to, co potřebujete pro tento návod.</span><span class="sxs-lookup"><span data-stu-id="4205b-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="4205b-265">Místo metody `GetURLContentsAsync`, kterou jste vytvořili v předchozím postupu, ji můžete použít.</span><span class="sxs-lookup"><span data-stu-id="4205b-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="4205b-266">Prvním krokem je vytvoření objektu <xref:System.Net.Http.HttpClient> v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="4205b-267">Přidejte následující deklaraci na začátek metody.</span><span class="sxs-lookup"><span data-stu-id="4205b-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="4205b-268">V `SumPageSizesAsync,` nahraďte volání metody `GetURLContentsAsync` voláním metody `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="4205b-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="4205b-269">Odeberte nebo Odkomentujte metodu `GetURLContentsAsync`, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="4205b-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="4205b-270">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="4205b-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="4205b-271">Chování této verze projektu by se mělo shodovat s chováním, které popisuje postup testování asynchronního řešení, ale s ještě menším úsilím.</span><span class="sxs-lookup"><span data-stu-id="4205b-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="4205b-272">Příklad</span><span class="sxs-lookup"><span data-stu-id="4205b-272">Example</span></span>

<span data-ttu-id="4205b-273">Následuje úplný příklad převedeného asynchronního řešení, které používá asynchronní metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="4205b-274">Všimněte si, že se silně podobá původnímu synchronnímu řešení.</span><span class="sxs-lookup"><span data-stu-id="4205b-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

<span data-ttu-id="4205b-275">Následující kód obsahuje úplný příklad řešení, které používá metodu `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="4205b-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="4205b-276">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4205b-276">See also</span></span>

- [<span data-ttu-id="4205b-277">Asynchronní Ukázka: přístup k webovému návoduC# (a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="4205b-278">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="4205b-278">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="4205b-279">Async</span><span class="sxs-lookup"><span data-stu-id="4205b-279">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="4205b-280">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="4205b-281">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-281">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="4205b-282">Asynchronní programování založené na úlohách (klepnutím)</span><span class="sxs-lookup"><span data-stu-id="4205b-282">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="4205b-283">Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="4205b-284">Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4205b-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
