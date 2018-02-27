---
title: "Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 533cb4b342e3de3eb3143b001f5a26e36e4d79b9
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="59b2d-102">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="59b2d-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="59b2d-103">Asynchronní programy můžete napsat snadno a intuitivně najít pomocí modifikátoru async/await funkcí.</span><span class="sxs-lookup"><span data-stu-id="59b2d-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="59b2d-104">Můžete napsat asynchronní kód, který vypadá jako synchronní kódu a nechat kompilátoru zpracování funkce zpětného volání obtížné a pokračování, které obvykle zahrnuje asynchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="59b2d-105">Další informace o funkci asynchronní najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="59b2d-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="59b2d-106">Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sčítá počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="59b2d-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="59b2d-107">Průvodce potom převede aplikace pro asynchronní řešení pomocí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="59b2d-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="59b2d-108">Pokud nechcete, aby k vytváření aplikací, můžete stáhnout [asynchronní ukázka: přístup k webové návod (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="59b2d-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="59b2d-109">V tomto návodu dokončit následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="59b2d-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="59b2d-110">Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="59b2d-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="59b2d-111">Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="59b2d-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="59b2d-112">Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="59b2d-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="59b2d-113">Chcete-li přidat potřebné pomocí direktiv</span><span class="sxs-lookup"><span data-stu-id="59b2d-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="59b2d-114">Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="59b2d-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="59b2d-115">K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="59b2d-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="59b2d-116">Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="59b2d-117">Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="59b2d-118">Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="59b2d-119">K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="59b2d-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="59b2d-120">Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59b2d-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="59b2d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="59b2d-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  <span data-ttu-id="59b2d-122">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="59b2d-122">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="59b2d-123">Chcete-li vytvořit aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="59b2d-123">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="59b2d-124">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59b2d-124">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="59b2d-125">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-125">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="59b2d-126">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="59b2d-126">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="59b2d-127">V **nainstalovaných šablonách** podokně vyberte Visual C# a potom vyberte **aplikaci WPF** ze seznamu typy projektů.</span><span class="sxs-lookup"><span data-stu-id="59b2d-127">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="59b2d-128">V **název** textové pole, zadejte `AsyncExampleWPF`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-128">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="59b2d-129">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-129">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="59b2d-130">Při návrhu jednoduché MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="59b2d-130">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="59b2d-131">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="59b2d-131">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="59b2d-132">Pokud **sada nástrojů** okno není viditelný, otevřete **zobrazení** nabídce a potom zvolte **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-132">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="59b2d-133">Přidat **tlačítko** řízení a **TextBox** řídit k **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="59b2d-133">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="59b2d-134">Zvýrazněte **TextBox** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="59b2d-134">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="59b2d-135">Nastavte **název** vlastnost `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-135">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="59b2d-136">Nastavte **výška** vlastnost, která má 250.</span><span class="sxs-lookup"><span data-stu-id="59b2d-136">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="59b2d-137">Nastavte **šířka** vlastnost na 500.</span><span class="sxs-lookup"><span data-stu-id="59b2d-137">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="59b2d-138">Na **Text** zadejte neproporcionálního písma, jako je například Lucida Console nebo globální neproporcionální.</span><span class="sxs-lookup"><span data-stu-id="59b2d-138">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="59b2d-139">Zvýrazněte **tlačítko** řízení a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="59b2d-139">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="59b2d-140">Nastavte **název** vlastnost `startButton`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-140">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="59b2d-141">Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **spustit**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-141">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="59b2d-142">Pozice textového pole a tlačítko tak, aby obsahovat **MainWindow** okno.</span><span class="sxs-lookup"><span data-stu-id="59b2d-142">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="59b2d-143">Další informace o WPF návrháře XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="59b2d-143">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="59b2d-144">Chcete-li přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="59b2d-144">To add a reference</span></span>  
  
