---
title: 'Postupy: Vykreslení obdélníku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452932"
---
# <a name="how-to-draw-a-rectangle"></a>Postupy: Vykreslení obdélníku
Tento příklad ukazuje, jak vykreslit obdélník pomocí elementu <xref:System.Windows.Shapes.Rectangle>.  
  
 Chcete-li nakreslit obdélník, vytvořte prvek <xref:System.Windows.Shapes.Rectangle> a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Chcete-li malovat uvnitř obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>. Chcete-li obdélník obsloužit jako obrys, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a vlastnosti <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.  
  
 Chcete-li dát obdélník zaoblené rohy, určete volitelné <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a vlastnosti <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>. Vlastnosti <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastavují poloměry osy x a y na elipse, která se používá k zaoblení rohů obdélníku.  
  
 V následujícím příkladu jsou vykresleny dva prvky <xref:System.Windows.Shapes.Rectangle> v <xref:System.Windows.Controls.Canvas>. První obdélník má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní. Druhý obdélník má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřek, <xref:System.Windows.Media.Brushes.Black%2A> osnovu a zaoblené rohy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k zahrnutí obdélníků, můžete použít prvky Rectangle (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový. Obdélníky jsou zejména užitečné pro poskytování pozadí pro části <xref:System.Windows.Controls.Grid> panelů. Příklad naleznete v [tabulce Přehled](../advanced/table-overview.md).  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Rectangle>
- [Prvky tvaru – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled tabulek](../advanced/table-overview.md)
