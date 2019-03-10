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
ms.openlocfilehash: 13a9809507f30f70d751d24ec68de1e5a62011cd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714837"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip
Můžete použít <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> v ovládacím prvku <xref:System.Windows.Forms.StatusStrip> ovládacího prvku. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Vlastnost určuje, zda <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvek automaticky vyplní dostupné místo na <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost na pozici <xref:System.Windows.Forms.ToolStripStatusLabel> v ovládacím prvku <xref:System.Windows.Forms.StatusStrip> ovládacího prvku. <xref:System.Windows.Forms.ToolStripItem.Click> Obslužná rutina události provádí výhradně- nebo operace (XOR) Chcete-li přepnout hodnotu <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.  
  
 Použít tento příklad kódu, kompilaci a spuštění aplikace a pak klikněte na **doprostřed (Spring)** na <xref:System.Windows.Forms.StatusStrip> ovládacího prvku na hodnotu přepínače <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> vlastnost.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
