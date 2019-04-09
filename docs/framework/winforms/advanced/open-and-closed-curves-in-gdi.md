---
title: Otevřené a uzavřené křivky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 33a8954296a7e63637ad5e210fb30fba1a3fdd53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165110"
---
# <a name="open-and-closed-curves-in-gdi"></a>Otevřené a uzavřené křivky v GDI+
Následující obrázek znázorňuje dvě křivek: jeden otevřít a jeden zavřené.  
  
 ![Otevřené a uzavřené křivky](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Použití spravovaného rozhraní křivky  
 Uzavřené křivky mají vnitřním a proto může být vyplněny štětce. <xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro vyplnění uzavřených obrazců a křivek: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, a <xref:System.Drawing.Graphics.FillRegion%2A>. Pokaždé, když se bude volat jednu z těchto metod, je nutné předat jednoho z typů konkrétní štětce (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, nebo <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> Metody, který je k <xref:System.Drawing.Graphics.DrawArc%2A> metody. Stejně jako <xref:System.Drawing.Graphics.DrawArc%2A> metoda vykreslí část osnovy elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda vyplní část vnitřní elipsu. V následujícím příkladu Nakreslí oblouk a vyplní odpovídající část vnitřní elipsy:  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Následující obrázek znázorňuje oblouk a plného výseče.  
  
 ![Otevřené a uzavřené křivky](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> Metody, který je k <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody. Obě metody automaticky uzavřít křivka koncový bod připojení k výchozí bod. Následující příklad nakreslí křivku, která prochází (0, 0), (60, 20) a (40, 50). Pak se automaticky ukončí křivka připojením (40, 50) na počáteční bod (0, 0), a vnitřní je vyplněn plnou barvou.  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Metoda vyplní vnitřek samostatné části cesty. Pokud není tvoří část cesty, uzavřené křivky a obrazce, <xref:System.Drawing.Graphics.FillPath%2A> metoda automaticky uzavře danou částí cesty než vyplnění. V následujícím příkladu kreslení a vyplní cestu, která se skládá z oblouk, křivky mohutnosti, řetězce a výsečový:  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Následující obrázek znázorňuje cestu a nemusíte plné barvy. Všimněte si, že je text v řetězci uvedené, ale není vyplněné, tím <xref:System.Drawing.Graphics.DrawPath%2A> metody. Je <xref:System.Drawing.Graphics.FillPath%2A> metodu, která se vybarví vnitřek znaků v řetězci.  
  
 ![Řetězec v cestě](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Sestavování a kreslení cest](constructing-and-drawing-paths.md)
