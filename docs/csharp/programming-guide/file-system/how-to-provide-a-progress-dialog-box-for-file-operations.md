---
title: "Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac68b5aa6014db87b4f7a269ef73d0608371bd8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="fb962-102">Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fb962-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="fb962-103">Můžete zadat standardní dialogové okno se zobrazí průběh na operací se soubory v systému Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metoda v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fb962-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="fb962-104">Chcete-li přidat odkaz v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fb962-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="fb962-105">Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="fb962-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="fb962-106">**Správce odkazů** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fb962-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="fb962-107">V **sestavení** oblasti, zvolte**Framework** Pokud již není vybraná.</span><span class="sxs-lookup"><span data-stu-id="fb962-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="fb962-108">V seznamu názvů, vyberte **Microsoft.VisualBasic –** zaškrtněte políčko a potom vyberte **OK** tlačítko dialogové okno zavřete.</span><span class="sxs-lookup"><span data-stu-id="fb962-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb962-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb962-109">Example</span></span>  
 <span data-ttu-id="fb962-110">Následující kód zkopíruje adresáři, `sourcePath` určuje do adresáře, `destinationPath` určuje.</span><span class="sxs-lookup"><span data-stu-id="fb962-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="fb962-111">Tento kód také poskytuje standardní dialogové okno se zobrazí odhadované částky zbývající čas předtím, než se dokončí operaci.</span><span class="sxs-lookup"><span data-stu-id="fb962-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fb962-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb962-112">See Also</span></span>  
 [<span data-ttu-id="fb962-113">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="fb962-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
