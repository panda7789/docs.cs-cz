---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452107"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Postupy: Vytvoření kubické Bézierovy křivky
Tento příklad ukazuje, jak vytvořit Bézierovu křivku krychle. Chcete-li vytvořit Bézierovu křivku krychle, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.BezierSegment>.  Chcete-li zobrazit výslednou geometrii, použijte prvek <xref:System.Windows.Shapes.Path> nebo jej použijte s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. V následujících příkladech je vykreslená křivka krychle z (10, 100) na (300, 100). Křivka má kontrolní body (100, 0) a (200, 200).  
  
## <a name="example"></a>Příklad  
 formátu  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete k popisu cesty použít syntaxi zkráceného označení.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 formátu  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze také kreslit krychlovou Bézierovu křivku pomocí značek objektů. Následující příklad je ekvivalentní k předchozímu příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Viz také

- [Vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md)
- [Vytvoření LineSegment v PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Vytvoření kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md)
- [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md)
