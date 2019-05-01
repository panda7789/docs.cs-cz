---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 36544abc774b7fe82c2ff47483cfedd6fb13e344
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054624"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Postupy: Vytvoření kubické Bézierovy křivky
Tento příklad ukazuje postup vytvoření kubické Bézierovy křivky. K vytvoření kubické Bézierovy křivky, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.BezierSegment> třídy.  Chcete-li zobrazit výsledné geometrie, použijte <xref:System.Windows.Shapes.Path> element, nebo použít je s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. V následujících příkladech kubické Bézierovy křivky přenesou z (10, 100) na (300, 100). Křivka má ovládací prvek body (100, 0) a (200, 200).  
  
## <a name="example"></a>Příklad  
 [xaml]  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít k popisu cesty syntaxe zkrácený značek.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit kubické Bézierovy křivky pomocí značky object. Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md)
- [Vytvoření LineSegment v PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Vytvoření kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md)
- [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md)
