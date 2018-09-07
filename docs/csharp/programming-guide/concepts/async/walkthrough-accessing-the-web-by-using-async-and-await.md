---
title: 'Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: cb628941d53957356cfa49d81fb78f16369af86b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085209"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="20bc3-102">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="20bc3-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="20bc3-103">Asynchronní programy můžete napsat snadno a intuitivně s použitím funkce async/await.</span><span class="sxs-lookup"><span data-stu-id="20bc3-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="20bc3-104">Můžete psát asynchronní kód, který vypadá jako synchronní kód a nechte kompilátor obtížné zpětného volání funkce a pokračování, které obvykle zahrnuje asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="20bc3-105">Další informace o funkci Async naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="20bc3-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="20bc3-106">Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sumarizuje počet bajtů v seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="20bc3-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="20bc3-107">Návodu poté převádí aplikaci, aby asynchronní řešení pomocí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="20bc3-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="20bc3-108">Pokud nechcete, aby k vytváření aplikací, si můžete stáhnout [asynchronní vzorek: přístup k webovému návodu (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="20bc3-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="20bc3-109">V tomto návodu dokončíte následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="20bc3-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="20bc3-110">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="20bc3-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="20bc3-111">Návrh jednoduchého hlavního okna MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="20bc3-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="20bc3-112">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="20bc3-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="20bc3-113">Chcete-li přidat nezbytné direktivy using</span><span class="sxs-lookup"><span data-stu-id="20bc3-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="20bc3-114">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="20bc3-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="20bc3-115">Otestování synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="20bc3-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="20bc3-116">Převedení metody GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="20bc3-117">Převedení metody SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="20bc3-118">Převedení metody startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="20bc3-119">Otestování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="20bc3-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="20bc3-120">Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="20bc3-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="20bc3-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="20bc3-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  <span data-ttu-id="20bc3-122">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="20bc3-122">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="20bc3-123">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="20bc3-123">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="20bc3-124">Spusťte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20bc3-124">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="20bc3-125">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-125">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="20bc3-126">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="20bc3-126">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="20bc3-127">V **nainstalované šablony** podokně zvolte Visual C# a pak zvolte **aplikace WPF** ze seznamu typů projektů.</span><span class="sxs-lookup"><span data-stu-id="20bc3-127">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="20bc3-128">V **název** textové pole, zadejte `AsyncExampleWPF`a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-128">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="20bc3-129">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-129">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="20bc3-130">Návrh jednoduchého hlavního okna MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="20bc3-130">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="20bc3-131">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-131">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="20bc3-132">Pokud **nástrojů** okně není zobrazena, otevřete **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-132">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="20bc3-133">Přidat **tlačítko** ovládacího prvku a **textového pole** ovládací prvek **hlavního okna MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="20bc3-133">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="20bc3-134">Zvýrazněte **TextBox** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="20bc3-134">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="20bc3-135">Nastavte **název** vlastnost `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-135">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="20bc3-136">Nastavte **výška** vlastnost na 250.</span><span class="sxs-lookup"><span data-stu-id="20bc3-136">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="20bc3-137">Nastavte **šířka** vlastnost na hodnotu 500.</span><span class="sxs-lookup"><span data-stu-id="20bc3-137">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="20bc3-138">Na **Text** kartu, zadejte neproporcionální písmo jako Arial konzoly nebo globální neproporcionálním písmem v.</span><span class="sxs-lookup"><span data-stu-id="20bc3-138">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="20bc3-139">Zvýrazněte **tlačítko** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="20bc3-139">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="20bc3-140">Nastavte **název** vlastnost `startButton`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-140">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="20bc3-141">Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **Start**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-141">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="20bc3-142">Umístěte do textového pole a tlačítko tak, aby oba se objeví v **hlavního okna MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="20bc3-142">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="20bc3-143">Další informace o Návrhář WPF XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="20bc3-143">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="20bc3-144">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="20bc3-144">To add a reference</span></span>  
  
