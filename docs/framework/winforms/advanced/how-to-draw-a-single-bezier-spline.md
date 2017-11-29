---
title: "Postupy: kreslení jedné B &#233; zier křivkový"
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
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ebdba9e01824cc764a6ab759da049add180ba83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Postupy: kreslení jedné B &#233; zier křivkový
Bézierovy křivky je definována čtyři body: počáteční bod, dvě kontrolních bodů a koncový bod.  
  
## <a name="example"></a>Příklad  
 Následující příklad kreslení Bézierovy křivky se počáteční bod (10, 100) a koncového bodu (200, 100). Ovládací prvek body jsou (100, 10) a (150 150).  
  
 Následující obrázek znázorňuje výsledné Bézierovy křivky společně s jeho počáteční bod, kontrolní body a koncového bodu. Na obrázku také ukazuje konvexní trup křivky, který je vytvořen propojením čtyři body s přímky mnohoúhelníku.  
  
 ![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [Bézierovy křivky v GDI +](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Postupy: kreslení sekvence Bézierových křivek](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
