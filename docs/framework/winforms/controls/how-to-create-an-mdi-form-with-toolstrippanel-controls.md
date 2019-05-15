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
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a>Postupy: Vytvoření formuláře MDI s ovládacími prvky ToolStripPanel
Můžete vytvořit více formuláře (MDI interface) dokumentu, který má <xref:System.Windows.Forms.ToolStrip> rámců na všechny čtyři strany ovládací prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat ukotvených <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků pro rámec okna MDI pomocí čtyř <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.  
  
 V tomto příkladu <xref:System.Windows.Forms.ToolStripPanel.Join%2A> metoda bude k obrazci <xref:System.Windows.Forms.ToolStrip> ovládacích prvků do odpovídajícího <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
