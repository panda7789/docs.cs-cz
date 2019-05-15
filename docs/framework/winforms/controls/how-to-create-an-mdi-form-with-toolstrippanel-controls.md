---
title: 'Postupy: Vytvoření formuláře MDI s ovládacími prvky ToolStripPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 4dae528d69c6c08c2005fd30d7d16fafa67afb53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590563"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="89f8d-102">Postupy: Vytvoření formuláře MDI s ovládacími prvky ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="89f8d-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="89f8d-103">Můžete vytvořit více formuláře (MDI interface) dokumentu, který má <xref:System.Windows.Forms.ToolStrip> rámců na všechny čtyři strany ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="89f8d-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f8d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="89f8d-104">Example</span></span>  
 <span data-ttu-id="89f8d-105">Následující příklad kódu ukazuje, jak používat ukotvených <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků pro rámec okna MDI pomocí čtyř <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="89f8d-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="89f8d-106">V tomto příkladu <xref:System.Windows.Forms.ToolStripPanel.Join%2A> metoda bude k obrazci <xref:System.Windows.Forms.ToolStrip> ovládacích prvků do odpovídajícího <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="89f8d-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89f8d-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89f8d-107">Compiling the Code</span></span>  
 <span data-ttu-id="89f8d-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="89f8d-108">This example requires:</span></span>  
  
- <span data-ttu-id="89f8d-109">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="89f8d-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f8d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89f8d-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="89f8d-111">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="89f8d-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
