---
title: 'Postupy: Vytvoření formuláře MDI se slučováním nabídek a ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 2942d0e92a0f58bef5533d69b27a646d284fef62
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721109"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Postupy: Vytvoření formuláře MDI se slučováním nabídek a ovládacích prvcích ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více dokumentů aplikace (MDI interface) a <xref:System.Windows.Forms.MenuStrip> ovládací prvek podporuje slučování nabídek. MDI formuláře můžete také <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.  
  
 Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.  
  
 Viz také [názorný postup: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků formuláře MDI. Formulář podporuje také s nabídkami podřízené slučováním nabídek.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad kódu vyžaduje:  
  
-   Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
