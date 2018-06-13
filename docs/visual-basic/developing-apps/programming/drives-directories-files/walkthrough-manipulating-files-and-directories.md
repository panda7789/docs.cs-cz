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
ms.openlocfilehash: ab1c119d2c5cd9bfa0ff725774144bc65817cad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592506"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="c9367-102">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9367-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="c9367-103">Tento názorný postup obsahuje úvod do základní informace o souboru vstupně-výstupních operací v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c9367-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="c9367-104">Popisuje postup vytvoření malé aplikace, která obsahuje seznam a prověří textové soubory v adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9367-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="c9367-105">Pro každý soubor vybraný text aplikace poskytuje atributy souboru a prvního řádku obsahu.</span><span class="sxs-lookup"><span data-stu-id="c9367-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="c9367-106">Je k dispozici možnost při zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c9367-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="c9367-107">Tento návod používá členy `My.Computer.FileSystem Object`, které jsou dostupné v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c9367-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="c9367-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="c9367-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="c9367-109">Na konci tohoto průvodce, je ekvivalentní například zadaný používající třídy z <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c9367-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="c9367-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c9367-110">To create the project</span></span>  
  
1.  <span data-ttu-id="c9367-111">Na **soubor** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="c9367-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="c9367-112">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c9367-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="c9367-113">V **nainstalovaných šablonách** podokně rozbalte **jazyka Visual Basic**a potom klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9367-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="c9367-114">V **šablony** podokně v prostředním, klikněte na **formulářové aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9367-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="c9367-115">V **název** zadejte `FileExplorer` nastavit název projektu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9367-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c9367-116">Visual Studio. přidá projekt **Průzkumníku**, a otevře v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="c9367-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="c9367-117">Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c9367-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="c9367-118">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c9367-118">Control</span></span>|<span data-ttu-id="c9367-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c9367-119">Property</span></span>|<span data-ttu-id="c9367-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c9367-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="c9367-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="c9367-121">**ListBox**</span></span>|<span data-ttu-id="c9367-122">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c9367-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="c9367-123">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="c9367-123">**Button**</span></span>|<span data-ttu-id="c9367-124">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c9367-124">**Name**</span></span><br /><br /> <span data-ttu-id="c9367-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="c9367-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="c9367-126">**Procházet**</span><span class="sxs-lookup"><span data-stu-id="c9367-126">**Browse**</span></span>|  
    |<span data-ttu-id="c9367-127">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="c9367-127">**Button**</span></span>|<span data-ttu-id="c9367-128">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c9367-128">**Name**</span></span><br /><br /> <span data-ttu-id="c9367-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="c9367-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="c9367-130">**Zkontrolujte**</span><span class="sxs-lookup"><span data-stu-id="c9367-130">**Examine**</span></span>|  
    |<span data-ttu-id="c9367-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="c9367-131">**CheckBox**</span></span>|<span data-ttu-id="c9367-132">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c9367-132">**Name**</span></span><br /><br /> <span data-ttu-id="c9367-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="c9367-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="c9367-134">**Uložení výsledků**</span><span class="sxs-lookup"><span data-stu-id="c9367-134">**Save Results**</span></span>|  
    |<span data-ttu-id="c9367-135">**FolderBrowserDialog –**</span><span class="sxs-lookup"><span data-stu-id="c9367-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="c9367-136">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c9367-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="c9367-137">Vyberte složku, a seznam souborů ve složce</span><span class="sxs-lookup"><span data-stu-id="c9367-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="c9367-138">Vytvoření `Click` obslužné rutiny události pro `browseButton` poklepáním na ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c9367-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="c9367-139">Otevře se Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="c9367-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="c9367-140">Přidejte následující kód, který `Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     <span data-ttu-id="c9367-141">`FolderBrowserDialog1.ShowDialog` Volání otevře **vyhledat složku** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c9367-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="c9367-142">Poté, co uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost je odeslán jako argument k `ListFiles` metoda, která se přidá v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="c9367-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="c9367-143">Přidejte následující `ListFiles` metoda.</span><span class="sxs-lookup"><span data-stu-id="c9367-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     <span data-ttu-id="c9367-144">Tento kód nejdřív vymaže **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="c9367-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="c9367-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pak načte kolekci řetězce, jednu pro každý soubor v adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9367-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="c9367-146">`GetFiles` Metoda přijímá argumentem vzor hledání se budou načítat soubory, které odpovídají konkrétním vzorku.</span><span class="sxs-lookup"><span data-stu-id="c9367-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="c9367-147">V tomto příkladu jsou vráceny jen soubory s příponou .txt.</span><span class="sxs-lookup"><span data-stu-id="c9367-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="c9367-148">Řetězce, které se vrátí pomocí `GetFiles` metoda se pak přidají do **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="c9367-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="c9367-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9367-149">Run the application.</span></span> <span data-ttu-id="c9367-150">Klikněte **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c9367-150">Click the **Browse** button.</span></span> <span data-ttu-id="c9367-151">V **vyhledat složku** dialogové okno, přejděte do složky, která obsahuje soubory s příponou .txt, a potom vyberte složku a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9367-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="c9367-152">`ListBox` Obsahuje seznam soubory s příponou .txt ve vybrané složce.</span><span class="sxs-lookup"><span data-stu-id="c9367-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="c9367-153">Zastavte spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9367-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="c9367-154">Získání atributů souboru a obsahu z textového souboru</span><span class="sxs-lookup"><span data-stu-id="c9367-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="c9367-155">Vytvoření `Click` obslužné rutiny události pro `examineButton` poklepáním na ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c9367-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="c9367-156">Přidejte následující kód, který `Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     <span data-ttu-id="c9367-157">Kód ověřuje, že je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c9367-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="c9367-158">Poté získá položka z cesty k souboru `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c9367-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="c9367-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda se používá k ověření, zda soubor stále existuje.</span><span class="sxs-lookup"><span data-stu-id="c9367-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="c9367-160">Cesta k souboru je odeslán jako argument k `GetTextForOutput` metoda, která se přidá v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="c9367-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="c9367-161">Tato metoda vrátí řetězec, který obsahuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="c9367-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="c9367-162">Informace o souboru se zobrazí v **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="c9367-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="c9367-163">Přidejte následující `GetTextForOutput` metoda.</span><span class="sxs-lookup"><span data-stu-id="c9367-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     <span data-ttu-id="c9367-164">Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metoda získat soubor parametrů.</span><span class="sxs-lookup"><span data-stu-id="c9367-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="c9367-165">Soubor parametrů jsou přidány do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c9367-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="c9367-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda přečte obsah souboru do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="c9367-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="c9367-167">První řádek obsahu se získávají z `StreamReader` a přidají se do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="c9367-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="c9367-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9367-168">Run the application.</span></span> <span data-ttu-id="c9367-169">Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory s příponou .txt.</span><span class="sxs-lookup"><span data-stu-id="c9367-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="c9367-170">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9367-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="c9367-171">Vyberte soubor v `ListBox`a potom klikněte na **vyhledejte**.</span><span class="sxs-lookup"><span data-stu-id="c9367-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="c9367-172">A `MessageBox` zobrazuje informace o souboru.</span><span class="sxs-lookup"><span data-stu-id="c9367-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="c9367-173">Zastavte spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9367-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="c9367-174">Chcete-li přidat položky protokolu</span><span class="sxs-lookup"><span data-stu-id="c9367-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="c9367-175">Přidejte následující kód do konce `examineButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     <span data-ttu-id="c9367-176">Kód nastaví cesta k souboru protokolu pro umístění souboru protokolu ve stejném adresáři jako u vybraného souboru.</span><span class="sxs-lookup"><span data-stu-id="c9367-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="c9367-177">Text položky protokolu nastavena na aktuální datum a čas, za nímž následuje informací o souboru.</span><span class="sxs-lookup"><span data-stu-id="c9367-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="c9367-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody s `append` argument nastaven na hodnotu `True`, se používá k vytvoření položky protokolu.</span><span class="sxs-lookup"><span data-stu-id="c9367-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="c9367-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9367-179">Run the application.</span></span> <span data-ttu-id="c9367-180">Přejděte do textového souboru, vyberte ho v `ListBox`, vyberte **uložit výsledky** zaškrtněte políčko a potom klikněte na **vyhledejte**.</span><span class="sxs-lookup"><span data-stu-id="c9367-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="c9367-181">Ověřte, že je na zapisovat položky protokolu `log.txt` souboru.</span><span class="sxs-lookup"><span data-stu-id="c9367-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="c9367-182">Zastavte spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9367-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="c9367-183">Chcete-li používat aktuální adresář</span><span class="sxs-lookup"><span data-stu-id="c9367-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="c9367-184">Vytvoření obslužné rutiny události pro `Form1_Load` poklepáním na formulář.</span><span class="sxs-lookup"><span data-stu-id="c9367-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="c9367-185">Přidejte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     <span data-ttu-id="c9367-186">Tento kód nastaví výchozí adresář prohlížeče složky k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9367-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="c9367-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9367-187">Run the application.</span></span> <span data-ttu-id="c9367-188">Když kliknete na tlačítko **Procházet** první **vyhledat složku** otevře se dialogové okno k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9367-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="c9367-189">Zastavte spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9367-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="c9367-190">Povolit některé ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c9367-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="c9367-191">Přidejte následující `SetEnabled` metoda.</span><span class="sxs-lookup"><span data-stu-id="c9367-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     <span data-ttu-id="c9367-192">`SetEnabled` Metoda povolí nebo zakáže ovládací prvky v závislosti na tom, jestli je položka vybrána v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c9367-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="c9367-193">Vytvoření `SelectedIndexChanged` obslužné rutiny události pro `filesListBox` dvojitým kliknutím `ListBox` ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c9367-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="c9367-194">Přidejte volání `SetEnabled` v novém `filesListBox_SelectedIndexChanged` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="c9367-195">Přidejte volání `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="c9367-196">Přidejte volání `SetEnabled` na konci `Form1_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c9367-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="c9367-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9367-197">Run the application.</span></span> <span data-ttu-id="c9367-198">**Uložit výsledky** zaškrtávací políčko a **vyhledejte** tlačítko jsou zakázané, pokud není vybrána položka v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="c9367-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="c9367-199">Úplný příklad pomocí My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c9367-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="c9367-200">Toto je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="c9367-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="c9367-201">Úplný příklad pomocí System.IO</span><span class="sxs-lookup"><span data-stu-id="c9367-201">Full example using System.IO</span></span>  
 <span data-ttu-id="c9367-202">Následující příklad ekvivalentní používá třídy z <xref:System.IO> obor názvů místo použití `My.Computer.FileSystem` objekty.</span><span class="sxs-lookup"><span data-stu-id="c9367-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c9367-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9367-203">See Also</span></span>  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [<span data-ttu-id="c9367-204">Návod: Práce se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c9367-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
