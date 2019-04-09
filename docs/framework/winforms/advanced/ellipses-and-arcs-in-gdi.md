---
title: Elipsy a oblouky v rozhraní GDI+
ms.date: 03/30/2017
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
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117453"
---
# <a name="ellipses-and-arcs-in-gdi"></a>Elipsy a oblouky v rozhraní GDI+
Můžete snadno kreslení elipsy a oblouky pomocí <xref:System.Drawing.Graphics.DrawEllipse%2A> a <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> třídy.  
  
## <a name="drawing-an-ellipse"></a>Kreslení elipsy  
 Chcete-li nakreslit elipsu, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawEllipse%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, například šířku a barvu čáry použité k vykreslení elipsy. <xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Zbývající argumenty předané <xref:System.Drawing.Graphics.DrawEllipse%2A> metody zadejte ohraničující obdélník elipsy. Následující obrázek znázorňuje elipsa spolu s jeho ohraničující obdélník.  
  
 ![Elipsy a oblouky](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Následující příklad kreslení plné elipsy; ohraničující obdélník má šířku 80, výška 40 a levého horního rohu (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit <xref:System.Drawing.Rectangle> a předejte mu <xref:System.Drawing.Rectangle> k <xref:System.Drawing.Graphics.DrawEllipse%2A> metody jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Kreslení oblouk  
 Oblouku je část elipsu. Chcete-li nakreslit oblouk, zavolejte <xref:System.Drawing.Graphics.DrawArc%2A> metodu <xref:System.Drawing.Graphics> třídy. Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody jsou stejné jako parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, s výjimkou, že <xref:System.Drawing.Graphics.DrawArc%2A> vyžaduje počáteční úhel a úhel oblouku. Následující příklad nakreslí oblouk s počáteční úhel ze stupňů 30 a úhel oblouku 180 stupňů:  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Následující obrázek znázorňuje oblouku elipsy a ohraničující obdélník.  
  
 ![Elipsy a oblouky](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Postupy: Vytvoření pera](how-to-create-a-pen.md)
- [Postupy: Kreslení obrazce s obrysem](how-to-draw-an-outlined-shape.md)
