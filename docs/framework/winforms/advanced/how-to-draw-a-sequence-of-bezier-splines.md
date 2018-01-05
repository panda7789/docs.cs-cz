---
title: "Postupy: kreslení sekvence B &#233; zier křivky vyhlazení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5bdd9ae29dcbb8397d2fe645e240572aad32a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Postupy: kreslení sekvence B &#233; zier křivky vyhlazení
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
