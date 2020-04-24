---
title: Práce se soubory a adresáři
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333810"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="fc977-102">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc977-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="fc977-103">V tomto návodu se seznámíte se základy vstupně-výstupních operací se soubory v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc977-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="fc977-104">Popisuje, jak vytvořit malou aplikaci, která zobrazí a prověřuje textové soubory v adresáři.</span><span class="sxs-lookup"><span data-stu-id="fc977-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="fc977-105">Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu.</span><span class="sxs-lookup"><span data-stu-id="fc977-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="fc977-106">K dispozici je možnost zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="fc977-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="fc977-107">Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc977-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="fc977-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="fc977-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="fc977-109">Na konci tohoto návodu je k dispozici podobný příklad, který používá třídy z <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc977-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="fc977-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fc977-110">To create the project</span></span>  
  
1. <span data-ttu-id="fc977-111">V nabídce **soubor** klikněte na příkaz **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fc977-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="fc977-112">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fc977-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="fc977-113">V podokně **Nainstalované šablony** rozbalte **Visual Basic**a pak klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="fc977-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="fc977-114">V podokně **šablony** uprostřed klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="fc977-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="fc977-115">Do pole **název** zadejte `FileExplorer` název projektu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc977-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fc977-116">Visual Studio přidá projekt do **Průzkumník řešení**a otevře se Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="fc977-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="fc977-117">Přidejte ovládací prvky z následující tabulky do formuláře a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="fc977-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="fc977-118">Řízení</span><span class="sxs-lookup"><span data-stu-id="fc977-118">Control</span></span>|<span data-ttu-id="fc977-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fc977-119">Property</span></span>|<span data-ttu-id="fc977-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fc977-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="fc977-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="fc977-121">**ListBox**</span></span>|<span data-ttu-id="fc977-122">**Název**</span><span class="sxs-lookup"><span data-stu-id="fc977-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="fc977-123">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="fc977-123">**Button**</span></span>|<span data-ttu-id="fc977-124">**Název**</span><span class="sxs-lookup"><span data-stu-id="fc977-124">**Name**</span></span><br /><br /> <span data-ttu-id="fc977-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc977-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="fc977-126">**Procházet**</span><span class="sxs-lookup"><span data-stu-id="fc977-126">**Browse**</span></span>|  
    |<span data-ttu-id="fc977-127">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="fc977-127">**Button**</span></span>|<span data-ttu-id="fc977-128">**Název**</span><span class="sxs-lookup"><span data-stu-id="fc977-128">**Name**</span></span><br /><br /> <span data-ttu-id="fc977-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc977-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="fc977-130">**Zkontrolujte**</span><span class="sxs-lookup"><span data-stu-id="fc977-130">**Examine**</span></span>|  
    |<span data-ttu-id="fc977-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="fc977-131">**CheckBox**</span></span>|<span data-ttu-id="fc977-132">**Název**</span><span class="sxs-lookup"><span data-stu-id="fc977-132">**Name**</span></span><br /><br /> <span data-ttu-id="fc977-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc977-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="fc977-134">**Uložit výsledky**</span><span class="sxs-lookup"><span data-stu-id="fc977-134">**Save Results**</span></span>|  
    |<span data-ttu-id="fc977-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="fc977-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="fc977-136">**Název**</span><span class="sxs-lookup"><span data-stu-id="fc977-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="fc977-137">Výběr složky a vypsání souborů ve složce</span><span class="sxs-lookup"><span data-stu-id="fc977-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="fc977-138">Vytvořte obslužnou `Click` rutinu události `browseButton` pro dvojitým kliknutím na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fc977-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="fc977-139">Otevře se Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="fc977-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="fc977-140">Přidejte následující kód do obslužné rutiny `Click` události.</span><span class="sxs-lookup"><span data-stu-id="fc977-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="fc977-141">`FolderBrowserDialog1.ShowDialog` Volání otevře dialogové okno **Vyhledat složku** .</span><span class="sxs-lookup"><span data-stu-id="fc977-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="fc977-142">Poté, co uživatel klikne na <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> **tlačítko OK**, je vlastnost odeslána jako argument `ListFiles` metodě, která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="fc977-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="fc977-143">Přidejte následující `ListFiles` metodu.</span><span class="sxs-lookup"><span data-stu-id="fc977-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="fc977-144">Tento kód nejprve vymaže **seznam**.</span><span class="sxs-lookup"><span data-stu-id="fc977-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="fc977-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda potom načte kolekci řetězců, jednu pro každý soubor v adresáři.</span><span class="sxs-lookup"><span data-stu-id="fc977-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="fc977-146">`GetFiles` Metoda přijímá argument vzor hledání, který načte soubory, které odpovídají konkrétnímu vzoru.</span><span class="sxs-lookup"><span data-stu-id="fc977-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="fc977-147">V tomto příkladu jsou vráceny pouze soubory, které mají příponu. txt.</span><span class="sxs-lookup"><span data-stu-id="fc977-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="fc977-148">Řetězce, které jsou vráceny `GetFiles` metodou, jsou poté přidány do seznamu. **ListBox**</span><span class="sxs-lookup"><span data-stu-id="fc977-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="fc977-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc977-149">Run the application.</span></span> <span data-ttu-id="fc977-150">Klikněte na tlačítko **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="fc977-150">Click the **Browse** button.</span></span> <span data-ttu-id="fc977-151">V dialogovém okně **Vyhledat složku** přejděte do složky, která obsahuje soubory. txt, a pak vyberte složku a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc977-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="fc977-152">`ListBox` Obsahuje seznam souborů. txt ve vybrané složce.</span><span class="sxs-lookup"><span data-stu-id="fc977-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="fc977-153">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="fc977-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="fc977-154">Získání atributů souboru a obsahu z textového souboru</span><span class="sxs-lookup"><span data-stu-id="fc977-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="fc977-155">Vytvořte obslužnou `Click` rutinu události `examineButton` pro dvojitým kliknutím na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fc977-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="fc977-156">Přidejte následující kód do obslužné rutiny `Click` události.</span><span class="sxs-lookup"><span data-stu-id="fc977-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="fc977-157">Kód ověřuje, zda je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="fc977-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="fc977-158">Pak získá položku cesty k souboru z `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="fc977-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="fc977-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda slouží ke kontrole, zda soubor stále existuje.</span><span class="sxs-lookup"><span data-stu-id="fc977-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="fc977-160">Cesta k souboru je odeslána jako argument `GetTextForOutput` metodě, která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="fc977-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="fc977-161">Tato metoda vrátí řetězec, který obsahuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="fc977-162">Informace o souboru se zobrazí v **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="fc977-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="fc977-163">Přidejte následující `GetTextForOutput` metodu.</span><span class="sxs-lookup"><span data-stu-id="fc977-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="fc977-164">Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodu pro získání parametrů souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="fc977-165">Parametry souboru jsou přidány do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="fc977-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="fc977-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda načte obsah souboru do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="fc977-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="fc977-167">První řádek obsahu je získán z `StreamReader` a je přidán do. `StringBuilder`</span><span class="sxs-lookup"><span data-stu-id="fc977-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="fc977-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc977-168">Run the application.</span></span> <span data-ttu-id="fc977-169">Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory. txt.</span><span class="sxs-lookup"><span data-stu-id="fc977-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="fc977-170">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc977-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="fc977-171">Vyberte soubor v `ListBox`nástroji a klikněte na tlačítko **Prohledat**.</span><span class="sxs-lookup"><span data-stu-id="fc977-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="fc977-172">A `MessageBox` zobrazuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="fc977-173">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="fc977-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="fc977-174">Přidání položky protokolu</span><span class="sxs-lookup"><span data-stu-id="fc977-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="fc977-175">Přidejte následující kód na konec obslužné rutiny `examineButton_Click` události.</span><span class="sxs-lookup"><span data-stu-id="fc977-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="fc977-176">Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu do stejného adresáře jako u vybraného souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="fc977-177">Text položky protokolu je nastaven na aktuální datum a čas, po kterém následují informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="fc977-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda s `append` argumentem nastaveným na `True`slouží k vytvoření položky protokolu.</span><span class="sxs-lookup"><span data-stu-id="fc977-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="fc977-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc977-179">Run the application.</span></span> <span data-ttu-id="fc977-180">Přejděte k textovému souboru, vyberte ho v oblasti `ListBox`, zaškrtněte políčko **Uložit výsledky** a potom klikněte na **prošetřit**.</span><span class="sxs-lookup"><span data-stu-id="fc977-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="fc977-181">Ověřte, že položka protokolu je zapsána `log.txt` do souboru.</span><span class="sxs-lookup"><span data-stu-id="fc977-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="fc977-182">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="fc977-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="fc977-183">Použití aktuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="fc977-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="fc977-184">Vytvořte obslužnou rutinu události `Form1_Load` pro dvojitým kliknutím na formulář.</span><span class="sxs-lookup"><span data-stu-id="fc977-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="fc977-185">Přidejte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fc977-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="fc977-186">Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="fc977-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="fc977-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc977-187">Run the application.</span></span> <span data-ttu-id="fc977-188">Když kliknete na tlačítko **Procházet** poprvé, otevře se dialogové okno **Vyhledat složku** do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="fc977-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="fc977-189">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="fc977-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="fc977-190">Selektivní povolení ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fc977-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="fc977-191">Přidejte následující `SetEnabled` metodu.</span><span class="sxs-lookup"><span data-stu-id="fc977-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="fc977-192">`SetEnabled` Metoda povoluje nebo zakazuje ovládací prvky v závislosti na tom, zda je položka vybrána `ListBox`v.</span><span class="sxs-lookup"><span data-stu-id="fc977-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="fc977-193">Vytvořte obslužnou `SelectedIndexChanged` rutinu události `filesListBox` pro dvojitým kliknutím na `ListBox` ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fc977-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="fc977-194">Přidejte volání do `SetEnabled` nové `filesListBox_SelectedIndexChanged` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fc977-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="fc977-195">Na konec obslužné rutiny `SetEnabled` `browseButton_Click` události přidejte volání.</span><span class="sxs-lookup"><span data-stu-id="fc977-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="fc977-196">Na konec obslužné rutiny `SetEnabled` `Form1_Load` události přidejte volání.</span><span class="sxs-lookup"><span data-stu-id="fc977-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="fc977-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc977-197">Run the application.</span></span> <span data-ttu-id="fc977-198">Zaškrtávací políčko **Uložit výsledky** a tlačítko **prostudovat** jsou zakázány, pokud položka není vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="fc977-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="fc977-199">Úplný příklad použití My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="fc977-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="fc977-200">Toto je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="fc977-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="fc977-201">Úplný příklad použití System.IO</span><span class="sxs-lookup"><span data-stu-id="fc977-201">Full example using System.IO</span></span>  

 <span data-ttu-id="fc977-202">Následující podobný příklad používá třídy z <xref:System.IO> oboru názvů namísto použití `My.Computer.FileSystem` objektů.</span><span class="sxs-lookup"><span data-stu-id="fc977-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="fc977-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc977-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="fc977-204">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc977-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
