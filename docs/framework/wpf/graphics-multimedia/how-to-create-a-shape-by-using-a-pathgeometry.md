---
title: 'Postupy: Vytvoření tvaru použitím PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452042"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Postupy: Vytvoření tvaru použitím PathGeometry
Tento příklad ukazuje, jak vytvořit obrazec pomocí třídy <xref:System.Windows.Media.PathGeometry>. <xref:System.Windows.Media.PathGeometry> objekty se skládají z jednoho nebo více objektů <xref:System.Windows.Media.PathFigure>; Každý <xref:System.Windows.Media.PathFigure> představuje jiný obrázek nebo tvar. Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru. Typy segmentů zahrnují <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>a <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.PathGeometry> k vytvoření trojúhelníku. <xref:System.Windows.Media.PathGeometry> se zobrazí pomocí elementu <xref:System.Windows.Shapes.Path>.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Trojúhelník vytvořený s PathGeometry  
  
 Předchozí příklad ukázal, jak vytvořit relativně jednoduchý tvar, trojúhelník. <xref:System.Windows.Media.PathGeometry> lze také použít k vytvoření složitějších tvarů, včetně elips a křivek. Příklady naleznete v tématu [Vytvoření eliptického oblouku](how-to-create-an-elliptical-arc.md), [Vytvoření Bézierovy křivky krychle](how-to-create-a-cubic-bezier-curve.md)a [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).  
  
 Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Přehled geometrie](geometry-overview.md)
- [Ukázka geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
