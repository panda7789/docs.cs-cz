---
title: 'Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 13f924566df0d7fe601e32bfe74878c18d8e64b8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245386"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="d3302-102">Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="d3302-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="d3302-103">Můžete zadat standardní dialogové okno, který znázorňuje průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d3302-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="d3302-104">Chcete-li přidat odkaz v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3302-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="d3302-105">V panelu nabídky zvolte **projektu**, **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="d3302-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="d3302-106">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d3302-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="d3302-107">V **sestavení** oblasti, zvolte **Framework** Pokud není již vybrána.</span><span class="sxs-lookup"><span data-stu-id="d3302-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="d3302-108">Vyberte v seznamu názvů **Microsoft.VisualBasic** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítka zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d3302-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3302-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3302-109">Example</span></span>  
 <span data-ttu-id="d3302-110">Následující kód zkopíruje adresář, který `sourcePath` určuje do adresáře, který `destinationPath` určuje.</span><span class="sxs-lookup"><span data-stu-id="d3302-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="d3302-111">Tento kód také poskytuje standardní dialogové okno zobrazující odhadovanou výši zbývajícího času před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="d3302-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d3302-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3302-112">See Also</span></span>

- [<span data-ttu-id="d3302-113">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d3302-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
