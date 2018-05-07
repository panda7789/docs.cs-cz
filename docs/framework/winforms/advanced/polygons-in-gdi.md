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
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="polygons-in-gdi"></a>Mnohoúhelníky v GDI+
Mnohoúhelníku je uzavřený obrazec s tři nebo více rovné strany. Například trojúhelníček je mnohoúhelník s tři strany, obdélníku je mnohoúhelník s čtyři strany a pětiúhelník je mnohoúhelník s pěti stranách. Následující obrázek znázorňuje několik mnohoúhelníky.  
  
 ![Mnohoúhelníky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Kreslení mnohoúhelníku  
 Kreslení mnohoúhelníku, musíte <xref:System.Drawing.Graphics> objekt, <xref:System.Drawing.Pen> objekt a pole <xref:System.Drawing.Point> (nebo <xref:System.Drawing.PointF>) objekty. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawPolygon%2A> metoda. <xref:System.Drawing.Pen> Objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení mnohoúhelníku a pole <xref:System.Drawing.Point> objekty ukládá body připojí pomocí přímých řádky. <xref:System.Drawing.Pen> Objekt a pole <xref:System.Drawing.Point> jako argumenty pro předávání objektů <xref:System.Drawing.Graphics.DrawPolygon%2A> metoda. Následující příklad nevykresluje zachytávání tři mnohoúhelníku. Všimněte si, že jsou jenom tři body v `myPointArray`: (0, 0), (50, 30) a (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Metoda automaticky zavře mnohoúhelníku ve kreslení řádek ze (30, 60) zpět na výchozí bod (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Následující obrázek znázorňuje mnohoúhelníku.  
  
 ![Mnohoúhelníku](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Vytvoření pera](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
