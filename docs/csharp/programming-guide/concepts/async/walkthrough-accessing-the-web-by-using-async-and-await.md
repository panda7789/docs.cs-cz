---
title: "Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="7ef24-102">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef24-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="7ef24-103">Asynchronní programy můžete napsat snadno a intuitivně najít pomocí modifikátoru async/await funkcí.</span><span class="sxs-lookup"><span data-stu-id="7ef24-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="7ef24-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kódu a nechat kompilátoru zpracování funkce zpětného volání obtížné a pokračování, které obvykle zahrnuje asynchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="7ef24-105">Další informace o funkci asynchronní najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ef24-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="7ef24-106">Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sčítá počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="7ef24-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="7ef24-107">Průvodce potom převede aplikace pro asynchronní řešení pomocí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="7ef24-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="7ef24-108">Pokud nechcete, aby k vytváření aplikací, můžete stáhnout "asynchronní ukázka: přístup k webové návod (C# a Visual Basic)" z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="7ef24-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="7ef24-109">V tomto návodu dokončit následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7ef24-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="7ef24-110">Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="7ef24-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="7ef24-111">Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="7ef24-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="7ef24-112">Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="7ef24-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="7ef24-113">Chcete-li přidat potřebné pomocí direktiv</span><span class="sxs-lookup"><span data-stu-id="7ef24-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="7ef24-114">Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="7ef24-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="7ef24-115">K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="7ef24-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="7ef24-116">Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="7ef24-117">Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="7ef24-118">Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="7ef24-119">K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="7ef24-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="7ef24-120">Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ef24-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="7ef24-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ef24-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="7ef24-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ef24-122">Prerequisites</span></span>  
 <span data-ttu-id="7ef24-123">Visual Studio 2012 nebo novější musí být nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="7ef24-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="7ef24-124">Další informace najdete v tématu [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="7ef24-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="7ef24-125"><a name="CreateWPFApp"></a>Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="7ef24-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="7ef24-126">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ef24-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7ef24-127">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="7ef24-128">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7ef24-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7ef24-129">V **nainstalovaných šablonách** podokně vyberte Visual C# a potom vyberte **aplikaci WPF** ze seznamu typy projektů.</span><span class="sxs-lookup"><span data-stu-id="7ef24-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="7ef24-130">V **název** textové pole, zadejte `AsyncExampleWPF`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="7ef24-131">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="7ef24-132"><a name="MainWindow"></a>Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="7ef24-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="7ef24-133">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="7ef24-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="7ef24-134">Pokud **sada nástrojů** okno není viditelný, otevřete **zobrazení** nabídce a potom zvolte **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="7ef24-135">Přidat **tlačítko** řízení a **TextBox** řídit k **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="7ef24-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="7ef24-136">Zvýrazněte **TextBox** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7ef24-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7ef24-137">Nastavte **název** vlastnost `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="7ef24-138">Nastavte **výška** vlastnost, která má 250.</span><span class="sxs-lookup"><span data-stu-id="7ef24-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="7ef24-139">Nastavte **šířka** vlastnost na 500.</span><span class="sxs-lookup"><span data-stu-id="7ef24-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="7ef24-140">Na **Text** zadejte neproporcionálního písma, jako je například Lucida Console nebo globální neproporcionální.</span><span class="sxs-lookup"><span data-stu-id="7ef24-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="7ef24-141">Zvýrazněte **tlačítko** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7ef24-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7ef24-142">Nastavte **název** vlastnost `startButton`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="7ef24-143">Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **spustit**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="7ef24-144">Pozice textového pole a tlačítko tak, aby obsahovat **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="7ef24-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="7ef24-145">Další informace o WPF návrháře XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7ef24-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="7ef24-146"><a name="AddRef"></a>Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="7ef24-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="7ef24-147">V **Průzkumníku**, zvýrazněte názvem vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="7ef24-148">Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="7ef24-149">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7ef24-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="7ef24-150">V horní části dialogových oken ověřte, že je váš projekt cílení na rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="7ef24-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="7ef24-151">V **sestavení** oblasti, zvolte **Framework** Pokud již není vybraná.</span><span class="sxs-lookup"><span data-stu-id="7ef24-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="7ef24-152">V seznamu názvů, vyberte **System.Net.Http** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="7ef24-153">Vyberte **OK** tlačítko dialogové okno zavřete.</span><span class="sxs-lookup"><span data-stu-id="7ef24-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="7ef24-154"><a name="usingDir"></a>Chcete-li přidat potřebné pomocí direktiv</span><span class="sxs-lookup"><span data-stu-id="7ef24-154"><a name="usingDir"></a> To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="7ef24-155">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="7ef24-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="7ef24-156">Přidejte následující `using` direktivy v horní části souboru kódu, pokud nejsou již existuje.</span><span class="sxs-lookup"><span data-stu-id="7ef24-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="7ef24-157"><a name="synchronous"></a>Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="7ef24-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="7ef24-158">V okně návrhu MainWindow.xaml, dvakrát klikněte **spustit** tlačítko vytvořte `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="7ef24-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="7ef24-159">V MainWindow.xaml.cs, zkopírujte následující kód do textu `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="7ef24-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="7ef24-160">Kód volá metody, která řídí aplikace, `SumPageSizes`a zobrazí zprávu, když se vrátí ovládací prvek `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="7ef24-161">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="7ef24-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="7ef24-162">`SumPageSizes`, který získá seznam adres URL webové stránky z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7ef24-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="7ef24-163">`SetUpURLList`, který provede a vrátí seznam hodnot webové adresy.</span><span class="sxs-lookup"><span data-stu-id="7ef24-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="7ef24-164">`GetURLContents`, který stáhne obsah každý web a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="7ef24-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="7ef24-165">`DisplayResults`, který zobrazí počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7ef24-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="7ef24-166">Zkopírujte následující čtyři metody a vložte je v části `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="7ef24-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
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
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="7ef24-167"><a name="testSynch"></a>K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="7ef24-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="7ef24-168">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7ef24-169">By se zobrazit výstup, který vypadá takto: v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="7ef24-170">Všimněte si, že bude trvat několik sekund zobrazí počty.</span><span class="sxs-lookup"><span data-stu-id="7ef24-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="7ef24-171">Během této doby je blokována vlákna uživatelského rozhraní, kdy čeká požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="7ef24-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="7ef24-172">V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo i zavřete okno zobrazení po kliknutí **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="7ef24-173">Tyto úsilí nezdaří, dokud začít zobrazí počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ef24-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="7ef24-174">Pokud web nereaguje, nemáte žádná informace o lokality, která se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="7ef24-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="7ef24-175">Je i obtížné čekání na zastavení a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="7ef24-176"><a name="GetURLContents"></a>Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7ef24-177">Převést synchronní řešení asynchronní řešení, je nejlepší místo k spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webové .</span><span class="sxs-lookup"><span data-stu-id="7ef24-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="7ef24-178">Rozhraní .NET Framework usnadňuje převod zadáním asynchronní verze obě metody.</span><span class="sxs-lookup"><span data-stu-id="7ef24-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="7ef24-179">Další informace o metodách, které se používají v `GetURLContents`, najdete v části <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="7ef24-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ef24-180">Jak budete postupovat podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7ef24-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="7ef24-181">Můžete je ignorovat a pokračovat návodu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="7ef24-182">Změnit metodu, která je volána v třetím řádku `GetURLContents` z `GetResponse` pro asynchronní, založený na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7ef24-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="7ef24-183">`GetResponseAsync`Vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="7ef24-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7ef24-184">V takovém případě *návratový proměnnou úloh*, `TResult`, má typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="7ef24-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="7ef24-185">Tato úloha je promise k vytvoření skutečné třídě `WebResponse` objektu po požadovaná data byla stažena a je úloha spuštěná na dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ef24-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="7ef24-186">Načíst `WebResponse` z úlohy hodnoty, použijí [await](../../../../csharp/language-reference/keywords/await.md) operátor k volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="7ef24-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="7ef24-187">`await` Operátor pozastaví provádění aktuální metody `GetURLContents`, dokud se nedokončí awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="7ef24-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="7ef24-188">Do té doby vrátí ovládací prvek volajícímu aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="7ef24-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="7ef24-189">V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="7ef24-190">Po dokončení úlohy, přislíbeném `WebResponse` objektu je jako hodnotu awaited úloh a jejich přiřazení k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="7ef24-191">Do následujících dvou příkazů o vysvětlení, co se stane, je možné oddělit předchozí příkaz.</span><span class="sxs-lookup"><span data-stu-id="7ef24-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="7ef24-192">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="7ef24-193">Pak operátor await se použije pro úlohu načíst `WebResponse` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="7ef24-194">Pokud asynchronní metody má práce uděláte, které nezávisí na dokončení úlohy, které pracují mezi těchto dvou příkazů po volání metody asynchronní a před pokračovat metodu `await` operátor platí.</span><span class="sxs-lookup"><span data-stu-id="7ef24-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="7ef24-195">Příklady najdete v tématu [postupy: paralelní provádění více webových dotazů pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="7ef24-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="7ef24-196">Protože jste přidali `await` dojde k chybě kompilátoru operátor v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="7ef24-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="7ef24-197">Operátor mohou být používány pouze metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7ef24-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7ef24-198">Ignorovat chybu při opakováním kroků převod nahradit volání `CopyTo` pomocí volání `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="7ef24-199">Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ef24-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="7ef24-200">`CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů na její argument `content`a nevrací smysluplný hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="7ef24-201">V synchronní verzi volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="7ef24-202">Asynchronní verzi `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="7ef24-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="7ef24-203">Úloha funguje jako "Task(void)" a umožňuje metody být očekáváno.</span><span class="sxs-lookup"><span data-stu-id="7ef24-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="7ef24-204">Použít `Await` nebo `await` k volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="7ef24-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="7ef24-205">Předchozí příkaz zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="7ef24-206">Všechno, co zůstane v `GetURLContents` je upravte podpis metody.</span><span class="sxs-lookup"><span data-stu-id="7ef24-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="7ef24-207">Můžete použít `await` operátor pouze v metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7ef24-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7ef24-208">Přidat modifikátor označit jako metodu *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="7ef24-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="7ef24-209">Návratový typ asynchronní metody lze pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, nebo `void` v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="7ef24-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="7ef24-210">Obvykle návratovým typem `void` se používá jenom v asynchronní obslužnou rutinu, kde `void` je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="7ef24-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="7ef24-211">V ostatních případech použijete `Task(T)` Pokud má metodu dokončené [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který vrací hodnotu zadejte T a používáte `Task` pokud dokončené metoda nevrací hodnotu smysluplný.</span><span class="sxs-lookup"><span data-stu-id="7ef24-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="7ef24-212">Si můžete představit `Task` návratový typ jako znamená "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="7ef24-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="7ef24-213">Další informace najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ef24-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="7ef24-214">Metoda `GetURLContents` má příkaz return, a příkaz vrátí pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ef24-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="7ef24-215">Návratový typ asynchronní verze je proto Task(T), kde T představuje bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="7ef24-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="7ef24-216">Proveďte následující změny v podpis metody:</span><span class="sxs-lookup"><span data-stu-id="7ef24-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="7ef24-217">Změnit návratový typ na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="7ef24-218">Podle konvence asynchronní metody mají názvy, které končí "Asynchronní,", přejmenujte metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="7ef24-219">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="7ef24-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="7ef24-220">Pomocí těchto několik změn, převod `GetURLContents` pro asynchronní metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ef24-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="7ef24-221"><a name="SumPageSizes"></a>Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-221"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7ef24-222">Opakováním kroků v předchozím postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="7ef24-223">Nejprve změnit volání `GetURLContents` pro asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="7ef24-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="7ef24-224">Změňte název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="7ef24-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="7ef24-225">Použít `await` úlohy, `GetURLContentsAsync` vrátí získat bajtů pole hodnota.</span><span class="sxs-lookup"><span data-stu-id="7ef24-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="7ef24-226">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="7ef24-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="7ef24-227">Předchozí přiřazení zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="7ef24-228">Proveďte následující změny v signatury metody:</span><span class="sxs-lookup"><span data-stu-id="7ef24-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="7ef24-229">Označit metodu s `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7ef24-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="7ef24-230">Přidejte "Asynchronní" název metody.</span><span class="sxs-lookup"><span data-stu-id="7ef24-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="7ef24-231">Neexistuje žádné proměnné návratový úkolů, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metodu neobsahuje žádné `return` příkaz.) Však musí vracet metodu `Task` být může používat await.</span><span class="sxs-lookup"><span data-stu-id="7ef24-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="7ef24-232">Proto změnit návratový typ metody z `void` k `Task`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="7ef24-233">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="7ef24-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="7ef24-234">Převod `SumPageSizes` k `SumPageSizesAsync` dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ef24-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="7ef24-235"><a name="startButton"></a>Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="7ef24-235"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7ef24-236">V obslužné rutině, změňte název metody volané z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="7ef24-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="7ef24-237">Protože `SumPageSizesAsync` je asynchronní metody, změňte kód v obslužné rutiny události pro await výsledek.</span><span class="sxs-lookup"><span data-stu-id="7ef24-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="7ef24-238">Volání `SumPageSizesAsync` odpovídá volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="7ef24-239">Vrátí volání `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="7ef24-240">Jako v předchozích postupech můžete převést volání pomocí jeden příkaz nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="7ef24-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="7ef24-241">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="7ef24-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="7ef24-242">Pokud chcete zabránit omylem nutnosti opětovného zadávání operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="7ef24-243">Tlačítko na konci obslužné rutiny události můžete znovu povolit.</span><span class="sxs-lookup"><span data-stu-id="7ef24-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="7ef24-244">Další informace o opětovné zadání najdete v tématu [zpracování vícenásobný přístup v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="7ef24-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="7ef24-245">Nakonec přidejte `async` modifikátor deklaraci tak, aby obslužná rutina události můžete await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="7ef24-246">Obvykle se nezmění názvy obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef24-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="7ef24-247">Návratový typ se nezmění na `Task` protože obslužné rutiny události musí vracet `void`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="7ef24-248">Převod projektu synchronní pro asynchronní zpracování je dokončena.</span><span class="sxs-lookup"><span data-stu-id="7ef24-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="7ef24-249"><a name="testAsynch"></a>K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="7ef24-249"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="7ef24-250">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="7ef24-251">By se zobrazit výstup, který vypadá takto: výstup synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="7ef24-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="7ef24-252">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="7ef24-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="7ef24-253">Výsledky všechny nedojde ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="7ef24-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="7ef24-254">Například obě aplikace obsahovat řádek v `startButton_Click` který vymaže textového pole.</span><span class="sxs-lookup"><span data-stu-id="7ef24-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="7ef24-255">Je cílem vymazat textové pole mezi spustí, pokud se rozhodnete **spustit** tlačítko druhý dobu, po ukazuje se, jednu sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="7ef24-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="7ef24-256">V synchronní verzi textového pole není zaškrtnuto, těsně před zobrazí počty druhý dobu, po dokončení stahování a vlákna uživatelského rozhraní může provádět další činnosti.</span><span class="sxs-lookup"><span data-stu-id="7ef24-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="7ef24-257">V asynchronní verzi textového pole vymaže hned po zvolení **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="7ef24-258">Co je nejdůležitější – vlákna uživatelského rozhraní není blokován během stahování.</span><span class="sxs-lookup"><span data-stu-id="7ef24-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="7ef24-259">Můžete přesunout nebo změňte velikost okna během stahování webové prostředky, počítají a zobrazit.</span><span class="sxs-lookup"><span data-stu-id="7ef24-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="7ef24-260">Pokud jeden z webů je pomalé nebo přestane reagovat, můžete zrušit operaci tak, že zvolíte **Zavřít** tlačítko (x v poli red v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="7ef24-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="7ef24-261"><a name="GetURLContentsAsync"></a>Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ef24-261"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="7ef24-262">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="7ef24-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="7ef24-263">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, nemá právě co potřebujete pro účely tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="7ef24-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="7ef24-264">Můžete ho místo `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="7ef24-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="7ef24-265">Prvním krokem je vytvoření `HttpClient` objektu v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="7ef24-266">Přidejte následující deklarace při spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="7ef24-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="7ef24-267">V `SumPageSizesAsync,` nahradit volání vaše `GetURLContentsAsync` metoda pomocí volání `HttpClient` metoda.</span><span class="sxs-lookup"><span data-stu-id="7ef24-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="7ef24-268">Odeberte nebo komentář `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="7ef24-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="7ef24-269">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7ef24-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7ef24-270">Chování tuto verzi projekt by měl odpovídat chování, které je popsaný v části "postup testovací asynchronní řešení", ale s i méně úsilí od vás.</span><span class="sxs-lookup"><span data-stu-id="7ef24-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="7ef24-271"><a name="BKMK_CompleteCodeExamples"></a>Příklad</span><span class="sxs-lookup"><span data-stu-id="7ef24-271"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="7ef24-272">Následující kód obsahuje úplný příklad převod synchronního asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="7ef24-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="7ef24-273">Všimněte si, že důrazně podobá řešení původní, synchronní.</span><span class="sxs-lookup"><span data-stu-id="7ef24-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7ef24-274">Následující kód obsahuje kompletní příklad řešení, která používá `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef24-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ef24-275">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ef24-275">See Also</span></span>  
 [<span data-ttu-id="7ef24-276">Ukázka asynchronního: Přístup k webové návod (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ef24-276">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="7ef24-277">asynchronní</span><span class="sxs-lookup"><span data-stu-id="7ef24-277">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="7ef24-278">await</span><span class="sxs-lookup"><span data-stu-id="7ef24-278">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="7ef24-279">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef24-279">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="7ef24-280">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef24-280">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="7ef24-281">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="7ef24-281">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="7ef24-282">Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef24-282">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="7ef24-283">Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef24-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
