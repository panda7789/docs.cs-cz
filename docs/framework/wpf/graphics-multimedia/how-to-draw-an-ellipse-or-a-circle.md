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
ms.openlocfilehash: 1393e158c1787dc7d4e44e5e1c90ed2e65666dc3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146741"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Postupy: Vykreslení elipsy nebo kruhu
Tento příklad ukazuje, jak pomocí vykreslení elipsy nebo kruhu <xref:System.Windows.Shapes.Ellipse> elementu. Chcete-li nakreslit elipsu, vytvořte <xref:System.Windows.Shapes.Ellipse> element a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Použití jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti a určit tak <xref:System.Windows.Media.Brush> , který se používá k vyplnění vnitřku elipsy. Použití jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti a určit tak <xref:System.Windows.Media.Brush> , který slouží k vykreslení osnovy na tři tečky. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Vlastnost určuje tloušťku obrysu elipsy.  
  
 Pokud chcete nakreslit kruh, ujistěte se, <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> prvek s hodnotou k sobě navzájem.  
  
 Následující příklad nakreslí čtyři <xref:System.Windows.Shapes.Ellipse> elementů v rámci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> obsahovat symbol tří teček, můžete použít prvky tři tečky (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Ukázka elementy obrazce](https://go.microsoft.com/fwlink/?LinkID=160037)
