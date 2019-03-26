---
title: 'Postupy: Kreslení textu v určeném umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 8327043f9afdec7e2d84e564801342d7d7cbef9d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412237"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Postupy: Kreslení textu v určeném umístění
Při provádění vlastní kreslení můžete nakreslit text v jedné vodorovnou horizontální čáru od k určitému bodu. Tímto způsobem můžete nakreslit text pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody <xref:System.Drawing.Graphics> třídu, která přijímá <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF> parametru. <xref:System.Drawing.Graphics.DrawString%2A> Také vyžaduje metodu <xref:System.Drawing.Brush> a <xref:System.Drawing.Font>  
  
 Můžete také použít <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížené metody <xref:System.Windows.Forms.TextRenderer> , která přijímá <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> také vyžaduje <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.  
  
 Následující obrázek znázorňuje výstup textu při použití vykreslit k určitému bodu <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody.  
  
 ![Snímek obrazovky zobrazující výstup textu v určeném okamžiku.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Chcete-li nakreslit řádek textu pomocí GDI +  
  
1.  Použití <xref:System.Drawing.Graphics.DrawString%2A> předejte text, který má <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Chcete-li nakreslit řádek textu pomocí GDI  
  
1.  Použití <xref:System.Windows.Forms.TextRenderer.DrawText%2A> předejte text, který má <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyžadovat v předchozích příkladech:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)
- [Použití písem a textu](using-fonts-and-text.md)
- [Postupy: Vytváření rodin písem a písem](how-to-construct-font-families-and-fonts.md)
- [Postupy: Kreslení zalomeného textu do obdélníku](how-to-draw-wrapped-text-in-a-rectangle.md)
