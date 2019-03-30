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
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654247"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Postupy: Kreslení sekvence B&#233;zier křivek
Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třídy kreslení sekvence Bézierových křivek.  
  
## <a name="example"></a>Příklad  
 Následující příklad nakreslí křivku, která se skládá ze dvou připojených Bézierovy křivky. Koncový bod první Bézierovy křivky se počáteční bod druhý Bézierovy křivky.  
  
 Následující obrázek znázorňuje připojených křivky spolu s sedm body:  
  
 ![Obrázek znázorňující, připojené křivky spolu s sedm bodů.](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Bézierovy křivky v GDI+](bezier-splines-in-gdi.md)
- [Sestavování a kreslení křivek](constructing-and-drawing-curves.md)
