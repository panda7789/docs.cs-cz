---
title: 'Postupy: Zkosení barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 204f15ce44d5ad688be0ea9ac0fa4a90781b25dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-shear-colors"></a>Postupy: Zkosení barev
Zkosení zvyšuje nebo snižuje komponentu Barva o částku úměrná jiné barevnou složku. Představte si třeba transformaci, kde komponentu red vzroste polovina hodnotou modré součásti. V části transformace by stát barvu (0,2, 0,5, 1) (0,7, 0,5, 1). Novou red součást je 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars4.bmp. Kód pak použije transformaci zkosení popsané v předchozím odstavci pro každý pixelů v bitové kopii.  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii ořezanými na pravé straně.  
  
 ![Zkosení barev](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po transformaci zkosení.  
  
|Původní|Zrcadlili|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `ColorBars.bmp` s název bitové kopie a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
