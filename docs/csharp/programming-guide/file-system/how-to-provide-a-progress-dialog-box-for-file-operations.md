---
title: Postup poskytnutí dialogového okna průběhu pro Souborová operace – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705129"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="15d0e-102">Postup poskytnutí dialogového okna průběhu pro operace se soubory (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="15d0e-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="15d0e-103">Můžete zadat standardní dialogové okno, které zobrazí průběh operací se soubory ve Windows, pokud použijete metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> v oboru názvů <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15d0e-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="15d0e-104">Přidání odkazu v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15d0e-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="15d0e-105">V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="15d0e-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="15d0e-106">Zobrazí se dialogové okno **Správce odkazů** .</span><span class="sxs-lookup"><span data-stu-id="15d0e-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="15d0e-107">V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.</span><span class="sxs-lookup"><span data-stu-id="15d0e-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="15d0e-108">V seznamu názvů zaškrtněte políčko **Microsoft. VisualBasic** a kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="15d0e-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d0e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="15d0e-109">Example</span></span>  
 <span data-ttu-id="15d0e-110">Následující kód zkopíruje adresář, který `sourcePath` určuje do adresáře, který `destinationPath` určuje.</span><span class="sxs-lookup"><span data-stu-id="15d0e-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="15d0e-111">Tento kód také obsahuje standardní dialogové okno, ve kterém se zobrazuje odhadované množství času zbývajícího před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="15d0e-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="15d0e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d0e-112">See also</span></span>

- [<span data-ttu-id="15d0e-113">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="15d0e-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
