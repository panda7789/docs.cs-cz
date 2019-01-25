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
ms.openlocfilehash: bde3271398c6bc6a37c975476b76acb85511c1a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589829"
---
# <a name="how-to-shear-colors"></a>Postupy: Zkosení barev
Zkosení zvyšuje nebo snižuje složku barvy podle zadaného množství úměrná jiné součásti barvy. Představte si třeba transformace, kde se hodnota červené zvýší o polovinu hodnota modré. V takové transformace barvu (0.2, 0,5, 1) by se mohla stát (0,7, 0,5, 1). Nová hodnota červené je 0.2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars4.bmp. Potom kód použije transformace zkosení je popsáno v předchozím odstavci každý pixel na obrázku.  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a zkosené image na pravé straně.  
  
 ![Zkosení barev](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po transformaci zkosení.  
  
|Původní|Stříhanou|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `ColorBars.bmp` image název a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
