---
title: 'Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 0e1d085b0695150e40c88683721134e9ea5116d9
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260964"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="b201c-102">Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="b201c-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="b201c-103">Můžete použít <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> v ovládacím prvku <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b201c-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="b201c-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Vlastnost určuje, zda <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvek automaticky vyplní dostupné místo na <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b201c-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b201c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b201c-105">Example</span></span>  
 <span data-ttu-id="b201c-106">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> v ovládacím prvku <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b201c-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="b201c-107"><xref:System.Windows.Forms.ToolStripItem.Click> Obslužná rutina události provádí výhradně- nebo operace (XOR) Chcete-li přepnout hodnotu <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b201c-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="b201c-108">Použít tento příklad kódu, kompilaci a spuštění aplikace a pak klikněte na **doprostřed (Spring)** na <xref:System.Windows.Forms.StatusStrip> ovládacího prvku na hodnotu přepínače <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b201c-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b201c-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b201c-109">Compiling the Code</span></span>  
 <span data-ttu-id="b201c-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b201c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="b201c-111">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b201c-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b201c-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b201c-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b201c-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="b201c-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b201c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b201c-114">See also</span></span>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="b201c-115">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b201c-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
