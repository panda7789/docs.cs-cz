---
title: Dialogové okno Průběh pro operace se soubory – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705129"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="ec121-102">Jak poskytnout dialogové okno průběhu pro operace se soubory (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ec121-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="ec121-103">Pokud použijete metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> v oboru názvů, můžete zadat standardní dialogové <xref:Microsoft.VisualBasic?displayProperty=nameWithType> okno, které zobrazuje průběh operací se soubory v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ec121-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="ec121-104">Přidání odkazu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec121-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="ec121-105">Na řádku nabídek zvolte **Project**, **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="ec121-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="ec121-106">Zobrazí se dialogové okno **Správce odkazů.**</span><span class="sxs-lookup"><span data-stu-id="ec121-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ec121-107">V oblasti **Sestavení** zvolte **Framework,** pokud ještě není vybrána.</span><span class="sxs-lookup"><span data-stu-id="ec121-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="ec121-108">V seznamu názvů zaškrtněte políčko **Microsoft.VisualBasic** a potom zvolte tlačítko **OK** a zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ec121-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec121-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec121-109">Example</span></span>  
 <span data-ttu-id="ec121-110">Následující kód zkopíruje `sourcePath` adresář, který určuje `destinationPath` do adresáře, který určuje.</span><span class="sxs-lookup"><span data-stu-id="ec121-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="ec121-111">Tento kód také poskytuje standardní dialogové okno, které zobrazuje odhadované množství času zbývajícího před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="ec121-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ec121-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec121-112">See also</span></span>

- [<span data-ttu-id="ec121-113">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ec121-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