1.  <span data-ttu-id="20bc3-145">V **Průzkumníka řešení**, vyberte název vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-145">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="20bc3-146">V panelu nabídky zvolte **projektu**, **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-146">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="20bc3-147">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="20bc3-147">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="20bc3-148">V horní části dialogového okna ověřte, že váš projekt je cílen na verzi rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="20bc3-148">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="20bc3-149">V **sestavení** oblasti, zvolte **Framework** Pokud není již vybrána.</span><span class="sxs-lookup"><span data-stu-id="20bc3-149">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="20bc3-150">Vyberte v seznamu názvů **System.Net.Http** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-150">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="20bc3-151">Zvolte **OK** tlačítka zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="20bc3-151">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> <span data-ttu-id="20bc3-152">Chcete-li přidat nezbytné direktivy using</span><span class="sxs-lookup"><span data-stu-id="20bc3-152">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="20bc3-153">V **Průzkumníka řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="20bc3-153">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="20bc3-154">Přidejte následující `using` direktivy v horní části souboru kódu, pokud již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="20bc3-154">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="20bc3-155">Vytvoření synchronní aplikace</span><span class="sxs-lookup"><span data-stu-id="20bc3-155">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="20bc3-156">V okně návrhu, MainWindow.xaml, dvakrát klikněte **Start** pro vytvoření `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="20bc3-156">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="20bc3-157">V MainWindow.xaml.cs, zkopírujte následující kód do hlavní části `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="20bc3-157">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="20bc3-158">Kód volá metodu, která řídí aplikaci, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-158">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="20bc3-159">Kód pro synchronní řešení obsahuje následující čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="20bc3-159">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="20bc3-160">`SumPageSizes`, která načte seznam adres URL webové stránky z `SetUpURLList` a pak zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="20bc3-160">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="20bc3-161">`SetUpURLList`, který provede a vrátí seznam webové adresy.</span><span class="sxs-lookup"><span data-stu-id="20bc3-161">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="20bc3-162">`GetURLContents`, který stáhne obsah každého webu a vrátí obsah jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="20bc3-162">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="20bc3-163">`DisplayResults`, který zobrazuje počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="20bc3-163">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="20bc3-164">Následující čtyři metody zkopírujte a vložte je za `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="20bc3-164">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
###  <a name="testSynch"></a> <span data-ttu-id="20bc3-165">Otestování synchronního řešení</span><span class="sxs-lookup"><span data-stu-id="20bc3-165">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="20bc3-166">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-166">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="20bc3-167">By se zobrazit výstup, který vypadá podobně jako v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-167">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="20bc3-168">Všimněte si, že trvá několik sekund zobrazí počty.</span><span class="sxs-lookup"><span data-stu-id="20bc3-168">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="20bc3-169">Během této doby vlákno uživatelského rozhraní je blokována během čekání požadované prostředky ke stažení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-169">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="20bc3-170">V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo dokonce zavřete okno zobrazení po zvolení **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-170">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="20bc3-171">Tyto aktivity dál rozšiřuji neúspěšné, dokud se začnou objevovat počtu bajtů.</span><span class="sxs-lookup"><span data-stu-id="20bc3-171">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="20bc3-172">Pokud web nereaguje, je nutné žádná zpráva o které lokalitě se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="20bc3-172">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="20bc3-173">Je obtížné i zastavte čekání a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-173">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="20bc3-174">Převedení metody GetURLContents na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-174">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="20bc3-175">Převést synchronní řešení na asynchronní řešení, je nejlepším místem pro spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> – metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje na web .</span><span class="sxs-lookup"><span data-stu-id="20bc3-175">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="20bc3-176">Rozhraní .NET Framework zjednodušuje převod zadáním asynchronní verze obě metody.</span><span class="sxs-lookup"><span data-stu-id="20bc3-176">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="20bc3-177">Další informace o metodách, které se používají v `GetURLContents`, naleznete v tématu <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="20bc3-177">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20bc3-178">Jak budete postupovat podle kroků v tomto názorném postupu se zobrazí několik chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="20bc3-178">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="20bc3-179">Můžete je ignorovat a pokračovat v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-179">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="20bc3-180">Změnit metodu, která je volána v třetí řádek `GetURLContents` z `GetResponse` na asynchronní, založené na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="20bc3-180">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="20bc3-181">`GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="20bc3-181">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="20bc3-182">V takovém případě *úloh návratové*, `TResult`, má typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="20bc3-182">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="20bc3-183">Úkol je příslib z k vytvoření skutečný `WebResponse` objektu po stažení požadovaných dat a je úloha spuštěná na dokončení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-183">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="20bc3-184">Načíst `WebResponse` hodnoty z úlohy, použijte [await](../../../../csharp/language-reference/keywords/await.md) operátor volání `GetResponseAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="20bc3-184">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="20bc3-185">`await` Operátor pozastaví vykonávání aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="20bc3-185">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="20bc3-186">Mezitím se ovládací prvek vrátí volajícímu metody, aktuální.</span><span class="sxs-lookup"><span data-stu-id="20bc3-186">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="20bc3-187">V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-187">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="20bc3-188">Úloha dokončení přislíbeném `WebResponse` objekt je vytvořen jako hodnota očekávané úlohy a přiřazená k proměnné `response`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-188">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="20bc3-189">Předchozí příkaz je možné rozdělit na následující dva příkazy o vysvětlení, co se stane.</span><span class="sxs-lookup"><span data-stu-id="20bc3-189">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="20bc3-190">Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-190">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="20bc3-191">Pak operátor await se použije na úlohu k načtení `WebResponse` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-191">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="20bc3-192">Pokud asynchronní metoda má práce, která nezávisí na dokončení úlohy, metoda může pokračovat v práci mezi tyto dva příkazy po volání metody async a před `await` je použit operátor.</span><span class="sxs-lookup"><span data-stu-id="20bc3-192">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="20bc3-193">Příklady najdete v tématu [postupy: paralelní provádění více webových požadavků pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření návodu úloh pomocí metody Task.whenall (C#) asynchronních](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="20bc3-193">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="20bc3-194">Vzhledem k tomu, že jste přidali `await` dojde k chybě kompilátoru operátor v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="20bc3-194">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="20bc3-195">Operátor, který lze použít pouze v metodách, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="20bc3-195">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="20bc3-196">Ignorovat chybu, zatímco nahraďte volání kroky převod `CopyTo` voláním `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-196">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="20bc3-197">Změnit název metody, která je volána k <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="20bc3-197">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="20bc3-198">`CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů do svého argumentu, `content`a nevrací smysluplnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-198">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="20bc3-199">Synchronní verze volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-199">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="20bc3-200">Asynchronní verze `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="20bc3-200">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="20bc3-201">Úloha funkce jako "Task(void)" a umožňuje metodu k ní použít operátor await.</span><span class="sxs-lookup"><span data-stu-id="20bc3-201">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="20bc3-202">Použít `Await` nebo `await` volání `CopyToAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="20bc3-202">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="20bc3-203">Předchozí příkaz zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-203">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="20bc3-204">Všechno, zůstane do `GetURLContents` je upravte podpis metody.</span><span class="sxs-lookup"><span data-stu-id="20bc3-204">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="20bc3-205">Můžete použít `await` operátor pouze v metodách, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="20bc3-205">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="20bc3-206">Přidat modifikátor k označení metody jako *asynchronní metoda*, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="20bc3-206">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="20bc3-207">Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, nebo `void` v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="20bc3-207">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="20bc3-208">Obvykle, návratový typ `void` se používá jenom v asynchronní obslužnou rutinu události, kde `void` je povinný.</span><span class="sxs-lookup"><span data-stu-id="20bc3-208">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="20bc3-209">V ostatních případech použijete `Task(T)` pokud dokončené metody [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který vrátí hodnotu typu T a používáte `Task` Pokud dokončená metoda nevrací hodnotu smysluplné.</span><span class="sxs-lookup"><span data-stu-id="20bc3-209">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="20bc3-210">Můžete si představit `Task` návratový typ jako "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="20bc3-210">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="20bc3-211">Další informace najdete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="20bc3-211">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="20bc3-212">Metoda `GetURLContents` disponuje návratovým příkazem, a příkaz vrátí pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="20bc3-212">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="20bc3-213">Návratový typ asynchronní verze je proto Task(T), kde T je bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="20bc3-213">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="20bc3-214">Proveďte následující změny v podpisu metody:</span><span class="sxs-lookup"><span data-stu-id="20bc3-214">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="20bc3-215">Změňte návratový typ na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-215">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="20bc3-216">Podle konvence asynchronní metody mají názvy, které končí slovem "Async", takže přejmenovat metodu `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-216">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="20bc3-217">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="20bc3-217">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="20bc3-218">Tyto drobné změny převodu `GetURLContents` na asynchronní metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-218">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="20bc3-219">Převedení metody SumPageSizes na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-219">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="20bc3-220">Zopakujte kroky z předchozího postupu pro `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-220">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="20bc3-221">Nejprve změňte volání `GetURLContents` pro asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="20bc3-221">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="20bc3-222">Změnit název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="20bc3-222">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="20bc3-223">Použít `await` úkolu, který `GetURLContentsAsync` hodnota pole vrátí získat bajt.</span><span class="sxs-lookup"><span data-stu-id="20bc3-223">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="20bc3-224">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="20bc3-224">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="20bc3-225">Dřívější přiřazení zkrátí následující dva řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="20bc3-225">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="20bc3-226">Proveďte následující změny v podpisu metody:</span><span class="sxs-lookup"><span data-stu-id="20bc3-226">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="20bc3-227">Označení metody `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="20bc3-227">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="20bc3-228">Přidáte k názvu metody "Async".</span><span class="sxs-lookup"><span data-stu-id="20bc3-228">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="20bc3-229">Neexistuje žádná proměnná vrácené úlohy, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metoda nemá žádný `return` příkazu.) Metoda však musí vrátit `Task` bude očekávatelný.</span><span class="sxs-lookup"><span data-stu-id="20bc3-229">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="20bc3-230">Proto změnit návratový typ metody z `void` k `Task`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-230">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="20bc3-231">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="20bc3-231">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="20bc3-232">Převod `SumPageSizes` k `SumPageSizesAsync` je dokončena.</span><span class="sxs-lookup"><span data-stu-id="20bc3-232">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="20bc3-233">Převedení metody startButton_Click na asynchronní metodu</span><span class="sxs-lookup"><span data-stu-id="20bc3-233">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="20bc3-234">V obslužné rutině události změnit název volané metody z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.</span><span class="sxs-lookup"><span data-stu-id="20bc3-234">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="20bc3-235">Protože `SumPageSizesAsync` je metodou asynchronní kód v obslužné rutině události await pro čekání výsledek.</span><span class="sxs-lookup"><span data-stu-id="20bc3-235">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="20bc3-236">Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-236">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="20bc3-237">Volání se vrátí `Task`, nikoli `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-237">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="20bc3-238">Stejně jako v předchozích postupů můžete převést volání pomocí jednoho příkazu nebo dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="20bc3-238">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="20bc3-239">Následující kód znázorňuje tyto změny.</span><span class="sxs-lookup"><span data-stu-id="20bc3-239">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="20bc3-240">Chcete-li zabránit náhodnému pokuste operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-240">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="20bc3-241">Můžete znovu povolit tlačítko na konci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="20bc3-241">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="20bc3-242">Další informace o vícenásobného přístupu najdete v tématu [zpracování vícenásobného přístupu v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="20bc3-242">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="20bc3-243">Nakonec přidejte `async` modifikátoru deklarace tak, aby obslužná rutina události může čekat `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-243">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="20bc3-244">Obvykle se nezmění názvy obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="20bc3-244">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="20bc3-245">Návratový typ není změněn na `Task` protože obslužné rutiny událostí musí vracet `void`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-245">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="20bc3-246">Dokončení převodu projektu z synchronní pro asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="20bc3-246">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="20bc3-247">Otestování asynchronního řešení</span><span class="sxs-lookup"><span data-stu-id="20bc3-247">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="20bc3-248">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-248">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="20bc3-249">By se zobrazit výstup, který se podobá výstup synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-249">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="20bc3-250">Všimněte si však následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="20bc3-250">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="20bc3-251">Výsledky všech nedojde ve stejnou dobu, po dokončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="20bc3-251">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="20bc3-252">Například obě aplikace obsahovat řádek v `startButton_Click` , který vymaže do textového pole.</span><span class="sxs-lookup"><span data-stu-id="20bc3-252">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="20bc3-253">Naším záměrem je zrušte textové pole mezi spuštění, pokud se rozhodnete **Start** tlačítko podruhé, po jednu sadu výsledků nezobrazila.</span><span class="sxs-lookup"><span data-stu-id="20bc3-253">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="20bc3-254">Synchronní verze do textového pole není zaškrtnuto, těsně před plánovaným začátkem zobrazují počty pro při druhém volání při dokončení stahování a vlákna uživatelského rozhraní je zdarma provádět další činnosti.</span><span class="sxs-lookup"><span data-stu-id="20bc3-254">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="20bc3-255">V asynchronní verze, do textového pole vymaže ihned poté, co vyberete **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-255">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="20bc3-256">Co je nejdůležitější vlákno uživatelského rozhraní není blokované, soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-256">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="20bc3-257">Můžete přecházet nebo změně velikosti okna, zatímco v průběhu stahování webové prostředky počítá a zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="20bc3-257">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="20bc3-258">Pokud některý z webů je pomalý nebo nereaguje, můžete zrušit operaci výběrem **Zavřít** tlačítko (x červená pole v pravém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="20bc3-258">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="20bc3-259">Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="20bc3-259">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="20bc3-260">Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="20bc3-260">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="20bc3-261">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, stačí provedla potřebné pro tento návod.</span><span class="sxs-lookup"><span data-stu-id="20bc3-261">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="20bc3-262">Můžete použít místo něj `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="20bc3-262">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="20bc3-263">Prvním krokem je vytvoření `HttpClient` objektů v metodě `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-263">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="20bc3-264">Na začátek metody přidejte následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="20bc3-264">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="20bc3-265">V `SumPageSizesAsync,` nahraďte volání vaše `GetURLContentsAsync` pomocí volání metody `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="20bc3-265">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="20bc3-266">Odstranit nebo okomentovat `GetURLContentsAsync` metodu, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="20bc3-266">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="20bc3-267">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="20bc3-267">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="20bc3-268">Chování této verze projektu by měl odpovídat chování, které popisuje postup "k otestování asynchronního řešení", ale s i menším úsilím od vás.</span><span class="sxs-lookup"><span data-stu-id="20bc3-268">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="20bc3-269">Příklad</span><span class="sxs-lookup"><span data-stu-id="20bc3-269">Example</span></span>  
 <span data-ttu-id="20bc3-270">Následující kód obsahuje úplný příklad převod ze synchronního na asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metodu, která jste napsali.</span><span class="sxs-lookup"><span data-stu-id="20bc3-270">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="20bc3-271">Všimněte si, že důrazně vypadá podobně jako původní, která je synchronní řešení.</span><span class="sxs-lookup"><span data-stu-id="20bc3-271">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="20bc3-272">Následující kód obsahuje úplný příklad řešení, které používá `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="20bc3-272">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20bc3-273">Viz také</span><span class="sxs-lookup"><span data-stu-id="20bc3-273">See Also</span></span>

- [<span data-ttu-id="20bc3-274">Asynchronní vzorek: Přístup k webovému návodu (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20bc3-274">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
- [<span data-ttu-id="20bc3-275">async</span><span class="sxs-lookup"><span data-stu-id="20bc3-275">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
- [<span data-ttu-id="20bc3-276">await</span><span class="sxs-lookup"><span data-stu-id="20bc3-276">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
- [<span data-ttu-id="20bc3-277">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="20bc3-277">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="20bc3-278">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="20bc3-278">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="20bc3-279">Asynchronní programování založené na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="20bc3-279">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
- [<span data-ttu-id="20bc3-280">Postupy: rozšíření návodu úloh pomocí metody Task.whenall (C#) asynchronních</span><span class="sxs-lookup"><span data-stu-id="20bc3-280">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
- [<span data-ttu-id="20bc3-281">Postupy: paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="20bc3-281">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
