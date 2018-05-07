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
ms.openlocfilehash: e55afd0629c1b9e6d30c8b31116ec28a718fcb4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Postupy: Kreslení textu v určeném umístění
Při provádění vlastní kreslení je nakreslit text ve vodorovném jeden řádek začínající na zadaný bod. Tímto způsobem můžete nakreslit text pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížený metodu <xref:System.Drawing.Graphics> třídu, která přebírá <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF> parametr. <xref:System.Drawing.Graphics.DrawString%2A> Metoda také vyžaduje, <xref:System.Drawing.Brush> a <xref:System.Drawing.Font>  
  
 Můžete také <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížený metodu <xref:System.Windows.Forms.TextRenderer> , která má <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> také vyžaduje <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.  
  
 Následující obrázek ukazuje výstup textu vykreslovat Zadaný bod při použití <xref:System.Drawing.Graphics.DrawString%2A> metodu přetížených.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Kreslení na řádku textu pomocí GDI +  
  
1.  Použití <xref:System.Drawing.Graphics.DrawString%2A> metodu předáním text, který má, <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Kreslení na řádku textu pomocí GDI  
  
1.  Použití <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu předáním text, který má, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyžadovat v předchozích příkladech:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Postupy: Vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Postupy: Kreslení zalomeného textu do obdélníku](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
