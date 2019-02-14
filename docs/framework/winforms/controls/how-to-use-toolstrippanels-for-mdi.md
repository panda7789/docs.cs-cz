---
title: 'Postupy: Použití prvku ToolStripPanels pro MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], using ToolStripPanels [Windows Forms]
- ToolStripPanel control [Windows Forms], using for MDI
- toolbars [Windows Forms], using for MDI
ms.assetid: d6b884fc-0846-465f-83c3-5dc0fe93b00f
ms.openlocfilehash: dd9421bd0ca284f9adc837a6a7e4643f38e80d31
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260852"
---
# <a name="how-to-use-toolstrippanels-for-mdi"></a>Postupy: Použití prvku ToolStripPanels pro MDI
<xref:System.Windows.Forms.ToolStripPanel> Poskytuje flexibilitu pro aplikace rozhraní více dokumentů (MDI) s použitím <xref:System.Windows.Forms.ToolStripPanel.Join%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky pro MDI.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolStripPanel>
- [Postupy: Připojte se k prvku ToolStripPanels](../../../../docs/framework/winforms/controls/how-to-join-toolstrippanels.md)
