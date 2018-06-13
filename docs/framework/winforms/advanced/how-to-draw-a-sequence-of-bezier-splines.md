---
title: 'Postupy: kreslení sekvence B&#233;zier křivky vyhlazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 8439e08109630b9a59c8e0359aa4d18e5241412c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521404"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Postupy: kreslení sekvence B&#233;zier křivky vyhlazení
Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třída pro kreslení sekvence Bézierových křivek.  
  
## <a name="example"></a>Příklad  
 Následující příklad nakreslí křivku, který se skládá ze dvou připojené Bézierovy křivky. Koncový bod první Bézierovy křivky je počáteční bod druhý Bézierovy křivky.  
  
 Následující obrázek znázorňuje připojené křivky společně s sedm body.  
  
 ![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Bézierovy křivky v GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Sestavování a kreslení křivek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
