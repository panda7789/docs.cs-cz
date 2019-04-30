---
title: 'Postupy: Vytvoření tvaru pomocí PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: b0ab703596612524881ab892a1095b0f49cd1551
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904307"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Postupy: Vytvoření tvaru pomocí PathGeometry
Tento příklad ukazuje postup vytvoření tvaru použitím <xref:System.Windows.Media.PathGeometry> třídy. <xref:System.Windows.Media.PathGeometry> objekty se skládají z nejméně jednu <xref:System.Windows.Media.PathFigure> objektů; každý <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvar. Každý <xref:System.Windows.Media.PathFigure> samotný tvoří jeden nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představující připojených část obrázku nebo tvar. Segment typy zahrnují <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, a <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.PathGeometry> vytvořit trojúhelník. <xref:System.Windows.Media.PathGeometry> Se zobrazí pomocí <xref:System.Windows.Shapes.Path> elementu.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Trojúhelník vytvořené pomocí PathGeometry  
  
 Předchozí příklad ukázal, jak vytvořit obrazec poměrně jednoduchý trojúhelník. A <xref:System.Windows.Media.PathGeometry> slouží také k vytvoření složitějších tvary, včetně oblouky křivky. Příklady najdete v tématu [vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md), [vytvoření Kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md), a [vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Přehled geometrie](geometry-overview.md)
- [Ukázka geometrie](https://go.microsoft.com/fwlink/?LinkID=159989)