1.  <span data-ttu-id="59b2d-145">V **Průzkumníku**, zvýrazněte názvem vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-145">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="59b2d-146">Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-146">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="59b2d-147">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="59b2d-147">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="59b2d-148">V horní části dialogových oken ověřte, že je váš projekt cílení na rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="59b2d-148">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="59b2d-149">V **sestavení** oblasti, zvolte **Framework** Pokud již není vybraná.</span><span class="sxs-lookup"><span data-stu-id="59b2d-149">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="59b2d-150">V seznamu názvů, vyberte **System.Net.Http** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-150">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="59b2d-151">Vyberte **OK** tlačítko dialogové okno zavřete.</span><span class="sxs-lookup"><span data-stu-id="59b2d-151">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> <span data-ttu-id="59b2d-152">Chcete-li přidat potřebné pomocí direktiv</span><span class="sxs-lookup"><span data-stu-id="59b2d-152">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="59b2d-153">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="59b2d-153">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="59b2d-154">Přidejte následující `using` direktivy v horní části souboru kódu, pokud nejsou již existuje.</span><span class="sxs-lookup"><span data-stu-id="59b2d-154">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="59b2d-155">Chcete-li vytvořit synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="59b2d-155">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="59b2d-156">V okně návrhu MainWindow.xaml, dvakrát klikněte **spustit** tlačítko vytvořte `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="59b2d-156">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="59b2d-157">V MainWindow.xaml.cs, zkopírujte následující kód do textu `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="59b2d-157">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="59b2d-158">Kód volá metody, která řídí aplikace, `SumPageSizes`a zobrazí zprávu, když se vrátí ovládací prvek `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-158">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="59b2d-159">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="59b2d-159">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="59b2d-160">`SumPageSizes`, který získá seznam adres URL webové stránky z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="59b2d-160">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="59b2d-161">`SetUpURLList`, který provede a vrátí seznam hodnot webové adresy.</span><span class="sxs-lookup"><span data-stu-id="59b2d-161">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="59b2d-162">`GetURLContents`, který stáhne obsah každý web a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="59b2d-162">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="59b2d-163">`DisplayResults`, který zobrazí počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="59b2d-163">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="59b2d-164">Zkopírujte následující čtyři metody a vložte je v části `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="59b2d-164">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
###  <a name="testSynch"></a> <span data-ttu-id="59b2d-165">K testování synchronní řešení</span><span class="sxs-lookup"><span data-stu-id="59b2d-165">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="59b2d-166">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-166">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="59b2d-167">By se zobrazit výstup, který vypadá takto: v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-167">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="59b2d-168">Všimněte si, že bude trvat několik sekund zobrazí počty.</span><span class="sxs-lookup"><span data-stu-id="59b2d-168">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="59b2d-169">Během této doby je blokována vlákna uživatelského rozhraní, kdy čeká požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="59b2d-169">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="59b2d-170">V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo i zavřete okno zobrazení po kliknutí **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-170">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="59b2d-171">Tyto úsilí nezdaří, dokud začít zobrazí počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="59b2d-171">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="59b2d-172">Pokud web nereaguje, nemáte žádná informace o lokality, která se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="59b2d-172">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="59b2d-173">Je i obtížné čekání na zastavení a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-173">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="59b2d-174">Chcete-li převést GetURLContents asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-174">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="59b2d-175">Převést synchronní řešení asynchronní řešení, je nejlepší místo k spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webové .</span><span class="sxs-lookup"><span data-stu-id="59b2d-175">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="59b2d-176">Rozhraní .NET Framework usnadňuje převod zadáním asynchronní verze obě metody.</span><span class="sxs-lookup"><span data-stu-id="59b2d-176">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="59b2d-177">Další informace o metodách, které se používají v `GetURLContents`, najdete v části <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="59b2d-177">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59b2d-178">Jak budete postupovat podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="59b2d-178">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="59b2d-179">Můžete je ignorovat a pokračovat návodu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-179">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="59b2d-180">Změnit metodu, která je volána v třetím řádku `GetURLContents` z `GetResponse` pro asynchronní, založený na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="59b2d-180">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="59b2d-181">`GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="59b2d-181">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="59b2d-182">V takovém případě *návratový proměnnou úloh*, `TResult`, má typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="59b2d-182">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="59b2d-183">Tato úloha je promise k vytvoření skutečné třídě `WebResponse` objektu po požadovaná data byla stažena a je úloha spuštěná na dokončení.</span><span class="sxs-lookup"><span data-stu-id="59b2d-183">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="59b2d-184">Načíst `WebResponse` z úlohy hodnoty, použijí [await](../../../../csharp/language-reference/keywords/await.md) operátor k volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="59b2d-184">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="59b2d-185">`await` Operátor pozastaví provádění aktuální metody `GetURLContents`, dokud se nedokončí awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="59b2d-185">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="59b2d-186">Do té doby vrátí ovládací prvek volajícímu aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="59b2d-186">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="59b2d-187">V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-187">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="59b2d-188">Po dokončení úlohy, přislíbeném `WebResponse` objektu je jako hodnotu awaited úloh a jejich přiřazení k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-188">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="59b2d-189">Do následujících dvou příkazů o vysvětlení, co se stane, je možné oddělit předchozí příkaz.</span><span class="sxs-lookup"><span data-stu-id="59b2d-189">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="59b2d-190">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-190">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="59b2d-191">Pak operátor await se použije pro úlohu načíst `WebResponse` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-191">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="59b2d-192">Pokud asynchronní metody má práce uděláte, které nezávisí na dokončení úlohy, které pracují mezi těchto dvou příkazů po volání metody asynchronní a před pokračovat metodu `await` operátor platí.</span><span class="sxs-lookup"><span data-stu-id="59b2d-192">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="59b2d-193">Příklady najdete v tématu [postupy: paralelní provádění více webových dotazů pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="59b2d-193">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="59b2d-194">Protože jste přidali `await` dojde k chybě kompilátoru operátor v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="59b2d-194">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="59b2d-195">Operátor mohou být používány pouze metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="59b2d-195">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="59b2d-196">Ignorovat chybu při opakováním kroků převod nahradit volání `CopyTo` pomocí volání `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-196">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="59b2d-197">Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="59b2d-197">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="59b2d-198">`CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů na její argument `content`a nevrací smysluplný hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-198">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="59b2d-199">V synchronní verzi volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-199">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="59b2d-200">Asynchronní verzi `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="59b2d-200">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="59b2d-201">Úloha funguje jako "Task(void)" a umožňuje metody být očekáváno.</span><span class="sxs-lookup"><span data-stu-id="59b2d-201">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="59b2d-202">Použít `Await` nebo `await` k volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="59b2d-202">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="59b2d-203">Předchozí příkaz zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-203">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="59b2d-204">Všechno, co zůstane v `GetURLContents` je upravte podpis metody.</span><span class="sxs-lookup"><span data-stu-id="59b2d-204">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="59b2d-205">Můžete použít `await` operátor pouze v metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="59b2d-205">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="59b2d-206">Přidat modifikátor označit jako metodu *asynchronní metody*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="59b2d-206">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="59b2d-207">Návratový typ asynchronní metody lze pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, nebo `void` v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="59b2d-207">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="59b2d-208">Obvykle návratovým typem `void` se používá jenom v asynchronní obslužnou rutinu, kde `void` je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="59b2d-208">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="59b2d-209">V ostatních případech použijete `Task(T)` Pokud má metodu dokončené [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který vrací hodnotu zadejte T a používáte `Task` pokud dokončené metoda nevrací hodnotu smysluplný.</span><span class="sxs-lookup"><span data-stu-id="59b2d-209">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="59b2d-210">Si můžete představit `Task` návratový typ jako znamená "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="59b2d-210">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="59b2d-211">Další informace najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="59b2d-211">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="59b2d-212">Metoda `GetURLContents` má příkaz return, a příkaz vrátí pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="59b2d-212">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="59b2d-213">Návratový typ asynchronní verze je proto Task(T), kde T představuje bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="59b2d-213">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="59b2d-214">Proveďte následující změny v podpis metody:</span><span class="sxs-lookup"><span data-stu-id="59b2d-214">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="59b2d-215">Změnit návratový typ na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-215">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="59b2d-216">Podle konvence asynchronní metody mají názvy, které končí "Asynchronní,", přejmenujte metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-216">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="59b2d-217">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="59b2d-217">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="59b2d-218">Pomocí těchto několik změn, převod `GetURLContents` pro asynchronní metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="59b2d-218">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="59b2d-219">Chcete-li převést SumPageSizes asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-219">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="59b2d-220">Opakováním kroků v předchozím postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-220">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="59b2d-221">Nejprve změnit volání `GetURLContents` pro asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="59b2d-221">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="59b2d-222">Změňte název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="59b2d-222">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="59b2d-223">Použít `await` úlohy, `GetURLContentsAsync` vrátí získat bajtů pole hodnota.</span><span class="sxs-lookup"><span data-stu-id="59b2d-223">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="59b2d-224">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="59b2d-224">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="59b2d-225">Předchozí přiřazení zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-225">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="59b2d-226">Proveďte následující změny v signatury metody:</span><span class="sxs-lookup"><span data-stu-id="59b2d-226">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="59b2d-227">Označit metodu s `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="59b2d-227">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="59b2d-228">Přidejte "Asynchronní" název metody.</span><span class="sxs-lookup"><span data-stu-id="59b2d-228">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="59b2d-229">Neexistuje žádné proměnné návratový úkolů, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metodu neobsahuje žádné `return` příkaz.) Však musí vracet metodu `Task` být může používat await.</span><span class="sxs-lookup"><span data-stu-id="59b2d-229">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="59b2d-230">Proto změnit návratový typ metody z `void` k `Task`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-230">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="59b2d-231">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="59b2d-231">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="59b2d-232">Převod `SumPageSizes` k `SumPageSizesAsync` dokončení.</span><span class="sxs-lookup"><span data-stu-id="59b2d-232">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="59b2d-233">Chcete-li převést startButton_Click asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="59b2d-233">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="59b2d-234">V obslužné rutině, změňte název metody volané z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="59b2d-234">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="59b2d-235">Protože `SumPageSizesAsync` je asynchronní metody, změňte kód v obslužné rutiny události pro await výsledek.</span><span class="sxs-lookup"><span data-stu-id="59b2d-235">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="59b2d-236">Volání `SumPageSizesAsync` odpovídá volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-236">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="59b2d-237">Vrátí volání `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-237">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="59b2d-238">Jako v předchozích postupech můžete převést volání pomocí jeden příkaz nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="59b2d-238">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="59b2d-239">Následující kód ukazuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="59b2d-239">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="59b2d-240">Pokud chcete zabránit omylem nutnosti opětovného zadávání operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-240">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="59b2d-241">Tlačítko na konci obslužné rutiny události můžete znovu povolit.</span><span class="sxs-lookup"><span data-stu-id="59b2d-241">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="59b2d-242">Další informace o opětovné zadání najdete v tématu [zpracování vícenásobný přístup v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="59b2d-242">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="59b2d-243">Nakonec přidejte `async` modifikátor deklaraci tak, aby obslužná rutina události můžete await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-243">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="59b2d-244">Obvykle se nezmění názvy obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="59b2d-244">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="59b2d-245">Návratový typ se nezmění na `Task` protože obslužné rutiny události musí vracet `void`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-245">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="59b2d-246">Převod projektu synchronní pro asynchronní zpracování je dokončena.</span><span class="sxs-lookup"><span data-stu-id="59b2d-246">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="59b2d-247">K testování asynchronní řešení</span><span class="sxs-lookup"><span data-stu-id="59b2d-247">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="59b2d-248">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-248">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="59b2d-249">By se zobrazit výstup, který vypadá takto: výstup synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="59b2d-249">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="59b2d-250">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="59b2d-250">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="59b2d-251">Výsledky všechny nedojde ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="59b2d-251">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="59b2d-252">Například obě aplikace obsahovat řádek v `startButton_Click` který vymaže textového pole.</span><span class="sxs-lookup"><span data-stu-id="59b2d-252">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="59b2d-253">Je cílem vymazat textové pole mezi spustí, pokud se rozhodnete **spustit** tlačítko druhý dobu, po ukazuje se, jednu sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="59b2d-253">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="59b2d-254">V synchronní verzi textového pole není zaškrtnuto, těsně před zobrazí počty druhý dobu, po dokončení stahování a vlákna uživatelského rozhraní může provádět další činnosti.</span><span class="sxs-lookup"><span data-stu-id="59b2d-254">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="59b2d-255">V asynchronní verzi textového pole vymaže hned po zvolení **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-255">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="59b2d-256">Co je nejdůležitější – vlákna uživatelského rozhraní není blokován během stahování.</span><span class="sxs-lookup"><span data-stu-id="59b2d-256">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="59b2d-257">Můžete přesunout nebo změňte velikost okna během stahování webové prostředky, počítají a zobrazit.</span><span class="sxs-lookup"><span data-stu-id="59b2d-257">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="59b2d-258">Pokud jeden z webů je pomalé nebo přestane reagovat, můžete zrušit operaci tak, že zvolíte **Zavřít** tlačítko (x v poli red v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="59b2d-258">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="59b2d-259">Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59b2d-259">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="59b2d-260">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="59b2d-260">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="59b2d-261">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, nemá právě co potřebujete pro účely tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="59b2d-261">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="59b2d-262">Můžete ho místo `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="59b2d-262">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="59b2d-263">Prvním krokem je vytvoření `HttpClient` objektu v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-263">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="59b2d-264">Přidejte následující deklarace při spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="59b2d-264">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="59b2d-265">V `SumPageSizesAsync,` nahradit volání vaše `GetURLContentsAsync` metoda pomocí volání `HttpClient` metoda.</span><span class="sxs-lookup"><span data-stu-id="59b2d-265">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="59b2d-266">Odeberte nebo komentář `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="59b2d-266">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="59b2d-267">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="59b2d-267">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="59b2d-268">Chování tuto verzi projekt by měl odpovídat chování, které je popsaný v části "postup testovací asynchronní řešení", ale s i méně úsilí od vás.</span><span class="sxs-lookup"><span data-stu-id="59b2d-268">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="59b2d-269">Příklad</span><span class="sxs-lookup"><span data-stu-id="59b2d-269">Example</span></span>  
 <span data-ttu-id="59b2d-270">Následující kód obsahuje úplný příklad převod synchronního asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metoda, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="59b2d-270">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="59b2d-271">Všimněte si, že důrazně podobá řešení původní, synchronní.</span><span class="sxs-lookup"><span data-stu-id="59b2d-271">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="59b2d-272">Následující kód obsahuje kompletní příklad řešení, která používá `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="59b2d-272">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59b2d-273">Viz také</span><span class="sxs-lookup"><span data-stu-id="59b2d-273">See Also</span></span>  
 [<span data-ttu-id="59b2d-274">Ukázka asynchronního: Přístup k webové návod (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59b2d-274">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [<span data-ttu-id="59b2d-275">async</span><span class="sxs-lookup"><span data-stu-id="59b2d-275">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="59b2d-276">await</span><span class="sxs-lookup"><span data-stu-id="59b2d-276">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="59b2d-277">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="59b2d-277">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="59b2d-278">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="59b2d-278">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="59b2d-279">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="59b2d-279">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
 [<span data-ttu-id="59b2d-280">Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="59b2d-280">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="59b2d-281">Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="59b2d-281">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
