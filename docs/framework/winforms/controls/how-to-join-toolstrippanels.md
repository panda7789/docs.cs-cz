---
title: 'Postupy: Spojení ToolStripPanels'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: 5e1688fb00e6eefa4873284e1ea1ba29536d3227
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723623"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="59aad-102">Postupy: Spojení ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="59aad-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="59aad-103">Toho se můžete zapojit <xref:System.Windows.Forms.ToolStrip> ovládacích prvků do <xref:System.Windows.Forms.ToolStripPanel> za běhu, který poskytuje flexibilitu aplikací rozhraní více dokumentů (MDI).</span><span class="sxs-lookup"><span data-stu-id="59aad-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59aad-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="59aad-104">Example</span></span>  
 <span data-ttu-id="59aad-105">Následující příklad kódu ukazuje, jak propojit <xref:System.Windows.Forms.ToolStrip> ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="59aad-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59aad-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="59aad-106">Compiling the Code</span></span>  
 <span data-ttu-id="59aad-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="59aad-107">This example requires:</span></span>  
  
-   <span data-ttu-id="59aad-108">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="59aad-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="59aad-109">Informace o vytváření použijeme příklad z příkazového řádku pro visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="59aad-109">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="59aad-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="59aad-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="59aad-111">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="59aad-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59aad-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="59aad-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="59aad-113">Postupy: Použití prvku ToolStripPanels pro MDI</span><span class="sxs-lookup"><span data-stu-id="59aad-113">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
