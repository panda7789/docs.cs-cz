---
title: 'Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 8f3d2f2ed290c61c898a9f6159f213a8f68731ee
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707284"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci
Můžete přizpůsobit vzhled vašich <xref:System.Windows.Forms.ToolStrip> řídí jednotlivě nebo pro všechny <xref:System.Windows.Forms.ToolStrip> ovládacích prvků ve vaší aplikaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak selektivně použít vlastní zobrazovací jednotky k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Pokud chcete použít tento příklad kódu, kompilaci a spuštění aplikace a vyberte vlastní roztržení z oboru <xref:System.Windows.Forms.ComboBox> ovládacího prvku. Klikněte na tlačítko **použít** k nastavení vykreslovacího modulu.  
  
 Pokud chcete zobrazit vykreslení položky nabídky vlastní, vyberte <xref:System.Windows.Forms.MenuStrip> možnost <xref:System.Windows.Forms.ComboBox> řídit, klikněte na tlačítko **použít**a pak otevřete **souboru** položky nabídky.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Nastavte <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost platí pro všechny vlastní zobrazovací jednotky <xref:System.Windows.Forms.ToolStrip> ovládacích prvků ve vaší aplikaci.  
  
 Nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost použít vlastní zobrazovací jednotky pro jednotlivý <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
