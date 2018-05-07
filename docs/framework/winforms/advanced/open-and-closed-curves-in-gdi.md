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
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="open-and-closed-curves-in-gdi"></a>Otevřené a uzavřené křivky v GDI+
Následující obrázek znázorňuje dvě: jeden otevřete a jeden zavřené.  
  
 ![Otevřené a uzavřené křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Spravovaná rozhraní pro křivek  
 Uzavřené křivky mít vnitřním a proto může být vyplněna štětcem. <xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro naplnění uzavřené tvarů a křivek: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, a <xref:System.Drawing.Graphics.FillRegion%2A>. Při každém volání jednoho z těchto metod, je nutné předat jeden z typů konkrétní štětce (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, nebo <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> Metoda je Pomocníka pro <xref:System.Drawing.Graphics.DrawArc%2A> metoda. Stejně jako <xref:System.Drawing.Graphics.DrawArc%2A> metoda vykreslí část obrys elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda doplní část vnitřek elipsy. Následující příklad nakreslí oblouk a výplní odpovídající část vnitřek se třemi tečkami:  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Následující obrázek znázorňuje oblouk a vyplněné výseč.  
  
 ![Otevřené a uzavřené křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> Metoda je Pomocníka pro <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metoda. Obě metody automaticky uzavřít křivku připojením koncový bod se počáteční bod. Následující příklad nakreslí křivku, které procházejí (0, 0), (60, 20) a (40, 50). Potom automaticky zavře křivku připojením (40, 50) do výchozího bodu (0, 0), a vnitřní je vyplněn plnou barvou.  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Metoda doplní vnitřek samostatné části cesty. Pokud není část cesty formuláři uzavřené křivky nebo tvaru, <xref:System.Drawing.Graphics.FillPath%2A> metody se automaticky zavře tuto část cesty před jeho naplnění. Následující příklad nevykresluje a výplní cestu, která se skládá z oblouk, křivky mohutnosti, řetězec a výsečový:  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Následující obrázek ukazuje cestu s i bez plné výplně. Všimněte si, že je text v řetězci uvedené, ale není vyplněno, pomocí <xref:System.Drawing.Graphics.DrawPath%2A> metoda. Je <xref:System.Drawing.Graphics.FillPath%2A> metoda, která vybarví vnitřek znaky v řetězci.  
  
 ![Řetězec cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Sestavování a kreslení cest](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
