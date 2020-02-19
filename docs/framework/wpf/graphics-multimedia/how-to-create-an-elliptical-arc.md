---
title: 'Postupy: Vytvoření oblouku elipsy'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453062"
---
# <a name="how-to-create-an-elliptical-arc"></a>Postupy: Vytvoření oblouku elipsy
Tento příklad ukazuje, jak nakreslit eliptický oblouk. Chcete-li vytvořit eliptický oblouk, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.ArcSegment>.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech je eliptický oblouk vykreslen z (10 100) do (200 100). Oblouk má <xref:System.Windows.Media.ArcSegment.Size%2A> 100, 50 pixelů nezávislých na zařízení, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stupňů, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> nastavení `true`a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 formátu  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete použít syntaxi atributu k popisu cesty.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 formátu  
  
 (Všimněte si, že tato syntaxe atributu ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, což je verze <xref:System.Windows.Media.PathGeometry>s světlejší váhou. Další informace naleznete na stránce [syntaxe označení cesty](path-markup-syntax.md) .)  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze také nakreslit eliptický oblouk explicitním použitím značek objektů. Následující kód je ekvivalentem předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] označení.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Tento příklad je součástí většího vzorku. Úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Viz také

- [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md)
- [Vytvoření kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md)
