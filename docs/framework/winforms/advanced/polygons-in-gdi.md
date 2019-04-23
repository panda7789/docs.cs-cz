---
title: Mnohoúhelníky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132623"
---
# <a name="polygons-in-gdi"></a>Mnohoúhelníky v GDI+
Mnohoúhelník je uzavřený obrazec se třemi nebo více stran přímo. Například trojúhelník je mnohoúhelník s tři strany obdélníku je mnohoúhelník s čtyřech stranách a pětiúhelník je mnohoúhelník s pěti strany. Následující obrázek znázorňuje několik mnohoúhelníku.  
  
 ![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Kreslení mnohoúhelníku  
 Chcete-li nakreslit mnohoúhelníku, je nutné <xref:System.Drawing.Graphics> objektu, <xref:System.Drawing.Pen> objektu a pole <xref:System.Drawing.Point> (nebo <xref:System.Drawing.PointF>) objekty. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. <xref:System.Drawing.Pen> Ukládá atributy, například šířku a barvu čáry použité k vykreslení mnohoúhelník a pole <xref:System.Drawing.Point> objekty ukládá body pro připojené prostřednictvím přímé čáry. <xref:System.Drawing.Pen> Objektu a pole <xref:System.Drawing.Point> objekty jsou předány jako argumenty, které mají <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. Následující příklad kreslení oboustranný tři mnohoúhelníku. Všimněte si, že jsou jenom tři body v `myPointArray`: (0, 0), (50, 30) a (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Metoda automaticky uzavře mnohoúhelník kreslením řádek z (30, 60) zpět na počáteční bod (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Následující obrázek znázorňuje mnohoúhelníku.  
  
 ![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vytvoření pera](how-to-create-a-pen.md)
