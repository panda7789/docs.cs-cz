---
title: 'Postupy: Vytvoření kvadratické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452068"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Postupy: Vytvoření kvadratické Bézierovy křivky
Tento příklad ukazuje, jak vytvořit kvadratickou Bézierovu křivku.  Chcete-li vytvořit kvadratickou Bézierovu křivku, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech je kvadratická Bézierova křivka vykreslena z (10 100) do (300 100). Křivka má řídicí bod (200 200).  
  
 formátu  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete použít syntaxi atributu k popisu cesty.  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 formátu  
  
 (Všimněte si, že tato syntaxe atributu ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, což je verze <xref:System.Windows.Media.PathGeometry>s světlejší váhou. Další informace naleznete na stránce [syntaxe označení cesty](path-markup-syntax.md) .)  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze také nakreslit kvadratickou Bézierovu křivku pomocí syntaxe elementů objektu. Následující příklad je ekvivalentní k předchozímu příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Viz také

- [Vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md)
- [Vytvoření kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md)
