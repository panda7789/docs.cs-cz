---
title: 'Postupy: Vykreslení elipsy nebo kruhu'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452919"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Postupy: Vykreslení elipsy nebo kruhu
Tento příklad ukazuje, jak kreslit elipsy a kroužky pomocí elementu <xref:System.Windows.Shapes.Ellipse>. Chcete-li nakreslit elipsu, vytvořte prvek <xref:System.Windows.Shapes.Ellipse> a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> k určení <xref:System.Windows.Media.Brush>, který se používá k malování vnitřku elipsy. Pomocí vlastnosti <xref:System.Windows.Shapes.Shape.Stroke%2A> určete <xref:System.Windows.Media.Brush>, která se používá k vykreslování obrysu elipsy. Vlastnost <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> určuje tloušťku obrysu elipsy.  
  
 Chcete-li nakreslit kruh, nastavte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> elementu <xref:System.Windows.Shapes.Ellipse> se vzájemně rovnají.  
  
 Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Ellipse> prvky v rámci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k tomu, aby obsahoval tři tečky, můžete použít elipsové elementy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Prvky tvaru – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
