---
title: 'Postupy: Implementace vlastního prvku ToolStripRenderer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: acf5967c015d61a0cc148e5cb509a5a7ded2152c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533195"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Postupy: Implementace vlastního prvku ToolStripRenderer
Můžete přizpůsobit vzhled <xref:System.Windows.Forms.ToolStrip> řízení implementací třídu odvozenou z <xref:System.Windows.Forms.ToolStripRenderer>. To vám dává flexibilitu při vytváření vzhledu, která se liší od vzhled zadaný <xref:System.Windows.Forms.ToolStripProfessionalRenderer> a <xref:System.Windows.Forms.ToolStripSystemRenderer> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak implementovat vlastní <xref:System.Windows.Forms.ToolStripRenderer> třídy. V tomto příkladu `GridStrip` ovládací prvek implementuje stavebnice klouzavé dlaždice, který umožňuje uživatelům přesunutí dlaždice v rozložení tabulky a vytvořit bitovou kopii. Vlastní <xref:System.Windows.Forms.ToolStrip> řízení uspořádá jeho <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků v rozložení mřížky. Rozložení obsahuje jeden prázdné buňky, do kterého může uživatel Vysuňte přiléhající dlaždice pomocí operace přetažení myší. Jsou vyznačené dlaždice, které může uživatel přesunout.  
  
 `GridStripRenderer` Třída přizpůsobí tři aspekty `GridStrip` vzhledu ovládacího prvku:  
  
-   `GridStrip` Ohraničení  
  
-   <xref:System.Windows.Forms.ToolStripButton> Ohraničení  
  
-   <xref:System.Windows.Forms.ToolStripButton> Bitové kopie  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
