---
title: 'Postupy: Kreslení jedné B&#233;zier křivky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 0731595dc25b1afb4b3dbcc7eedbfb92ef32d267
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126276"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Postupy: Kreslení jedné B&#233;zier křivky
Bézierovy křivky definoval čtyři body: počáteční bod, dva kontrolních bodů a koncový bod.  
  
## <a name="example"></a>Příklad  
 Následující příklad kreslení Bézierovy křivky s počáteční bod (10, 100) a koncového bodu (200, 100). Ovládací prvek body jsou (100, 10) a (150, 150).  
  
 Následující obrázek znázorňuje výsledný Bézierovy křivky spolu s jeho počáteční bod, kontrolní body a koncový bod. Tento obrázek také ukazuje konvexní trupu křivky, který je tvořen čtyři body sítě s rovné čáry mnohoúhelníku.  
  
 ![Obrázek Bézierovy křivky.](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [Bézierovy křivky v GDI+](bezier-splines-in-gdi.md)
- [Postupy: Kreslení sekvence Bézierových křivek](how-to-draw-a-sequence-of-bezier-splines.md)
