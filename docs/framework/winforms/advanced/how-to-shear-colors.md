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
ms.openlocfilehash: bf645cf88c4905cd5cf47c2a6c7af088fa428c8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076240"
---
# <a name="how-to-shear-colors"></a>Postupy: Zkosení barev
Zkosení zvyšuje nebo snižuje složku barvy podle zadaného množství úměrná jiné součásti barvy. Představte si třeba transformace, kde se hodnota červené zvýší o polovinu hodnota modré. V takové transformace barvu (0.2, 0,5, 1) by se mohla stát (0,7, 0,5, 1). Nová hodnota červené je 0.2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars4.bmp. Potom kód použije transformace zkosení je popsáno v předchozím odstavci každý pixel na obrázku.  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a zkosené image na pravé straně: 
  
 ![Dvě pole s barevné pruhy – souběžně ilustrující původní bitové kopie a zkosené bitové kopie.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po transformaci zkosení.  
  
|Původní|Stříhanou|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs>`e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `ColorBars.bmp` image název a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v rozhraní Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
