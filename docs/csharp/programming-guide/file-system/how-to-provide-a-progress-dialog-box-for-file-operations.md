---
title: 'Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: ab268c30af6b5eefe84ade852c679535c1e48068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597265"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="467b1-102">Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="467b1-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="467b1-103">Můžete zadat standardní dialogové okno, který znázorňuje průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="467b1-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="467b1-104">Chcete-li přidat odkaz v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="467b1-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="467b1-105">V panelu nabídky zvolte **projektu**, **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="467b1-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="467b1-106">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="467b1-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="467b1-107">V **sestavení** oblasti, zvolte **Framework** Pokud není již vybrána.</span><span class="sxs-lookup"><span data-stu-id="467b1-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="467b1-108">Vyberte v seznamu názvů **Microsoft.VisualBasic** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítka zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="467b1-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="467b1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="467b1-109">Example</span></span>  
 <span data-ttu-id="467b1-110">Následující kód zkopíruje adresář, který `sourcePath` určuje do adresáře, který `destinationPath` určuje.</span><span class="sxs-lookup"><span data-stu-id="467b1-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="467b1-111">Tento kód také poskytuje standardní dialogové okno zobrazující odhadovanou výši zbývajícího času před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="467b1-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="467b1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="467b1-112">See also</span></span>

- [<span data-ttu-id="467b1-113">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="467b1-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
