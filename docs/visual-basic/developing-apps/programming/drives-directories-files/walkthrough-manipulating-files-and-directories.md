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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333810"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="66fe2-102">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66fe2-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="66fe2-103">V tomto návodu se seznámíte se základy vstupně-výstupních operací se soubory v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66fe2-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="66fe2-104">Popisuje, jak vytvořit malou aplikaci, která zobrazí a prověřuje textové soubory v adresáři.</span><span class="sxs-lookup"><span data-stu-id="66fe2-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="66fe2-105">Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu.</span><span class="sxs-lookup"><span data-stu-id="66fe2-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="66fe2-106">K dispozici je možnost zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="66fe2-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="66fe2-107">Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66fe2-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="66fe2-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="66fe2-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="66fe2-109">Na konci tohoto návodu je k dispozici podobný příklad, který používá třídy z oboru názvů <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="66fe2-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="66fe2-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="66fe2-110">To create the project</span></span>  
  
1. <span data-ttu-id="66fe2-111">V nabídce **soubor** klikněte na příkaz **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="66fe2-112">Zobrazí se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="66fe2-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="66fe2-113">V podokně **Nainstalované šablony** rozbalte **Visual Basic**a pak klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="66fe2-114">V podokně **šablony** uprostřed klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="66fe2-115">Do pole **název** zadejte `FileExplorer` pro nastavení názvu projektu a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="66fe2-116">Visual Studio přidá projekt do **Průzkumník řešení**a otevře se Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="66fe2-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="66fe2-117">Přidejte ovládací prvky z následující tabulky do formuláře a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="66fe2-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="66fe2-118">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="66fe2-118">Control</span></span>|<span data-ttu-id="66fe2-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="66fe2-119">Property</span></span>|<span data-ttu-id="66fe2-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66fe2-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="66fe2-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="66fe2-121">**ListBox**</span></span>|<span data-ttu-id="66fe2-122">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66fe2-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="66fe2-123">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="66fe2-123">**Button**</span></span>|<span data-ttu-id="66fe2-124">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66fe2-124">**Name**</span></span><br /><br /> <span data-ttu-id="66fe2-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="66fe2-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="66fe2-126">**Hlíží**</span><span class="sxs-lookup"><span data-stu-id="66fe2-126">**Browse**</span></span>|  
    |<span data-ttu-id="66fe2-127">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="66fe2-127">**Button**</span></span>|<span data-ttu-id="66fe2-128">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66fe2-128">**Name**</span></span><br /><br /> <span data-ttu-id="66fe2-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="66fe2-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="66fe2-130">**Zkontrolujte**</span><span class="sxs-lookup"><span data-stu-id="66fe2-130">**Examine**</span></span>|  
    |<span data-ttu-id="66fe2-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="66fe2-131">**CheckBox**</span></span>|<span data-ttu-id="66fe2-132">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66fe2-132">**Name**</span></span><br /><br /> <span data-ttu-id="66fe2-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="66fe2-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="66fe2-134">**Uložit výsledky**</span><span class="sxs-lookup"><span data-stu-id="66fe2-134">**Save Results**</span></span>|  
    |<span data-ttu-id="66fe2-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="66fe2-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="66fe2-136">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66fe2-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="66fe2-137">Výběr složky a vypsání souborů ve složce</span><span class="sxs-lookup"><span data-stu-id="66fe2-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="66fe2-138">Vytvořte obslužnou rutinu události `Click` pro `browseButton` dvojitým kliknutím na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="66fe2-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="66fe2-139">Otevře se Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="66fe2-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="66fe2-140">Do obslužné rutiny události `Click` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66fe2-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="66fe2-141">Volání `FolderBrowserDialog1.ShowDialog` otevře dialogové okno **Vyhledat složku** .</span><span class="sxs-lookup"><span data-stu-id="66fe2-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="66fe2-142">Poté, co uživatel klikne na **tlačítko OK**, je vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> odeslána jako argument metodě `ListFiles`, která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="66fe2-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="66fe2-143">Přidejte následující metodu `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="66fe2-144">Tento kód nejprve vymaže **seznam**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="66fe2-145">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> potom načte kolekci řetězců, jednu pro každý soubor v adresáři.</span><span class="sxs-lookup"><span data-stu-id="66fe2-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="66fe2-146">Metoda `GetFiles` akceptuje argument vyhledávacího vzoru pro načtení souborů, které odpovídají konkrétnímu vzoru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="66fe2-147">V tomto příkladu jsou vráceny pouze soubory, které mají příponu. txt.</span><span class="sxs-lookup"><span data-stu-id="66fe2-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="66fe2-148">Řetězce, které jsou vráceny metodou `GetFiles`, jsou poté **přidány do seznamu.**</span><span class="sxs-lookup"><span data-stu-id="66fe2-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="66fe2-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66fe2-149">Run the application.</span></span> <span data-ttu-id="66fe2-150">Klikněte na tlačítko **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="66fe2-150">Click the **Browse** button.</span></span> <span data-ttu-id="66fe2-151">V dialogovém okně **Vyhledat složku** přejděte do složky, která obsahuje soubory. txt, a pak vyberte složku a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="66fe2-152">`ListBox` obsahuje seznam souborů. txt ve vybrané složce.</span><span class="sxs-lookup"><span data-stu-id="66fe2-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="66fe2-153">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="66fe2-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="66fe2-154">Získání atributů souboru a obsahu z textového souboru</span><span class="sxs-lookup"><span data-stu-id="66fe2-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="66fe2-155">Vytvořte obslužnou rutinu události `Click` pro `examineButton` dvojitým kliknutím na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="66fe2-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="66fe2-156">Do obslužné rutiny události `Click` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66fe2-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="66fe2-157">Kód ověřuje, zda je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="66fe2-158">Poté získá položku cesty k souboru z `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="66fe2-159">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> slouží ke kontrole, zda soubor stále existuje.</span><span class="sxs-lookup"><span data-stu-id="66fe2-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="66fe2-160">Cesta k souboru je odeslána jako argument metody `GetTextForOutput`, která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="66fe2-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="66fe2-161">Tato metoda vrátí řetězec, který obsahuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="66fe2-162">Informace o souboru se zobrazí v **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="66fe2-163">Přidejte následující metodu `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="66fe2-164">Kód používá metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> k získání parametrů souboru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="66fe2-165">Parametry souboru jsou přidány do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="66fe2-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="66fe2-166">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> přečte obsah souboru do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="66fe2-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="66fe2-167">První řádek obsahu se získá z `StreamReader` a přidá se do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="66fe2-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66fe2-168">Run the application.</span></span> <span data-ttu-id="66fe2-169">Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory. txt.</span><span class="sxs-lookup"><span data-stu-id="66fe2-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="66fe2-170">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="66fe2-171">Vyberte soubor v `ListBox`a pak klikněte na **prošetřit**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="66fe2-172">`MessageBox` zobrazí informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="66fe2-173">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="66fe2-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="66fe2-174">Přidání položky protokolu</span><span class="sxs-lookup"><span data-stu-id="66fe2-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="66fe2-175">Přidejte následující kód na konec obslužné rutiny události `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="66fe2-176">Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu do stejného adresáře jako u vybraného souboru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="66fe2-177">Text položky protokolu je nastaven na aktuální datum a čas, po kterém následují informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="66fe2-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="66fe2-178">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> s argumentem `append` nastaveným na `True`slouží k vytvoření položky protokolu.</span><span class="sxs-lookup"><span data-stu-id="66fe2-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="66fe2-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66fe2-179">Run the application.</span></span> <span data-ttu-id="66fe2-180">Přejděte k textovému souboru, vyberte ho v `ListBox`, zaškrtněte políčko **Uložit výsledky** a potom klikněte na **prošetřit**.</span><span class="sxs-lookup"><span data-stu-id="66fe2-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="66fe2-181">Ověřte, že položka protokolu je zapsána do souboru `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="66fe2-182">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="66fe2-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="66fe2-183">Použití aktuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="66fe2-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="66fe2-184">Vytvořte obslužnou rutinu události pro `Form1_Load` dvojitým kliknutím na formulář.</span><span class="sxs-lookup"><span data-stu-id="66fe2-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="66fe2-185">Přidejte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="66fe2-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="66fe2-186">Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="66fe2-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="66fe2-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66fe2-187">Run the application.</span></span> <span data-ttu-id="66fe2-188">Když kliknete na tlačítko **Procházet** poprvé, otevře se dialogové okno **Vyhledat složku** do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="66fe2-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="66fe2-189">Zastavit běh aplikace</span><span class="sxs-lookup"><span data-stu-id="66fe2-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="66fe2-190">Selektivní povolení ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="66fe2-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="66fe2-191">Přidejte následující metodu `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="66fe2-192">Metoda `SetEnabled` povoluje nebo zakazuje ovládací prvky v závislosti na tom, zda je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="66fe2-193">Vytvořte obslužnou rutinu události `SelectedIndexChanged` pro `filesListBox` dvojitým kliknutím na ovládací prvek `ListBox` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="66fe2-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="66fe2-194">Přidejte volání `SetEnabled` v nové obslužné rutině události `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="66fe2-195">Přidejte volání `SetEnabled` na konci obslužné rutiny události `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="66fe2-196">Přidejte volání `SetEnabled` na konci obslužné rutiny události `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="66fe2-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66fe2-197">Run the application.</span></span> <span data-ttu-id="66fe2-198">Zaškrtávací políčko **Uložit výsledky** a tlačítko **Prohledat** jsou zakázány, pokud položka není vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="66fe2-199">Úplný příklad použití My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="66fe2-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="66fe2-200">Toto je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="66fe2-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="66fe2-201">Úplný příklad použití System.IO</span><span class="sxs-lookup"><span data-stu-id="66fe2-201">Full example using System.IO</span></span>  

 <span data-ttu-id="66fe2-202">Následující podobný příklad používá třídy z oboru názvů <xref:System.IO> namísto použití objektů `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="66fe2-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="66fe2-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66fe2-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="66fe2-204">Návod: Práce se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="66fe2-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
