---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 812c854c6c5b34ac958ef136b816f1eba211874a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648852"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="c68c5-102">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="c68c5-103">Asynchronní programy můžete napsat snadno a intuitivně s použitím funkce async/await.</span><span class="sxs-lookup"><span data-stu-id="c68c5-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="c68c5-104">Můžete psát asynchronní kód, který vypadá jako synchronní kód a nechte kompilátor obtížné zpětného volání funkce a pokračování, které obvykle zahrnuje asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="c68c5-105">Další informace o funkci Async naleznete v tématu [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="c68c5-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="c68c5-106">Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sumarizuje počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="c68c5-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="c68c5-107">Návodu poté převádí aplikaci, aby asynchronní řešení pomocí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="c68c5-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="c68c5-108">Pokud nechcete, aby k vytváření aplikací, si můžete stáhnout "asynchronní vzorek: Přístup k webovému návodu (C# a Visual Basic) "z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="c68c5-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="c68c5-109">V tomto návodu dokončíte následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="c68c5-109">In this walkthrough, you complete the following tasks:</span></span>  
  
- [<span data-ttu-id="c68c5-110">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c68c5-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
- [<span data-ttu-id="c68c5-111">Návrh jednoduchého hlavního okna MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="c68c5-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
- [<span data-ttu-id="c68c5-112">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="c68c5-112">To add a reference</span></span>](#AddRef)  
  
- [<span data-ttu-id="c68c5-113">Přidání potřebných příkazů Imports</span><span class="sxs-lookup"><span data-stu-id="c68c5-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
- [<span data-ttu-id="c68c5-114">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="c68c5-114">To create a synchronous application</span></span>](#synchronous)  
  
- [<span data-ttu-id="c68c5-115">Otestování synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="c68c5-115">To test the synchronous solution</span></span>](#testSynch)  
  
- [<span data-ttu-id="c68c5-116">Převedení metody GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
- [<span data-ttu-id="c68c5-117">Převedení metody SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
- [<span data-ttu-id="c68c5-118">Převedení metody startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
- [<span data-ttu-id="c68c5-119">Otestování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="c68c5-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
- [<span data-ttu-id="c68c5-120">Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c68c5-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
- [<span data-ttu-id="c68c5-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c68c5-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="c68c5-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c68c5-122">Prerequisites</span></span>  
 <span data-ttu-id="c68c5-123">Visual Studio 2012 nebo novější musí nainstalovat ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c68c5-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="c68c5-124">Další informace najdete v tématu [webu společnosti Microsoft](https://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="c68c5-124">For more information, see the [Microsoft website](https://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
### <a name="CreateWPFApp"></a> <span data-ttu-id="c68c5-125">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c68c5-125">To create a WPF application</span></span>  
  
1. <span data-ttu-id="c68c5-126">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c68c5-126">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="c68c5-127">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="c68c5-128">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c68c5-128">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="c68c5-129">V **nainstalované šablony** podokně zvolte jazyka Visual Basic a pak zvolte **aplikace WPF** ze seznamu typů projektů.</span><span class="sxs-lookup"><span data-stu-id="c68c5-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="c68c5-130">V **název** textové pole, zadejte `AsyncExampleWPF`a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="c68c5-131">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-131">The new project appears in **Solution Explorer**.</span></span>  
  
## <a name="BKMK_DesignWPFMainWin"></a>   
### <a name="MainWindow"></a> <span data-ttu-id="c68c5-132">Návrh jednoduchého hlavního okna MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="c68c5-132">To design a simple WPF MainWindow</span></span>  
  
1. <span data-ttu-id="c68c5-133">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2. <span data-ttu-id="c68c5-134">Pokud **nástrojů** okně není zobrazena, otevřete **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3. <span data-ttu-id="c68c5-135">Přidat **tlačítko** ovládacího prvku a **textového pole** ovládací prvek **hlavního okna MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="c68c5-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4. <span data-ttu-id="c68c5-136">Zvýrazněte **TextBox** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c68c5-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    - <span data-ttu-id="c68c5-137">Nastavte **název** vlastnost `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="c68c5-138">Nastavte **výška** vlastnost na 250.</span><span class="sxs-lookup"><span data-stu-id="c68c5-138">Set the **Height** property to 250.</span></span>  
  
    - <span data-ttu-id="c68c5-139">Nastavte **šířka** vlastnost na hodnotu 500.</span><span class="sxs-lookup"><span data-stu-id="c68c5-139">Set the **Width** property to 500.</span></span>  
  
    - <span data-ttu-id="c68c5-140">Na **Text** kartu, zadejte neproporcionální písmo jako Arial konzoly nebo globální neproporcionálním písmem v.</span><span class="sxs-lookup"><span data-stu-id="c68c5-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5. <span data-ttu-id="c68c5-141">Zvýrazněte **tlačítko** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c68c5-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    - <span data-ttu-id="c68c5-142">Nastavte **název** vlastnost `startButton`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-142">Set the **Name** property to `startButton`.</span></span>  
  
    - <span data-ttu-id="c68c5-143">Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **Start**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6. <span data-ttu-id="c68c5-144">Umístěte do textového pole a tlačítko tak, aby oba se objeví v **hlavního okna MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="c68c5-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="c68c5-145">Další informace o Návrhář WPF XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c68c5-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
## <a name="BKMK_AddReference"></a>   
### <a name="AddRef"></a> <span data-ttu-id="c68c5-146">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="c68c5-146">To add a reference</span></span>  
  
1. <span data-ttu-id="c68c5-147">V **Průzkumníka řešení**, vyberte název vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2. <span data-ttu-id="c68c5-148">V panelu nabídky zvolte **projektu**, **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="c68c5-149">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c68c5-149">The **Reference Manager** dialog box appears.</span></span>  
  
3. <span data-ttu-id="c68c5-150">V horní části dialogového okna ověřte, že váš projekt je cílen na verzi rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c68c5-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4. <span data-ttu-id="c68c5-151">V **sestavení** oblasti, zvolte **Framework** Pokud není již vybrána.</span><span class="sxs-lookup"><span data-stu-id="c68c5-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5. <span data-ttu-id="c68c5-152">Vyberte v seznamu názvů **System.Net.Http** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6. <span data-ttu-id="c68c5-153">Zvolte **OK** tlačítka zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c68c5-153">Choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="BKMK_AddStatesandDirs"></a>   
### <a name="ImportsState"></a> <span data-ttu-id="c68c5-154">Přidání potřebných příkazů Imports</span><span class="sxs-lookup"><span data-stu-id="c68c5-154">To add necessary Imports statements</span></span>  
  
1. <span data-ttu-id="c68c5-155">V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c68c5-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2. <span data-ttu-id="c68c5-156">Přidejte následující `Imports` příkazů v horní části souboru kódu, pokud již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c68c5-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
## <a name="BKMK_CreatSynchApp"></a>   
### <a name="synchronous"></a> <span data-ttu-id="c68c5-157">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="c68c5-157">To create a synchronous application</span></span>  
  
1. <span data-ttu-id="c68c5-158">V okně návrhu, MainWindow.xaml, dvakrát klikněte **Start** pro vytvoření `startButton_Click` obslužné rutiny události v souboru MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c68c5-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2. <span data-ttu-id="c68c5-159">V souboru MainWindow.xaml.vb, zkopírujte následující kód do hlavní části `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="c68c5-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="c68c5-160">Kód volá metodu, která řídí aplikaci, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3. <span data-ttu-id="c68c5-161">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="c68c5-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    - <span data-ttu-id="c68c5-162">`SumPageSizes`, která načte seznam adres URL webové stránky z `SetUpURLList` a pak zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="c68c5-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    - <span data-ttu-id="c68c5-163">`SetUpURLList`, který provede a vrátí seznam webové adresy.</span><span class="sxs-lookup"><span data-stu-id="c68c5-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    - <span data-ttu-id="c68c5-164">`GetURLContents`, který stáhne obsah každého webu a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="c68c5-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    - <span data-ttu-id="c68c5-165">`DisplayResults`, který zobrazuje počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="c68c5-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="c68c5-166">Následující čtyři metody zkopírujte a vložte je za `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="c68c5-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
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
  
## <a name="BKMK_TestSynchSol"></a>   
### <a name="testSynch"></a> <span data-ttu-id="c68c5-167">Otestování synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="c68c5-167">To test the synchronous solution</span></span>  
  
1. <span data-ttu-id="c68c5-168">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="c68c5-169">By se zobrazit výstup, který vypadá podobně jako v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="c68c5-170">Všimněte si, že trvá několik sekund zobrazí počty.</span><span class="sxs-lookup"><span data-stu-id="c68c5-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="c68c5-171">Během této doby vlákno uživatelského rozhraní je blokována během čekání požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="c68c5-172">V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo dokonce zavřete okno zobrazení po zvolení **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="c68c5-173">Tyto aktivity dál rozšiřuji neúspěšné, dokud se začnou objevovat počtu bajtů.</span><span class="sxs-lookup"><span data-stu-id="c68c5-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="c68c5-174">Pokud web nereaguje, je nutné žádná zpráva o které lokalitě se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="c68c5-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="c68c5-175">Je obtížné i zastavte čekání a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-175">It is difficult even to stop waiting and close the program.</span></span>  
  
## <a name="BKMK_ConvertGtBtArr"></a>   
### <a name="GetURLContents"></a> <span data-ttu-id="c68c5-176">Převedení metody GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1. <span data-ttu-id="c68c5-177">Převést synchronní řešení na asynchronní řešení, je nejlepším místem pro spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> – metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje na web .</span><span class="sxs-lookup"><span data-stu-id="c68c5-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="c68c5-178">Rozhraní .NET Framework zjednodušuje převod zadáním asynchronní verze obě metody.</span><span class="sxs-lookup"><span data-stu-id="c68c5-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="c68c5-179">Další informace o metodách, které se používají v `GetURLContents`, naleznete v tématu <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c68c5-180">Jak budete postupovat podle kroků v tomto názorném postupu se zobrazí několik chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c68c5-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="c68c5-181">Můžete je ignorovat a pokračovat v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="c68c5-182">Změnit metodu, která je volána v třetí řádek `GetURLContents` z `GetResponse` na asynchronní, založené na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c68c5-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2. <span data-ttu-id="c68c5-183">`GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c68c5-184">V takovém případě *úloh návratové*, `TResult`, má typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="c68c5-185">Úkol je příslib z k vytvoření skutečný `WebResponse` objektu po stažení požadovaných dat a je úloha spuštěná na dokončení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="c68c5-186">Načíst `WebResponse` hodnoty z úlohy, použijte [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="c68c5-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="c68c5-187">`Await` Operátor pozastaví vykonávání aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="c68c5-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="c68c5-188">Mezitím se ovládací prvek vrátí volajícímu metody, aktuální.</span><span class="sxs-lookup"><span data-stu-id="c68c5-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="c68c5-189">V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="c68c5-190">Úloha dokončení přislíbeném `WebResponse` objekt je vytvořen jako hodnota očekávané úlohy a přiřazená k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="c68c5-191">Předchozí příkaz je možné rozdělit na následující dva příkazy o vysvětlení, co se stane.</span><span class="sxs-lookup"><span data-stu-id="c68c5-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="c68c5-192">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="c68c5-193">Potom `Await` úkol k získání je použit operátor `WebResponse` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="c68c5-194">Pokud asynchronní metoda má práce, která nezávisí na dokončení úlohy, metoda může pokračovat v práci mezi tyto dva příkazy po volání metody async a předtím, než je použit operátor await.</span><span class="sxs-lookup"><span data-stu-id="c68c5-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="c68c5-195">Příklady najdete v tématu [jak: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="c68c5-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3. <span data-ttu-id="c68c5-196">Vzhledem k tomu, že jste přidali `Await` dojde k chybě kompilátoru operátor v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="c68c5-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="c68c5-197">Operátor, který lze použít pouze v metodách, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c68c5-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="c68c5-198">Ignorovat chybu, zatímco nahraďte volání kroky převod `CopyTo` voláním `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    - <span data-ttu-id="c68c5-199">Změnit název metody, která je volána k <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    - <span data-ttu-id="c68c5-200">`CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů do svého argumentu, `content`a nevrací smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="c68c5-201">Synchronní verze volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="c68c5-202">Asynchronní verze `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="c68c5-203">Úloha funkce jako "Task(void)" a umožňuje metodu k ní použít operátor await.</span><span class="sxs-lookup"><span data-stu-id="c68c5-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="c68c5-204">Použít `Await` nebo `await` volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="c68c5-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="c68c5-205">Předchozí příkaz zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4. <span data-ttu-id="c68c5-206">Všechno, zůstane do `GetURLContents` je upravte podpis metody.</span><span class="sxs-lookup"><span data-stu-id="c68c5-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="c68c5-207">Můžete použít `Await` operátor pouze v metodách, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c68c5-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="c68c5-208">Přidat modifikátor k označení metody jako *asynchronní metoda*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="c68c5-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5. <span data-ttu-id="c68c5-209">Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c68c5-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c68c5-210">V jazyce Visual Basic, musí být metoda `Function` , která vrací `Task` nebo `Task(Of T)`, nebo metoda musí být `Sub`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="c68c5-211">Obvykle `Sub` metoda se používá jenom v asynchronní obslužnou rutinu události, kde `Sub` je povinný.</span><span class="sxs-lookup"><span data-stu-id="c68c5-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="c68c5-212">V ostatních případech použijete `Task(T)` pokud dokončené metody [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrátí hodnotu typu T a používáte `Task` Pokud dokončená metoda nevrací hodnotu smysluplné.</span><span class="sxs-lookup"><span data-stu-id="c68c5-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="c68c5-213">Další informace najdete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="c68c5-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="c68c5-214">Metoda `GetURLContents` disponuje návratovým příkazem, a příkaz vrátí pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="c68c5-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="c68c5-215">Návratový typ asynchronní verze je proto Task(T), kde T je bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="c68c5-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="c68c5-216">Proveďte následující změny v podpisu metody:</span><span class="sxs-lookup"><span data-stu-id="c68c5-216">Make the following changes in the method signature:</span></span>  
  
    - <span data-ttu-id="c68c5-217">Změňte návratový typ na `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    - <span data-ttu-id="c68c5-218">Podle konvence asynchronní metody mají názvy, které končí slovem "Async", takže přejmenovat metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="c68c5-219">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c68c5-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="c68c5-220">Tyto drobné změny převodu `GetURLContents` na asynchronní metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
## <a name="BKMK_ConvertSumPagSzs"></a>   
### <a name="SumPageSizes"></a> <span data-ttu-id="c68c5-221">Převedení metody SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1. <span data-ttu-id="c68c5-222">Zopakujte kroky z předchozího postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="c68c5-223">Nejprve změňte volání `GetURLContents` pro asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="c68c5-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    - <span data-ttu-id="c68c5-224">Změnit název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="c68c5-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    - <span data-ttu-id="c68c5-225">Použít `Await` úkolu, který `GetURLContentsAsync` hodnota pole vrátí získat bajt.</span><span class="sxs-lookup"><span data-stu-id="c68c5-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="c68c5-226">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c68c5-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="c68c5-227">Dřívější přiřazení zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="c68c5-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2. <span data-ttu-id="c68c5-228">Proveďte následující změny v podpisu metody:</span><span class="sxs-lookup"><span data-stu-id="c68c5-228">Make the following changes in the method's signature:</span></span>  
  
    - <span data-ttu-id="c68c5-229">Označení metody `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c68c5-229">Mark the method with the `Async` modifier.</span></span>  
  
    - <span data-ttu-id="c68c5-230">Přidáte k názvu metody "Async".</span><span class="sxs-lookup"><span data-stu-id="c68c5-230">Add "Async" to the method name.</span></span>  
  
    - <span data-ttu-id="c68c5-231">Neexistuje žádná proměnná vrácené úlohy, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metoda nemá žádný `Return` příkazu.) Metoda však musí vrátit `Task` bude očekávatelný.</span><span class="sxs-lookup"><span data-stu-id="c68c5-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="c68c5-232">Proto změnit typ metody z `Sub` k `Function`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="c68c5-233">Návratový typ funkce je `Task`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="c68c5-234">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c68c5-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="c68c5-235">Převod `SumPageSizes` k `SumPageSizesAsync` je dokončena.</span><span class="sxs-lookup"><span data-stu-id="c68c5-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
## <a name="BKMK_Cnvrtbttn1"></a>   
### <a name="startButton"></a> <span data-ttu-id="c68c5-236">Převedení metody startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="c68c5-236">To convert startButton_Click to an asynchronous method</span></span>  
  
1. <span data-ttu-id="c68c5-237">V obslužné rutině události změnit název volané metody z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="c68c5-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2. <span data-ttu-id="c68c5-238">Protože `SumPageSizesAsync` je metodou asynchronní kód v obslužné rutině události await pro čekání výsledek.</span><span class="sxs-lookup"><span data-stu-id="c68c5-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="c68c5-239">Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="c68c5-240">Volání se vrátí `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="c68c5-241">Stejně jako v předchozích postupů můžete převést volání pomocí jednoho příkazu nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="c68c5-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="c68c5-242">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c68c5-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3. <span data-ttu-id="c68c5-243">Chcete-li zabránit náhodnému pokuste operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="c68c5-244">Můžete znovu povolit tlačítko na konci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c68c5-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="c68c5-245">Další informace o vícenásobného přístupu najdete v tématu [zpracování vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="c68c5-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4. <span data-ttu-id="c68c5-246">Nakonec přidejte `Async` modifikátoru deklarace tak, aby obslužná rutina události může čekat `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="c68c5-247">Obvykle se nezmění názvy obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="c68c5-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="c68c5-248">Návratový typ není změněn na `Task` protože obslužné rutiny události musí být `Sub` procedury v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c68c5-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="c68c5-249">Dokončení převodu projektu z synchronní pro asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="c68c5-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
## <a name="BKMK_testAsynchSolution"></a>   
### <a name="testAsynch"></a> <span data-ttu-id="c68c5-250">Otestování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="c68c5-250">To test the asynchronous solution</span></span>  
  
1. <span data-ttu-id="c68c5-251">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2. <span data-ttu-id="c68c5-252">By se zobrazit výstup, který se podobá výstup synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="c68c5-253">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="c68c5-253">However, notice the following differences.</span></span>  
  
    - <span data-ttu-id="c68c5-254">Výsledky všech nedojde ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="c68c5-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="c68c5-255">Například obě aplikace obsahovat řádek v `startButton_Click` , který vymaže do textového pole.</span><span class="sxs-lookup"><span data-stu-id="c68c5-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="c68c5-256">Naším záměrem je zrušte textové pole mezi spuštění, pokud se rozhodnete **Start** tlačítko podruhé, po jednu sadu výsledků nezobrazila.</span><span class="sxs-lookup"><span data-stu-id="c68c5-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="c68c5-257">Synchronní verze do textového pole není zaškrtnuto, těsně před plánovaným začátkem zobrazují počty pro při druhém volání při dokončení stahování a vlákna uživatelského rozhraní je zdarma provádět další činnosti.</span><span class="sxs-lookup"><span data-stu-id="c68c5-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="c68c5-258">V asynchronní verze, do textového pole vymaže ihned poté, co vyberete **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    - <span data-ttu-id="c68c5-259">Co je nejdůležitější vlákno uživatelského rozhraní není blokované, soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="c68c5-260">Můžete přecházet nebo změně velikosti okna, zatímco v průběhu stahování webové prostředky počítá a zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="c68c5-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="c68c5-261">Pokud některý z webů je pomalý nebo nereaguje, můžete zrušit operaci výběrem **Zavřít** tlačítko (x červená pole v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="c68c5-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
## <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
### <a name="GetURLContentsAsync"></a> <span data-ttu-id="c68c5-262">Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c68c5-262">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1. <span data-ttu-id="c68c5-263">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c68c5-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="c68c5-264">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, stačí provedla potřebné pro tento návod.</span><span class="sxs-lookup"><span data-stu-id="c68c5-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="c68c5-265">Můžete použít místo něj `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="c68c5-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="c68c5-266">Prvním krokem je vytvoření `HttpClient` objektů v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="c68c5-267">Na začátek metody přidejte následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="c68c5-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2. <span data-ttu-id="c68c5-268">V `SumPageSizesAsync,` nahraďte volání vaše `GetURLContentsAsync` pomocí volání metody `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="c68c5-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3. <span data-ttu-id="c68c5-269">Odstranit nebo okomentovat `GetURLContentsAsync` metodu, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="c68c5-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4. <span data-ttu-id="c68c5-270">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c68c5-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="c68c5-271">Chování této verze projektu by měl odpovídat chování, které popisuje postup "k otestování asynchronního řešení", ale s i menším úsilím od vás.</span><span class="sxs-lookup"><span data-stu-id="c68c5-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
## <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="c68c5-272">Příklad</span><span class="sxs-lookup"><span data-stu-id="c68c5-272">Example</span></span>  
 <span data-ttu-id="c68c5-273">Následující kód obsahuje úplný příklad převod ze synchronního na asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metodu, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="c68c5-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="c68c5-274">Všimněte si, že důrazně vypadá podobně jako původní, která je synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="c68c5-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="c68c5-275">Následující kód obsahuje úplný příklad řešení, které používá `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="c68c5-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
        '' Two-step async call.  
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
  
## <a name="see-also"></a><span data-ttu-id="c68c5-276">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c68c5-276">See also</span></span>

- [<span data-ttu-id="c68c5-277">Ukázka asynchronní metody: Přístup k webovému návodu (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="c68c5-278">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="c68c5-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="c68c5-279">Async</span><span class="sxs-lookup"><span data-stu-id="c68c5-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="c68c5-280">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="c68c5-281">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="c68c5-282">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="c68c5-282">Task-based Asynchronous Programming (TAP)</span></span>](https://go.microsoft.com/fwlink/?LinkId=204847)
- [<span data-ttu-id="c68c5-283">Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="c68c5-284">Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68c5-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
