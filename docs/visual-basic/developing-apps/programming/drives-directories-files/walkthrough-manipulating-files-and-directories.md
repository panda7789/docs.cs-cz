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
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="8ad20-102">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ad20-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="8ad20-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ad20-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="8ad20-104">It describes how to create a small application that lists and examines text files in a directory.</span><span class="sxs-lookup"><span data-stu-id="8ad20-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="8ad20-105">For each selected text file, the application provides file attributes and the first line of content.</span><span class="sxs-lookup"><span data-stu-id="8ad20-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="8ad20-106">There is an option to write information to a log file.</span><span class="sxs-lookup"><span data-stu-id="8ad20-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="8ad20-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ad20-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="8ad20-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="8ad20-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="8ad20-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span><span class="sxs-lookup"><span data-stu-id="8ad20-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="8ad20-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="8ad20-110">To create the project</span></span>  
  
1. <span data-ttu-id="8ad20-111">On the **File** menu, click **New Project**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="8ad20-112">The **New Project** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="8ad20-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="8ad20-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="8ad20-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="8ad20-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8ad20-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span><span class="sxs-lookup"><span data-stu-id="8ad20-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="8ad20-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span><span class="sxs-lookup"><span data-stu-id="8ad20-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="8ad20-118">Control</span><span class="sxs-lookup"><span data-stu-id="8ad20-118">Control</span></span>|<span data-ttu-id="8ad20-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8ad20-119">Property</span></span>|<span data-ttu-id="8ad20-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8ad20-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="8ad20-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="8ad20-121">**ListBox**</span></span>|<span data-ttu-id="8ad20-122">**Name**</span><span class="sxs-lookup"><span data-stu-id="8ad20-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="8ad20-123">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="8ad20-123">**Button**</span></span>|<span data-ttu-id="8ad20-124">**Name**</span><span class="sxs-lookup"><span data-stu-id="8ad20-124">**Name**</span></span><br /><br /> <span data-ttu-id="8ad20-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="8ad20-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="8ad20-126">**Browse**</span><span class="sxs-lookup"><span data-stu-id="8ad20-126">**Browse**</span></span>|  
    |<span data-ttu-id="8ad20-127">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="8ad20-127">**Button**</span></span>|<span data-ttu-id="8ad20-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="8ad20-128">**Name**</span></span><br /><br /> <span data-ttu-id="8ad20-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="8ad20-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="8ad20-130">**Examine**</span><span class="sxs-lookup"><span data-stu-id="8ad20-130">**Examine**</span></span>|  
    |<span data-ttu-id="8ad20-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="8ad20-131">**CheckBox**</span></span>|<span data-ttu-id="8ad20-132">**Name**</span><span class="sxs-lookup"><span data-stu-id="8ad20-132">**Name**</span></span><br /><br /> <span data-ttu-id="8ad20-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="8ad20-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="8ad20-134">**Save Results**</span><span class="sxs-lookup"><span data-stu-id="8ad20-134">**Save Results**</span></span>|  
    |<span data-ttu-id="8ad20-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="8ad20-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="8ad20-136">**Name**</span><span class="sxs-lookup"><span data-stu-id="8ad20-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="8ad20-137">To select a folder, and list files in a folder</span><span class="sxs-lookup"><span data-stu-id="8ad20-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="8ad20-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span><span class="sxs-lookup"><span data-stu-id="8ad20-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="8ad20-139">The Code Editor opens.</span><span class="sxs-lookup"><span data-stu-id="8ad20-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="8ad20-140">Add the following code to the `Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="8ad20-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span><span class="sxs-lookup"><span data-stu-id="8ad20-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="8ad20-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span><span class="sxs-lookup"><span data-stu-id="8ad20-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="8ad20-143">Add the following `ListFiles` method.</span><span class="sxs-lookup"><span data-stu-id="8ad20-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="8ad20-144">This code first clears the **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="8ad20-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span><span class="sxs-lookup"><span data-stu-id="8ad20-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="8ad20-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span><span class="sxs-lookup"><span data-stu-id="8ad20-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="8ad20-147">In this example, only files that have the extension .txt are returned.</span><span class="sxs-lookup"><span data-stu-id="8ad20-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="8ad20-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="8ad20-149">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ad20-149">Run the application.</span></span> <span data-ttu-id="8ad20-150">Click the **Browse** button.</span><span class="sxs-lookup"><span data-stu-id="8ad20-150">Click the **Browse** button.</span></span> <span data-ttu-id="8ad20-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="8ad20-152">The `ListBox` contains a list of .txt files in the selected folder.</span><span class="sxs-lookup"><span data-stu-id="8ad20-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="8ad20-153">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="8ad20-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="8ad20-154">To obtain attributes of a file, and content from a text file</span><span class="sxs-lookup"><span data-stu-id="8ad20-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="8ad20-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span><span class="sxs-lookup"><span data-stu-id="8ad20-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="8ad20-156">Add the following code to the `Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="8ad20-157">The code verifies that an item is selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="8ad20-158">It then obtains the file path entry from the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="8ad20-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span><span class="sxs-lookup"><span data-stu-id="8ad20-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="8ad20-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span><span class="sxs-lookup"><span data-stu-id="8ad20-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="8ad20-161">This method returns a string that contains file information.</span><span class="sxs-lookup"><span data-stu-id="8ad20-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="8ad20-162">The file information appears in a **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="8ad20-163">Add the following `GetTextForOutput` method.</span><span class="sxs-lookup"><span data-stu-id="8ad20-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="8ad20-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span><span class="sxs-lookup"><span data-stu-id="8ad20-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="8ad20-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8ad20-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="8ad20-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="8ad20-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="8ad20-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="8ad20-168">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ad20-168">Run the application.</span></span> <span data-ttu-id="8ad20-169">Click **Browse**, and browse to a folder that contains .txt files.</span><span class="sxs-lookup"><span data-stu-id="8ad20-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="8ad20-170">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ad20-171">Select a file in the `ListBox`, and then click **Examine**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="8ad20-172">A `MessageBox` shows the file information.</span><span class="sxs-lookup"><span data-stu-id="8ad20-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="8ad20-173">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="8ad20-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="8ad20-174">To add a log entry</span><span class="sxs-lookup"><span data-stu-id="8ad20-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="8ad20-175">Add the following code to the end of the `examineButton_Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="8ad20-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span><span class="sxs-lookup"><span data-stu-id="8ad20-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="8ad20-177">The text of the log entry is set to the current date and time followed by the file information.</span><span class="sxs-lookup"><span data-stu-id="8ad20-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="8ad20-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span><span class="sxs-lookup"><span data-stu-id="8ad20-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="8ad20-179">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ad20-179">Run the application.</span></span> <span data-ttu-id="8ad20-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span><span class="sxs-lookup"><span data-stu-id="8ad20-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="8ad20-181">Verify that the log entry is written to the `log.txt` file.</span><span class="sxs-lookup"><span data-stu-id="8ad20-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="8ad20-182">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="8ad20-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="8ad20-183">To use the current directory</span><span class="sxs-lookup"><span data-stu-id="8ad20-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="8ad20-184">Create an event handler for `Form1_Load` by double-clicking the form.</span><span class="sxs-lookup"><span data-stu-id="8ad20-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="8ad20-185">Add the following code to the event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="8ad20-186">This code sets the default directory of the folder browser to the current directory.</span><span class="sxs-lookup"><span data-stu-id="8ad20-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="8ad20-187">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ad20-187">Run the application.</span></span> <span data-ttu-id="8ad20-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span><span class="sxs-lookup"><span data-stu-id="8ad20-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="8ad20-189">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="8ad20-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="8ad20-190">To selectively enable controls</span><span class="sxs-lookup"><span data-stu-id="8ad20-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="8ad20-191">Add the following `SetEnabled` method.</span><span class="sxs-lookup"><span data-stu-id="8ad20-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="8ad20-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="8ad20-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span><span class="sxs-lookup"><span data-stu-id="8ad20-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="8ad20-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="8ad20-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="8ad20-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span><span class="sxs-lookup"><span data-stu-id="8ad20-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="8ad20-197">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ad20-197">Run the application.</span></span> <span data-ttu-id="8ad20-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="8ad20-199">Full example using My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="8ad20-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="8ad20-200">Following is the complete example.</span><span class="sxs-lookup"><span data-stu-id="8ad20-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="8ad20-201">Full example using System.IO</span><span class="sxs-lookup"><span data-stu-id="8ad20-201">Full example using System.IO</span></span>  

 <span data-ttu-id="8ad20-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span><span class="sxs-lookup"><span data-stu-id="8ad20-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad20-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ad20-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="8ad20-204">Návod: Práce se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8ad20-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
