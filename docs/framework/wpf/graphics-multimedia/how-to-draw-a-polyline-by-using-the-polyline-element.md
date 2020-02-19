---
title: 'Postupy: Vykreslení lomené čáry použitím elementu lomené čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452958"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Postupy: Vykreslení lomené čáry použitím elementu lomené čáry
Tento příklad ukazuje, jak nakreslit lomenou čáru, což je řada propojených řádků pomocí prvku <xref:System.Windows.Shapes.Polyline>.  
  
 Chcete-li nakreslit lomenou čáru, vytvořte <xref:System.Windows.Shapes.Polyline> element a použijte jeho vlastnost <xref:System.Windows.Shapes.Polyline.Points%2A> k určení vrcholů tvaru. Nakonec pomocí vlastností <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> popište obrys lomené čáry, protože čára bez tahu není viditelná.  
  
> [!NOTE]
> Vzhledem k tomu, že <xref:System.Windows.Shapes.Polyline> element není uzavřený obrazec, vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> nemá žádný vliv, i když záměrně uzavřete obrys tvaru. Chcete-li vytvořit uzavřený obrazec pomocí <xref:System.Windows.Shapes.Shape.Fill%2A>, použijte prvek <xref:System.Windows.Shapes.Polygon>.  
  
 Následující příklad kreslí dva prvky <xref:System.Windows.Shapes.Polyline> v rámci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]je platná syntaxe pro body oddělená mezerami čárkami oddělený seznam párů souřadnic x a y.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k tomu, aby obsahovala lomené čáry, můžete použít prvky lomené čáry (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Prvky tvaru – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
