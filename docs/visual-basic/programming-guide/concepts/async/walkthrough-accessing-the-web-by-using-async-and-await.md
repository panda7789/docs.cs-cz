---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 535b431fcf8ab5dafa134b8a3c1e2f7eacd6b427
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696504"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="e577f-102">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="e577f-103">Asynchronní programy můžete napsat snadno a intuitivně najít pomocí modifikátoru async/await funkcí.</span><span class="sxs-lookup"><span data-stu-id="e577f-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="e577f-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kódu a nechat kompilátoru zpracování funkce zpětného volání obtížné a pokračování, které obvykle zahrnuje asynchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="e577f-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="e577f-105">Další informace o funkci asynchronní najdete v tématu [asynchronní programování s Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="e577f-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="e577f-106">Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sčítá počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="e577f-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="e577f-107">Průvodce potom převede aplikace pro asynchronní řešení pomocí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="e577f-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="e577f-108">Pokud nechcete, aby k vytváření aplikací, můžete stáhnout "asynchronní ukázka: přístup k webové návod (C# a Visual Basic)" z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="e577f-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="e577f-109">V tomto návodu dokončit následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="e577f-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="e577f-110">Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="e577f-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="e577f-111">Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="e577f-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="e577f-112">Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="e577f-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="e577f-113">Chcete-li přidat potřebné příkazy importy</span><span class="sxs-lookup"><span data-stu-id="e577f-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="e577f-114">Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="e577f-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="e577f-115">K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="e577f-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="e577f-116">Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="e577f-117">Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="e577f-118">Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="e577f-119">K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="e577f-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="e577f-120">Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e577f-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="e577f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e577f-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="e577f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e577f-122">Prerequisites</span></span>  
 <span data-ttu-id="e577f-123">Visual Studio 2012 nebo novější musí být nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="e577f-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="e577f-124">Další informace najdete v tématu [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="e577f-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="e577f-125">Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="e577f-125">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="e577f-126">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e577f-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e577f-127">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e577f-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="e577f-128">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e577f-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e577f-129">V **nainstalovaných šablonách** podokně vyberte jazyka Visual Basic a potom vyberte **aplikaci WPF** ze seznamu typy projektů.</span><span class="sxs-lookup"><span data-stu-id="e577f-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="e577f-130">V **název** textové pole, zadejte `AsyncExampleWPF`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="e577f-131">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="e577f-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="e577f-132">Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="e577f-132">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="e577f-133">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="e577f-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="e577f-134">Pokud **sada nástrojů** okno není viditelný, otevřete **zobrazení** nabídce a potom zvolte **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="e577f-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="e577f-135">Přidat **tlačítko** řízení a **TextBox** řídit k **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="e577f-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="e577f-136">Zvýrazněte **TextBox** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e577f-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="e577f-137">Nastavte **název** vlastnost `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="e577f-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="e577f-138">Nastavte **výška** vlastnost, která má 250.</span><span class="sxs-lookup"><span data-stu-id="e577f-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="e577f-139">Nastavte **šířka** vlastnost na 500.</span><span class="sxs-lookup"><span data-stu-id="e577f-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="e577f-140">Na **Text** zadejte neproporcionálního písma, jako je například Lucida Console nebo globální neproporcionální.</span><span class="sxs-lookup"><span data-stu-id="e577f-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="e577f-141">Zvýrazněte **tlačítko** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e577f-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="e577f-142">Nastavte **název** vlastnost `startButton`.</span><span class="sxs-lookup"><span data-stu-id="e577f-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="e577f-143">Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **spustit**.</span><span class="sxs-lookup"><span data-stu-id="e577f-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="e577f-144">Pozice textového pole a tlačítko tak, aby obsahovat **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="e577f-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="e577f-145">Další informace o WPF návrháře XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e577f-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="e577f-146">Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="e577f-146">To add a reference</span></span>  
  
1.  <span data-ttu-id="e577f-147">V **Průzkumníku**, zvýrazněte názvem vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="e577f-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="e577f-148">Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="e577f-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="e577f-149">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e577f-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="e577f-150">V horní části dialogových oken ověřte, že je váš projekt cílení na rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="e577f-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="e577f-151">V **sestavení** oblasti, zvolte **Framework** Pokud již není vybraná.</span><span class="sxs-lookup"><span data-stu-id="e577f-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="e577f-152">V seznamu názvů, vyberte **System.Net.Http** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="e577f-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="e577f-153">Vyberte **OK** tlačítko dialogové okno zavřete.</span><span class="sxs-lookup"><span data-stu-id="e577f-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a> <span data-ttu-id="e577f-154">Chcete-li přidat potřebné příkazy importy</span><span class="sxs-lookup"><span data-stu-id="e577f-154">To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="e577f-155">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e577f-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="e577f-156">Přidejte následující `Imports` příkazy v horní části souboru kódu, pokud nejsou již existuje.</span><span class="sxs-lookup"><span data-stu-id="e577f-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="e577f-157">Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="e577f-157">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="e577f-158">V okně návrhu MainWindow.xaml, dvakrát klikněte **spustit** tlačítko vytvořte `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="e577f-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="e577f-159">V MainWindow.xaml.vb, zkopírujte následující kód do textu `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="e577f-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="e577f-160">Kód volá metody, která řídí aplikace, `SumPageSizes`a zobrazí zprávu, když se vrátí ovládací prvek `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="e577f-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="e577f-161">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="e577f-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="e577f-162">`SumPageSizes`, který získá seznam adres URL webové stránky z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e577f-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="e577f-163">`SetUpURLList`, který provede a vrátí seznam hodnot webové adresy.</span><span class="sxs-lookup"><span data-stu-id="e577f-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="e577f-164">`GetURLContents`, který stáhne obsah každý web a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="e577f-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="e577f-165">`DisplayResults`, který zobrazí počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e577f-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="e577f-166">Zkopírujte následující čtyři metody a vložte je v části `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="e577f-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> <span data-ttu-id="e577f-167">K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="e577f-167">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="e577f-168">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="e577f-169">By se zobrazit výstup, který vypadá takto: v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="e577f-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="e577f-170">Všimněte si, že bude trvat několik sekund zobrazí počty.</span><span class="sxs-lookup"><span data-stu-id="e577f-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="e577f-171">Během této doby je blokována vlákna uživatelského rozhraní, kdy čeká požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="e577f-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="e577f-172">V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo i zavřete okno zobrazení po kliknutí **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="e577f-173">Tyto úsilí nezdaří, dokud začít zobrazí počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="e577f-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="e577f-174">Pokud web nereaguje, nemáte žádná informace o lokality, která se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="e577f-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="e577f-175">Je i obtížné čekání na zastavení a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="e577f-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="e577f-176">Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="e577f-177">Převést synchronní řešení asynchronní řešení, je nejlepší místo k spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webové .</span><span class="sxs-lookup"><span data-stu-id="e577f-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="e577f-178">Rozhraní .NET Framework usnadňuje převod zadáním asynchronní verze obě metody.</span><span class="sxs-lookup"><span data-stu-id="e577f-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="e577f-179">Další informace o metodách, které se používají v `GetURLContents`, najdete v části <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="e577f-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e577f-180">Jak budete postupovat podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e577f-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="e577f-181">Můžete je ignorovat a pokračovat návodu.</span><span class="sxs-lookup"><span data-stu-id="e577f-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="e577f-182">Změnit metodu, která je volána v třetím řádku `GetURLContents` z `GetResponse` pro asynchronní, založený na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e577f-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="e577f-183">`GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e577f-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e577f-184">V takovém případě *návratový proměnnou úloh*, `TResult`, má typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="e577f-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="e577f-185">Tato úloha je promise k vytvoření skutečné třídě `WebResponse` objektu po požadovaná data byla stažena a je úloha spuštěná na dokončení.</span><span class="sxs-lookup"><span data-stu-id="e577f-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="e577f-186">Načíst `WebResponse` z úlohy hodnoty, použijí [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor k volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="e577f-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="e577f-187">`Await` Operátor pozastaví provádění aktuální metody `GetURLContents`, dokud se nedokončí awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="e577f-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="e577f-188">Do té doby vrátí ovládací prvek volajícímu aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="e577f-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="e577f-189">V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="e577f-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="e577f-190">Po dokončení úlohy, přislíbeném `WebResponse` objektu je jako hodnotu awaited úloh a jejich přiřazení k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="e577f-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="e577f-191">Do následujících dvou příkazů o vysvětlení, co se stane, je možné oddělit předchozí příkaz.</span><span class="sxs-lookup"><span data-stu-id="e577f-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="e577f-192">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="e577f-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="e577f-193">Potom `Await` operátor se použije k načtení úkolu `WebResponse` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e577f-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="e577f-194">Pokud asynchronní metody práce uděláte, které nezávisí na dokončení úlohy, metodu můžete pokračovat v které pracují mezi těchto dvou příkazů po volání asynchronní metody a před použitím operátoru await.</span><span class="sxs-lookup"><span data-stu-id="e577f-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="e577f-195">Příklady najdete v tématu [postup: Zkontrolujte vícenásobných webových dotazů paralelně pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření návodu asynchronních podle pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="e577f-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="e577f-196">Protože jste přidali `Await` dojde k chybě kompilátoru operátor v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="e577f-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="e577f-197">Operátor mohou být používány pouze metody, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e577f-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="e577f-198">Ignorovat chybu při opakováním kroků převod nahradit volání `CopyTo` pomocí volání `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="e577f-199">Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="e577f-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="e577f-200">`CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů na její argument `content`a nevrací smysluplný hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e577f-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="e577f-201">V synchronní verzi volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e577f-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="e577f-202">Asynchronní verzi `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="e577f-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="e577f-203">Úloha funguje jako "Task(void)" a umožňuje metody být očekáváno.</span><span class="sxs-lookup"><span data-stu-id="e577f-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="e577f-204">Použít `Await` nebo `await` k volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="e577f-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="e577f-205">Předchozí příkaz zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="e577f-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  <span data-ttu-id="e577f-206">Všechno, co zůstane v `GetURLContents` je upravte podpis metody.</span><span class="sxs-lookup"><span data-stu-id="e577f-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="e577f-207">Můžete použít `Await` operátor pouze v metody, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e577f-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="e577f-208">Přidat modifikátor označit jako metodu *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="e577f-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  <span data-ttu-id="e577f-209">Návratový typ asynchronní metody lze pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e577f-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e577f-210">V jazyce Visual Basic, musí být metoda `Function` , který vrací `Task` nebo `Task(Of T)`, nebo musí být metoda `Sub`.</span><span class="sxs-lookup"><span data-stu-id="e577f-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="e577f-211">Obvykle `Sub` metoda se používá jenom v asynchronní obslužnou rutinu, kde `Sub` je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e577f-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="e577f-212">V ostatních případech použijete `Task(T)` Pokud má metodu dokončené [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrací hodnotu zadejte T a používáte `Task` pokud dokončené metoda nevrací hodnotu smysluplný.</span><span class="sxs-lookup"><span data-stu-id="e577f-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="e577f-213">Další informace najdete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e577f-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="e577f-214">Metoda `GetURLContents` má příkaz return, a příkaz vrátí pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="e577f-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="e577f-215">Návratový typ asynchronní verze je proto Task(T), kde T představuje bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="e577f-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="e577f-216">Proveďte následující změny v podpis metody:</span><span class="sxs-lookup"><span data-stu-id="e577f-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="e577f-217">Změnit návratový typ na `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="e577f-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="e577f-218">Podle konvence asynchronní metody mají názvy, které končí "Asynchronní,", přejmenujte metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="e577f-219">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="e577f-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="e577f-220">Pomocí těchto několik změn, převod `GetURLContents` pro asynchronní metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="e577f-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="e577f-221">Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="e577f-222">Opakováním kroků v předchozím postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="e577f-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="e577f-223">Nejprve změnit volání `GetURLContents` pro asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="e577f-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="e577f-224">Změňte název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="e577f-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="e577f-225">Použít `Await` úlohy, `GetURLContentsAsync` vrátí získat bajtů pole hodnota.</span><span class="sxs-lookup"><span data-stu-id="e577f-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="e577f-226">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="e577f-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="e577f-227">Předchozí přiřazení zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="e577f-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  <span data-ttu-id="e577f-228">Proveďte následující změny v signatury metody:</span><span class="sxs-lookup"><span data-stu-id="e577f-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="e577f-229">Označit metodu s `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e577f-229">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="e577f-230">Přidejte "Asynchronní" název metody.</span><span class="sxs-lookup"><span data-stu-id="e577f-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="e577f-231">Neexistuje žádné proměnné návratový úkolů, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metodu neobsahuje žádné `Return` příkaz.) Však musí vracet metodu `Task` být může používat await.</span><span class="sxs-lookup"><span data-stu-id="e577f-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="e577f-232">Proto změnit typ metody z `Sub` k `Function`.</span><span class="sxs-lookup"><span data-stu-id="e577f-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="e577f-233">Návratový typ funkce je `Task`.</span><span class="sxs-lookup"><span data-stu-id="e577f-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="e577f-234">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="e577f-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="e577f-235">Převod `SumPageSizes` k `SumPageSizesAsync` dokončení.</span><span class="sxs-lookup"><span data-stu-id="e577f-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="e577f-236">Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e577f-236">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="e577f-237">V obslužné rutině, změňte název metody volané z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="e577f-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="e577f-238">Protože `SumPageSizesAsync` je asynchronní metody, změňte kód v obslužné rutiny události pro await výsledek.</span><span class="sxs-lookup"><span data-stu-id="e577f-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="e577f-239">Volání `SumPageSizesAsync` odpovídá volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="e577f-240">Vrátí volání `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="e577f-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="e577f-241">Jako v předchozích postupech můžete převést volání pomocí jeden příkaz nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="e577f-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="e577f-242">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="e577f-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="e577f-243">Pokud chcete zabránit omylem nutnosti opětovného zadávání operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="e577f-244">Tlačítko na konci obslužné rutiny události můžete znovu povolit.</span><span class="sxs-lookup"><span data-stu-id="e577f-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="e577f-245">Další informace o opětovné zadání najdete v tématu [zpracování vícenásobný přístup v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e577f-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="e577f-246">Nakonec přidejte `Async` modifikátor deklaraci tak, aby obslužná rutina události můžete await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="e577f-247">Obvykle se nezmění názvy obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="e577f-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="e577f-248">Návratový typ se nezmění na `Task` protože obslužné rutiny události musí být `Sub` procedury v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e577f-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="e577f-249">Převod projektu synchronní pro asynchronní zpracování je dokončena.</span><span class="sxs-lookup"><span data-stu-id="e577f-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="e577f-250">K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="e577f-250">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="e577f-251">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="e577f-252">By se zobrazit výstup, který vypadá takto: výstup synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="e577f-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="e577f-253">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="e577f-253">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="e577f-254">Výsledky všechny nedojde ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="e577f-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="e577f-255">Například obě aplikace obsahovat řádek v `startButton_Click` který vymaže textového pole.</span><span class="sxs-lookup"><span data-stu-id="e577f-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="e577f-256">Je cílem vymazat textové pole mezi spustí, pokud se rozhodnete **spustit** tlačítko druhý dobu, po ukazuje se, jednu sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="e577f-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="e577f-257">V synchronní verzi textového pole není zaškrtnuto, těsně před zobrazí počty druhý dobu, po dokončení stahování a vlákna uživatelského rozhraní může provádět další činnosti.</span><span class="sxs-lookup"><span data-stu-id="e577f-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="e577f-258">V asynchronní verzi textového pole vymaže hned po zvolení **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="e577f-259">Co je nejdůležitější – vlákna uživatelského rozhraní není blokován během stahování.</span><span class="sxs-lookup"><span data-stu-id="e577f-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="e577f-260">Můžete přesunout nebo změňte velikost okna během stahování webové prostředky, počítají a zobrazit.</span><span class="sxs-lookup"><span data-stu-id="e577f-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="e577f-261">Pokud jeden z webů je pomalé nebo přestane reagovat, můžete zrušit operaci tak, že zvolíte **Zavřít** tlačítko (x v poli red v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="e577f-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="e577f-262">Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e577f-262">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="e577f-263">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="e577f-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="e577f-264">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, nemá právě co potřebujete pro účely tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="e577f-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="e577f-265">Můžete ho místo `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="e577f-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="e577f-266">Prvním krokem je vytvoření `HttpClient` objektu v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="e577f-267">Přidejte následující deklarace při spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="e577f-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="e577f-268">V `SumPageSizesAsync,` nahradit volání vaše `GetURLContentsAsync` metoda pomocí volání `HttpClient` metoda.</span><span class="sxs-lookup"><span data-stu-id="e577f-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="e577f-269">Odeberte nebo komentář `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="e577f-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="e577f-270">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e577f-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="e577f-271">Chování tuto verzi projekt by měl odpovídat chování, které je popsaný v části "postup testovací asynchronní řešení", ale s i méně úsilí od vás.</span><span class="sxs-lookup"><span data-stu-id="e577f-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="e577f-272">Příklad</span><span class="sxs-lookup"><span data-stu-id="e577f-272">Example</span></span>  
 <span data-ttu-id="e577f-273">Následující kód obsahuje úplný příklad převod synchronního asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="e577f-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="e577f-274">Všimněte si, že důrazně podobá řešení původní, synchronní.</span><span class="sxs-lookup"><span data-stu-id="e577f-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="e577f-275">Následující kód obsahuje kompletní příklad řešení, která používá `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="e577f-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="e577f-276">Viz také</span><span class="sxs-lookup"><span data-stu-id="e577f-276">See Also</span></span>  
 [<span data-ttu-id="e577f-277">Ukázka asynchronního: Přístup k webové návod (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [<span data-ttu-id="e577f-278">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="e577f-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="e577f-279">Async</span><span class="sxs-lookup"><span data-stu-id="e577f-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="e577f-280">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="e577f-281">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="e577f-282">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="e577f-282">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="e577f-283">Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="e577f-284">Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e577f-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
