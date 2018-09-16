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
ms.openlocfilehash: 34d600454a7fa63c7ba59bebded6365cd5401cb4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685878"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="46259-102">Postupy: Definování hloubkového uspořádání ukotvených ovládacích prvků ToolStrip</span><span class="sxs-lookup"><span data-stu-id="46259-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="46259-103">Na pozici <xref:System.Windows.Forms.ToolStrip> ovládacího prvku správně s ukotvení, je třeba umístit ovládací prvek správně v pořadí vykreslování formuláře.</span><span class="sxs-lookup"><span data-stu-id="46259-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46259-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="46259-104">Example</span></span>  
 <span data-ttu-id="46259-105">Následující příklad kódu ukazuje, jak uspořádat <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a ukotvených <xref:System.Windows.Forms.MenuStrip> ovládacího prvku tak, že zadáte pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="46259-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="46259-106">Pořadí je určen podle pořadí, ve kterém <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="46259-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="46259-107">ovládací prvky jsou přidány do formuláře <xref:System.Windows.Forms.Control.Controls%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="46259-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="46259-108">Pořadí těchto volání <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody a zobrazení vliv na rozložení.</span><span class="sxs-lookup"><span data-stu-id="46259-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46259-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="46259-109">Compiling the Code</span></span>  
 <span data-ttu-id="46259-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="46259-110">This example requires:</span></span>  
  
-   <span data-ttu-id="46259-111">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="46259-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="46259-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="46259-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="46259-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="46259-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="46259-114">Také se [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="46259-114">Also se [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46259-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="46259-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>  
 <xref:System.Windows.Forms.Control.Controls%2A>  
 <xref:System.Windows.Forms.Control.Dock%2A>  
 [<span data-ttu-id="46259-116">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="46259-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
