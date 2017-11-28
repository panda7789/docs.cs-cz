---
title: "Elipsy a oblouky v rozhraní GDI+"
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebeae1d076a0ebcf36d52dee1af0c0ad5f04fdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a>Elipsy a oblouky v rozhraní GDI+
Můžete snadno kreslení elipsy a oblouky pomocí <xref:System.Drawing.Graphics.DrawEllipse%2A> a <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> třídy.  
  
## <a name="drawing-an-ellipse"></a>Kreslení elipsy  
 Kreslení elipsy, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawEllipse%2A> metody a <xref:System.Drawing.Pen> objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení se třemi tečkami. <xref:System.Drawing.Pen> Objekt je předán jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda. Zbývající argumenty předaný <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda zadejte ohraničující obdélník pro se třemi tečkami. Následující obrázek znázorňuje elipsy společně s jeho ohraničující obdélník.  
  
 ![Elipsy a oblouky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Následující příklad nevykresluje elipsy; ohraničující obdélník má šířku 80, výška 40 a levého horního rohu (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>je přetížené metodu <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit <xref:System.Drawing.Rectangle> a předat <xref:System.Drawing.Rectangle> k <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Kreslení oblouk  
 Oblouk je část elipsy. Chcete-li nakreslit oblouk, zavolejte <xref:System.Drawing.Graphics.DrawArc%2A> metodu <xref:System.Drawing.Graphics> – třída. Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody jsou stejné jako parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda, vyjma toho, že <xref:System.Drawing.Graphics.DrawArc%2A> vyžaduje počáteční úhel a úhel oblouku. Následující příklad nakreslí oblouk s počáteční úhel 30 stupňů a úhel oblouku 180 stupňů:  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Následující obrázek znázorňuje oblouk, se třemi tečkami a ohraničující obdélník.  
  
 ![Elipsy a oblouky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Čar, křivek a obrazců](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Postupy: vytvoření pera](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Postupy: kreslení obrazce s obrysem](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
