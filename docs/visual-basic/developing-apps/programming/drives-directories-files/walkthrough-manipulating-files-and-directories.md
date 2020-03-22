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
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="1cca6-102">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cca6-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="1cca6-103">Tento návod poskytuje úvod k základům vstupně-videa souboru v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cca6-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="1cca6-104">Popisuje, jak vytvořit malou aplikaci, která uvádí a zkoumá textové soubory v adresáři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="1cca6-105">Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="1cca6-106">Existuje možnost zapsat informace do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="1cca6-107">Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cca6-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="1cca6-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="1cca6-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="1cca6-109">Na konci návodu je k dispozici ekvivalentní příklad, který <xref:System.IO> používá třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1cca6-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="1cca6-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="1cca6-110">To create the project</span></span>  
  
1. <span data-ttu-id="1cca6-111">V nabídce **Soubor** klepněte na položku **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="1cca6-112">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="1cca6-113">V podokně **Nainstalované šablony** rozbalte **položku Visual Basic**a klepněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="1cca6-114">V podokně **Šablony** uprostřed klepněte na **položku Aplikace Windows Forms Application**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="1cca6-115">Do pole **Název** `FileExplorer` nastavte název projektu a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1cca6-116">Visual Studio přidá projekt do **Průzkumníka řešení**a otevře se Návrhář formulářů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1cca6-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="1cca6-117">Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1cca6-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="1cca6-118">Řízení</span><span class="sxs-lookup"><span data-stu-id="1cca6-118">Control</span></span>|<span data-ttu-id="1cca6-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1cca6-119">Property</span></span>|<span data-ttu-id="1cca6-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1cca6-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="1cca6-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="1cca6-121">**ListBox**</span></span>|<span data-ttu-id="1cca6-122">**Název**</span><span class="sxs-lookup"><span data-stu-id="1cca6-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="1cca6-123">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="1cca6-123">**Button**</span></span>|<span data-ttu-id="1cca6-124">**Název**</span><span class="sxs-lookup"><span data-stu-id="1cca6-124">**Name**</span></span><br /><br /> <span data-ttu-id="1cca6-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="1cca6-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="1cca6-126">**Procházet**</span><span class="sxs-lookup"><span data-stu-id="1cca6-126">**Browse**</span></span>|  
    |<span data-ttu-id="1cca6-127">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="1cca6-127">**Button**</span></span>|<span data-ttu-id="1cca6-128">**Název**</span><span class="sxs-lookup"><span data-stu-id="1cca6-128">**Name**</span></span><br /><br /> <span data-ttu-id="1cca6-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="1cca6-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="1cca6-130">**Zkoumat**</span><span class="sxs-lookup"><span data-stu-id="1cca6-130">**Examine**</span></span>|  
    |<span data-ttu-id="1cca6-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="1cca6-131">**CheckBox**</span></span>|<span data-ttu-id="1cca6-132">**Název**</span><span class="sxs-lookup"><span data-stu-id="1cca6-132">**Name**</span></span><br /><br /> <span data-ttu-id="1cca6-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="1cca6-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="1cca6-134">**Uložit výsledky**</span><span class="sxs-lookup"><span data-stu-id="1cca6-134">**Save Results**</span></span>|  
    |<span data-ttu-id="1cca6-135">**Dialogové okno Prohlížeče složek**</span><span class="sxs-lookup"><span data-stu-id="1cca6-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="1cca6-136">**Název**</span><span class="sxs-lookup"><span data-stu-id="1cca6-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="1cca6-137">Výběr složky a seznam souborů ve složce</span><span class="sxs-lookup"><span data-stu-id="1cca6-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="1cca6-138">Vytvořte `Click` obslužnou rutinu události `browseButton` poklepáním na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="1cca6-139">Otevře se Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="1cca6-140">Přidejte následující kód `Click` do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="1cca6-141">Volání `FolderBrowserDialog1.ShowDialog` otevře dialogové okno **Vyhledat složku.**</span><span class="sxs-lookup"><span data-stu-id="1cca6-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="1cca6-142">Po kliknutí uživatele **OK**na <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> OK je vlastnost odeslána `ListFiles` jako argument metodě, která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="1cca6-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="1cca6-143">Přidejte `ListFiles` následující metodu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="1cca6-144">Tento kód nejprve vymaže **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="1cca6-145">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> pak načte kolekci řetězců, jeden pro každý soubor v adresáři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="1cca6-146">Metoda `GetFiles` přijímá argument vzor hledání k načtení souborů, které odpovídají určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="1cca6-147">V tomto příkladu jsou vráceny pouze soubory, které mají příponu TXT.</span><span class="sxs-lookup"><span data-stu-id="1cca6-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="1cca6-148">Řetězce, které jsou vráceny `GetFiles` metodou jsou pak přidány do **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="1cca6-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cca6-149">Run the application.</span></span> <span data-ttu-id="1cca6-150">Klepněte na tlačítko **Procházet.**</span><span class="sxs-lookup"><span data-stu-id="1cca6-150">Click the **Browse** button.</span></span> <span data-ttu-id="1cca6-151">V dialogovém okně **Vyhledat složku** vyhledejte složku, která obsahuje soubory TXT, a pak ji vyberte a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="1cca6-152">Obsahuje `ListBox` seznam souborů TXT ve vybrané složce.</span><span class="sxs-lookup"><span data-stu-id="1cca6-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="1cca6-153">Zastavte spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cca6-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="1cca6-154">Získání atributů souboru a obsahu z textového souboru</span><span class="sxs-lookup"><span data-stu-id="1cca6-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="1cca6-155">Vytvořte `Click` obslužnou rutinu události `examineButton` poklepáním na ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="1cca6-156">Přidejte následující kód `Click` do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="1cca6-157">Kód ověří, zda je položka `ListBox`vybrána v oblasti .</span><span class="sxs-lookup"><span data-stu-id="1cca6-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="1cca6-158">Poté získá položku cesty k `ListBox`souboru z .</span><span class="sxs-lookup"><span data-stu-id="1cca6-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="1cca6-159">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> se používá ke kontrole, zda soubor stále existuje.</span><span class="sxs-lookup"><span data-stu-id="1cca6-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="1cca6-160">Cesta k souboru je odeslána jako argument k metodě, `GetTextForOutput` která je přidána v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="1cca6-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="1cca6-161">Tato metoda vrátí řetězec, který obsahuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="1cca6-162">Informace o souboru se zobrazí v **messageboxu**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="1cca6-163">Přidejte `GetTextForOutput` následující metodu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="1cca6-164">Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodu k získání parametrů souboru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="1cca6-165">Parametry souboru jsou <xref:System.Text.StringBuilder>přidány do aplikace .</span><span class="sxs-lookup"><span data-stu-id="1cca6-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="1cca6-166">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> přečte obsah souboru <xref:System.IO.StreamReader>do .</span><span class="sxs-lookup"><span data-stu-id="1cca6-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="1cca6-167">První řádek obsahu je získán `StreamReader` z a je `StringBuilder`přidán do .</span><span class="sxs-lookup"><span data-stu-id="1cca6-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="1cca6-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cca6-168">Run the application.</span></span> <span data-ttu-id="1cca6-169">Klepněte na **tlačítko Procházet**a vyhledejte složku, která obsahuje soubory TXT.</span><span class="sxs-lookup"><span data-stu-id="1cca6-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="1cca6-170">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="1cca6-171">Vyberte soubor `ListBox`v souboru a klepněte na tlačítko **Prozkoumat**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="1cca6-172">A `MessageBox` zobrazí informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="1cca6-173">Zastavte spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cca6-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="1cca6-174">Přidání položky protokolu</span><span class="sxs-lookup"><span data-stu-id="1cca6-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="1cca6-175">Přidejte následující kód na `examineButton_Click` konec obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="1cca6-176">Kód nastaví cestu k souboru protokolu tak, aby byl soubor protokolu umístěn do stejného adresáře jako vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="1cca6-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="1cca6-177">Text položky protokolu je nastaven na aktuální datum a čas následovaný informacemi o souboru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="1cca6-178">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> s argumentem `append` nastaveným na `True`, se používá k vytvoření položky protokolu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="1cca6-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cca6-179">Run the application.</span></span> <span data-ttu-id="1cca6-180">Vyhledejte textový soubor, zaškrtněte `ListBox`v poli , zaškrtněte políčko **Uložit výsledky** a klepněte na tlačítko **Zkontrolovat**.</span><span class="sxs-lookup"><span data-stu-id="1cca6-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="1cca6-181">Ověřte, zda je `log.txt` položka protokolu zapsána do souboru.</span><span class="sxs-lookup"><span data-stu-id="1cca6-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="1cca6-182">Zastavte spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cca6-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="1cca6-183">Použití aktuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="1cca6-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="1cca6-184">`Form1_Load` Poklepáním na formulář vytvořte obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="1cca6-185">Přidejte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="1cca6-186">Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="1cca6-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="1cca6-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cca6-187">Run the application.</span></span> <span data-ttu-id="1cca6-188">Po prvním **klepnutí** se otevře dialogové okno **Vyhledat složku** v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="1cca6-189">Zastavte spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cca6-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="1cca6-190">Chcete-li selektivně povolit kontroly</span><span class="sxs-lookup"><span data-stu-id="1cca6-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="1cca6-191">Přidejte `SetEnabled` následující metodu.</span><span class="sxs-lookup"><span data-stu-id="1cca6-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="1cca6-192">Metoda `SetEnabled` povolí nebo zakáže ovládací prvky v `ListBox`závislosti na tom, zda je položka vybrána v rozhraní .</span><span class="sxs-lookup"><span data-stu-id="1cca6-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="1cca6-193">Vytvořte `SelectedIndexChanged` obslužnou rutinu události `filesListBox` poklepáním na `ListBox` ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1cca6-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="1cca6-194">Přidejte volání `SetEnabled` do `filesListBox_SelectedIndexChanged` nové obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="1cca6-195">Přidejte volání `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="1cca6-196">Přidejte volání `SetEnabled` na konci `Form1_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cca6-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="1cca6-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cca6-197">Run the application.</span></span> <span data-ttu-id="1cca6-198">Zaškrtávací políčko **Uložit výsledky** a tlačítko **Zkontrolovat** je zakázáno, pokud v aplikaci není vybraná `ListBox`položka.</span><span class="sxs-lookup"><span data-stu-id="1cca6-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="1cca6-199">Úplný příklad pomocí my.computer.filesystem</span><span class="sxs-lookup"><span data-stu-id="1cca6-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="1cca6-200">Následuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="1cca6-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="1cca6-201">Úplný příklad pomocí System.IO</span><span class="sxs-lookup"><span data-stu-id="1cca6-201">Full example using System.IO</span></span>  

 <span data-ttu-id="1cca6-202">Následující ekvivalentní příklad používá <xref:System.IO> třídy z `My.Computer.FileSystem` oboru názvů namísto použití objektů.</span><span class="sxs-lookup"><span data-stu-id="1cca6-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="1cca6-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cca6-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="1cca6-204">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1cca6-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
