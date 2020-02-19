---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452971"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku
Tento příklad ukazuje, jak nakreslit uzavřený obrazec pomocí elementu <xref:System.Windows.Shapes.Polygon>. Chcete-li nakreslit uzavřený obrazec, vytvořte <xref:System.Windows.Shapes.Polygon> element a použijte jeho vlastnost <xref:System.Windows.Shapes.Polygon.Points%2A> k určení vrcholů tvaru. Čára se automaticky vykreslí, aby propojuje první a poslední bod. Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>nebo obojí.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]je platná syntaxe pro body oddělená mezerami čárkami oddělený seznam párů souřadnic x a y.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Přestože příklad používá <xref:System.Windows.Controls.Canvas> k zahrnutí mnohoúhelníků, můžete použít mnohoúhelníkové elementy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).
