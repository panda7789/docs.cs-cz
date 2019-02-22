---
title: 'Postupy: Definování hloubkového uspořádání ukotvených ovládacích prvků ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: cf2bd09f5eb29bc659e97cf7e390ceb78bf2bbd8
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583339"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="e7138-102">Postupy: Definování hloubkového uspořádání ukotvených ovládacích prvků ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7138-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="e7138-103">Na pozici <xref:System.Windows.Forms.ToolStrip> ovládacího prvku správně s ukotvení, je třeba umístit ovládací prvek správně v pořadí vykreslování formuláře.</span><span class="sxs-lookup"><span data-stu-id="e7138-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7138-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7138-104">Example</span></span>  
 <span data-ttu-id="e7138-105">Následující příklad kódu ukazuje, jak uspořádat <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a ukotvených <xref:System.Windows.Forms.MenuStrip> ovládacího prvku tak, že zadáte pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="e7138-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="e7138-106">Pořadí je určen podle pořadí, ve kterém <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="e7138-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="e7138-107">ovládací prvky jsou přidány do formuláře <xref:System.Windows.Forms.Control.Controls%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="e7138-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="e7138-108">Pořadí těchto volání <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody a zobrazení vliv na rozložení.</span><span class="sxs-lookup"><span data-stu-id="e7138-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7138-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e7138-109">Compiling the Code</span></span>  
 <span data-ttu-id="e7138-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e7138-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e7138-111">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e7138-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e7138-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e7138-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e7138-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="e7138-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7138-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7138-114">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="e7138-115">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7138-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
