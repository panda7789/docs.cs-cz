---
title: Práce se soubory a adresáře v jazyce Visual Basic
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
ms.openlocfilehash: 4d0aac533759f8cc20ac4f19d7f0e49fef17bf56
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314682"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="ec536-102">Návod: Práce se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec536-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="ec536-103">Tento názorný postup obsahuje úvod do základní informace o souboru vstupně-výstupních operací v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ec536-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="ec536-104">Popisuje postup vytvoření malou aplikaci, která obsahuje seznam a zkoumá textových souborů v adresáři.</span><span class="sxs-lookup"><span data-stu-id="ec536-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="ec536-105">Pro každý soubor vybraný text aplikace poskytuje atributy souboru a prvního řádku obsahu.</span><span class="sxs-lookup"><span data-stu-id="ec536-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="ec536-106">Je k dispozici možnost při zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="ec536-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="ec536-107">Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ec536-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="ec536-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="ec536-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="ec536-109">Na konci tohoto průvodce, ekvivalentem příkladu je zadána, který používá třídy z <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ec536-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="ec536-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ec536-110">To create the project</span></span>  
  
1. <span data-ttu-id="ec536-111">Na **souboru** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="ec536-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="ec536-112">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="ec536-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ec536-113">V **nainstalované šablony** podokně rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="ec536-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="ec536-114">V **šablony** podokně kliknout prostředním tlačítkem myši, **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="ec536-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="ec536-115">V **název** zadejte `FileExplorer` název projektu a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec536-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ec536-116">Visual Studio přidá projekt do **Průzkumníka řešení**, a otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ec536-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="ec536-117">Přidat ovládací prvky do formuláře v následující tabulce a nastavit odpovídající hodnoty pro jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="ec536-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="ec536-118">Control</span><span class="sxs-lookup"><span data-stu-id="ec536-118">Control</span></span>|<span data-ttu-id="ec536-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ec536-119">Property</span></span>|<span data-ttu-id="ec536-120">Value</span><span class="sxs-lookup"><span data-stu-id="ec536-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |**<span data-ttu-id="ec536-121">ListBox</span><span class="sxs-lookup"><span data-stu-id="ec536-121">ListBox</span></span>**|**<span data-ttu-id="ec536-122">Name</span><span class="sxs-lookup"><span data-stu-id="ec536-122">Name</span></span>**|`filesListBox`|  
    |**<span data-ttu-id="ec536-123">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="ec536-123">Button</span></span>**|**<span data-ttu-id="ec536-124">Name</span><span class="sxs-lookup"><span data-stu-id="ec536-124">Name</span></span>**<br /><br /> **<span data-ttu-id="ec536-125">Text</span><span class="sxs-lookup"><span data-stu-id="ec536-125">Text</span></span>**|`browseButton`<br /><br /> **<span data-ttu-id="ec536-126">Procházet</span><span class="sxs-lookup"><span data-stu-id="ec536-126">Browse</span></span>**|  
    |**<span data-ttu-id="ec536-127">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="ec536-127">Button</span></span>**|**<span data-ttu-id="ec536-128">Name</span><span class="sxs-lookup"><span data-stu-id="ec536-128">Name</span></span>**<br /><br /> **<span data-ttu-id="ec536-129">Text</span><span class="sxs-lookup"><span data-stu-id="ec536-129">Text</span></span>**|`examineButton`<br /><br /> **<span data-ttu-id="ec536-130">Prozkoumat</span><span class="sxs-lookup"><span data-stu-id="ec536-130">Examine</span></span>**|  
    |**<span data-ttu-id="ec536-131">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ec536-131">CheckBox</span></span>**|**<span data-ttu-id="ec536-132">Name</span><span class="sxs-lookup"><span data-stu-id="ec536-132">Name</span></span>**<br /><br /> **<span data-ttu-id="ec536-133">Text</span><span class="sxs-lookup"><span data-stu-id="ec536-133">Text</span></span>**|`saveCheckBox`<br /><br /> **<span data-ttu-id="ec536-134">Uložit výsledky</span><span class="sxs-lookup"><span data-stu-id="ec536-134">Save Results</span></span>**|  
    |**<span data-ttu-id="ec536-135">FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="ec536-135">FolderBrowserDialog</span></span>**|**<span data-ttu-id="ec536-136">Name</span><span class="sxs-lookup"><span data-stu-id="ec536-136">Name</span></span>**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="ec536-137">Vyberte složku, a seznam souborů ve složce</span><span class="sxs-lookup"><span data-stu-id="ec536-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="ec536-138">Vytvoření `Click` obslužné rutiny události pro `browseButton` dvojitým kliknutím na ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ec536-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="ec536-139">Otevře se Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="ec536-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="ec536-140">Přidejte následující kód, který `Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="ec536-141">`FolderBrowserDialog1.ShowDialog` Volání otevře **vyhledat složku** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ec536-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="ec536-142">Když uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnosti je předána jako argument pro `ListFiles` metoda, která se přidá v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="ec536-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="ec536-143">Přidejte následující `ListFiles` metody.</span><span class="sxs-lookup"><span data-stu-id="ec536-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="ec536-144">Tento kód nejprve vymaže **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="ec536-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="ec536-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pak načte kolekci řetězců, jeden pro každý soubor v adresáři.</span><span class="sxs-lookup"><span data-stu-id="ec536-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="ec536-146">`GetFiles` Metoda přijímá argument vzor hledání pro načtení souborů vyhovujících určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="ec536-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="ec536-147">V tomto příkladu jsou vráceny pouze soubory, které mají příponu .txt.</span><span class="sxs-lookup"><span data-stu-id="ec536-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="ec536-148">Řetězce, které jsou vrácené `GetFiles` metoda se poté přidají ke **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="ec536-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="ec536-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec536-149">Run the application.</span></span> <span data-ttu-id="ec536-150">Klikněte na tlačítko **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ec536-150">Click the **Browse** button.</span></span> <span data-ttu-id="ec536-151">V **vyhledat složku** dialogovém okně, přejděte do složky, která obsahuje soubory s příponou .txt, a potom vyberte složku a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec536-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="ec536-152">`ListBox` Obsahuje seznam souborů .txt ve vybrané složce.</span><span class="sxs-lookup"><span data-stu-id="ec536-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="ec536-153">Zastavení, spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec536-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="ec536-154">Získání atributů souboru a obsahu z textového souboru</span><span class="sxs-lookup"><span data-stu-id="ec536-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="ec536-155">Vytvoření `Click` obslužné rutiny události pro `examineButton` dvojitým kliknutím na ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ec536-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="ec536-156">Přidejte následující kód, který `Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="ec536-157">Kód zkontroluje, zda je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ec536-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="ec536-158">Potom získá položka z cesty k souboru `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ec536-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="ec536-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda se používá ke kontrole, jestli soubor stále existuje.</span><span class="sxs-lookup"><span data-stu-id="ec536-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="ec536-160">Cesta k souboru je předána jako argument pro `GetTextForOutput` metoda, která se přidá v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="ec536-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="ec536-161">Tato metoda vrátí řetězec, který obsahuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="ec536-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="ec536-162">Informace o souboru se zobrazí v **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="ec536-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="ec536-163">Přidejte následující `GetTextForOutput` metody.</span><span class="sxs-lookup"><span data-stu-id="ec536-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="ec536-164">Tento kód použije <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metoda získat soubor parametrů.</span><span class="sxs-lookup"><span data-stu-id="ec536-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="ec536-165">Soubor parametrů jsou přidány do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="ec536-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="ec536-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Přečte obsah souboru do metody <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="ec536-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="ec536-167">První řádek obsah se získávají z `StreamReader` a je přidán `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="ec536-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="ec536-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec536-168">Run the application.</span></span> <span data-ttu-id="ec536-169">Klikněte na tlačítko **Procházet**a přejděte do složky obsahující soubory s příponou .txt.</span><span class="sxs-lookup"><span data-stu-id="ec536-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="ec536-170">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec536-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="ec536-171">Vyberte soubor v `ListBox`a potom klikněte na tlačítko **vyhledejte**.</span><span class="sxs-lookup"><span data-stu-id="ec536-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="ec536-172">A `MessageBox` zobrazuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="ec536-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="ec536-173">Zastavení, spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec536-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="ec536-174">Chcete-li přidat položky protokolu</span><span class="sxs-lookup"><span data-stu-id="ec536-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="ec536-175">Přidejte následující kód do konce `examineButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="ec536-176">Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu ve stejném adresáři jako u vybraného souboru.</span><span class="sxs-lookup"><span data-stu-id="ec536-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="ec536-177">Text položky protokolu nastavena na aktuální datum a čas, za nímž následuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="ec536-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="ec536-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody s `append` argument nastaven na `True`, se používá k vytvoření položky protokolu.</span><span class="sxs-lookup"><span data-stu-id="ec536-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="ec536-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec536-179">Run the application.</span></span> <span data-ttu-id="ec536-180">Přejděte do textového souboru, vyberte ho v `ListBox`, vyberte **uložit výsledky** zaškrtněte políčko a potom klikněte na tlačítko **vyhledejte**.</span><span class="sxs-lookup"><span data-stu-id="ec536-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="ec536-181">Ověřte, že záznam protokolu se zapisují na `log.txt` souboru.</span><span class="sxs-lookup"><span data-stu-id="ec536-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="ec536-182">Zastavení, spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec536-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="ec536-183">Chcete-li používat aktuální adresář</span><span class="sxs-lookup"><span data-stu-id="ec536-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="ec536-184">Vytvořte obslužnou rutinu události pro `Form1_Load` poklepáním na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ec536-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="ec536-185">Přidejte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="ec536-186">Tento kód nastaví výchozí adresář prohlížeč složek do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ec536-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="ec536-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec536-187">Run the application.</span></span> <span data-ttu-id="ec536-188">Po kliknutí na **Procházet** poprvé, **vyhledat složku** dialogové okno k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="ec536-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="ec536-189">Zastavení, spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec536-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="ec536-190">Povolit některé ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="ec536-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="ec536-191">Přidejte následující `SetEnabled` metody.</span><span class="sxs-lookup"><span data-stu-id="ec536-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="ec536-192">`SetEnabled` Metoda povolí nebo zakáže ovládací prvky v závislosti na tom, zda je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ec536-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="ec536-193">Vytvoření `SelectedIndexChanged` obslužné rutiny události pro `filesListBox` dvojitým kliknutím `ListBox` ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ec536-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="ec536-194">Přidejte volání do `SetEnabled` na novém `filesListBox_SelectedIndexChanged` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="ec536-195">Přidejte volání do `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="ec536-196">Přidejte volání do `SetEnabled` na konci `Form1_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ec536-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="ec536-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec536-197">Run the application.</span></span> <span data-ttu-id="ec536-198">**Uložit výsledky** zaškrtávací políčko a **vyhledejte** tlačítka jsou zakázané, pokud položka není vybraný `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ec536-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="ec536-199">Úplný příklad použití My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="ec536-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="ec536-200">Následuje Úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="ec536-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="ec536-201">Úplný příklad using System.IO</span><span class="sxs-lookup"><span data-stu-id="ec536-201">Full example using System.IO</span></span>  
 <span data-ttu-id="ec536-202">Následující příklad ekvivalentní používá třídy z <xref:System.IO> obor názvů namísto použití `My.Computer.FileSystem` objekty.</span><span class="sxs-lookup"><span data-stu-id="ec536-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="ec536-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec536-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="ec536-204">Návod: Práce se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec536-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
