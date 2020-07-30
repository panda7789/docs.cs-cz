---
title: Postup poskytnutí dialogového okna průběhu pro Souborová operace – Průvodce programováním v C#
description: Naučte se, jak poskytnout dialogové okno průběhu pro operace se soubory pomocí metody CopyFile (String, String, UIOption).
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 2ea18d924b47fc10412d37479f1b09f7eef7ad3b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301967"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="31b69-103">Postup poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="31b69-103">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="31b69-104">Můžete zadat standardní dialogové okno, které zobrazí průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="31b69-104">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="31b69-105">Přidání odkazu v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31b69-105">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="31b69-106">V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="31b69-106">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="31b69-107">Zobrazí se dialogové okno **Správce odkazů** .</span><span class="sxs-lookup"><span data-stu-id="31b69-107">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="31b69-108">V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.</span><span class="sxs-lookup"><span data-stu-id="31b69-108">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="31b69-109">V seznamu názvů zaškrtněte políčko **Microsoft. VisualBasic** a kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="31b69-109">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31b69-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="31b69-110">Example</span></span>  
 <span data-ttu-id="31b69-111">Následující kód zkopíruje adresář, který `sourcePath` Určuje do adresáře, který `destinationPath` Určuje.</span><span class="sxs-lookup"><span data-stu-id="31b69-111">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="31b69-112">Tento kód také obsahuje standardní dialogové okno, ve kterém se zobrazuje odhadované množství času zbývajícího před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="31b69-112">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="31b69-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31b69-113">See also</span></span>

- [<span data-ttu-id="31b69-114">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="31b69-114">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
