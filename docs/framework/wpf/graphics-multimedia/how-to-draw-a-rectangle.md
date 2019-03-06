---
title: 'Postupy: Vykreslení obdélníku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 2734d5e808e8bc1f78c281e3fd6ab3c6ff12c58f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363745"
---
# <a name="how-to-draw-a-rectangle"></a>Postupy: Vykreslení obdélníku
Tento příklad ukazuje, jak nakreslit obdélník s použitím <xref:System.Windows.Shapes.Rectangle> elementu.  
  
 Chcete-li nakreslit obdélník, vytvořte <xref:System.Windows.Shapes.Rectangle> element a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Má Vymalovat vnitřní obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>. Obdélník osnovy, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti.  
  
 Abyste obdélník zaoblené rohy, zadejte nepovinný <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastaveny vlastnosti osy x a y poloměr elipsy, který se používá k Zakulacení rohů obdélníku.  
  
 V následujícím příkladu dvě <xref:System.Windows.Shapes.Rectangle> prvky jsou vykreslovány <xref:System.Windows.Controls.Canvas>. Má první obdélník <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní. Je druhý obdélník <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní, <xref:System.Windows.Media.Brushes.Black%2A> osnovy a zaoblené rohy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala obdélníky, můžete použít prvky obdélník (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah. Ve skutečnosti jsou obzvláště užitečná pozadí pro části obdélníky <xref:System.Windows.Controls.Grid> panelů. Příklad najdete v tématu [Přehled tabulek](../advanced/table-overview.md).  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Shapes.Rectangle>
- [Ukázka elementy obrazce](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled tabulky](../advanced/table-overview.md)
