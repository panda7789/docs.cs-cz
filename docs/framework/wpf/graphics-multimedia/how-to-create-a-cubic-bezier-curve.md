---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 6332129179e1934e5a37c7a1a40ef5f46ab669a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Postupy: Vytvoření kubické Bézierovy křivky
Tento příklad ukazuje postup vytvoření krychlový Bézierovu křivku. Chcete-li vytvořit krychlový Bézierovu křivku, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.BezierSegment> třídy.  Chcete-li zobrazit výsledné geometry, použijte <xref:System.Windows.Shapes.Path> element, nebo použít je s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. V následujících příkladech se nevykreslí krychlový Bézierovu křivku z (10, 100) na (300, 100). Křivku má ovládací prvek body (100, 0) a (200, 200).  
  
## <a name="example"></a>Příklad  
 [xaml]  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít syntaxi zkrácené značek k popisu cestu.  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit krychlový Bézierovu křivku pomocí značek object. Tady je ekvivalentem předchozího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření oblouku elipsy](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [Vytvoření LineSegment v PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [Vytvoření kubické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [Vytvoření kvadratické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
