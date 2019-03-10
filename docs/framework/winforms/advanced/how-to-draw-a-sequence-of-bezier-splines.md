---
title: 'Postupy: Kreslení sekvence B&#233;zier křivek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711786"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Postupy: Kreslení sekvence B&#233;zier křivek
Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třídy kreslení sekvence Bézierových křivek.  
  
## <a name="example"></a>Příklad  
 Následující příklad nakreslí křivku, která se skládá ze dvou připojených Bézierovy křivky. Koncový bod první Bézierovy křivky se počáteční bod druhý Bézierovy křivky.  
  
 Následující obrázek znázorňuje připojených křivky spolu s sedm bodů.  
  
 ![Bezier Spline](./media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Bézierovy křivky v GDI+](bezier-splines-in-gdi.md)
- [Sestavování a kreslení křivek](constructing-and-drawing-curves.md)
