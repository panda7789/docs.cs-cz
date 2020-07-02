---
title: 'Postupy: Vykreslení elipsy nebo kruhu'
description: Naučte se, jak nakreslit elipsu nebo kroužek s volbami pro tloušťku obrysu a vnitřní barvu v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853566"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Postupy: Vykreslení elipsy nebo kruhu
Tento příklad ukazuje, jak kreslit elipsy a kroužky pomocí <xref:System.Windows.Shapes.Ellipse> elementu. Chcete-li nakreslit elipsu, vytvořte <xref:System.Windows.Shapes.Ellipse> element a určete jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> . Použijte jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost k určení <xref:System.Windows.Media.Brush> , která se používá k vykreslování vnitřku elipsy. Použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnost k určení <xref:System.Windows.Media.Brush> , který slouží k vykreslování obrysu elipsy. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Vlastnost určuje tloušťku obrysu elipsy.  
  
 Chcete-li nakreslit kruh, je nutné, aby byl <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> prvek a elementu rovny navzájem.  
  
 Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Ellipse> prvky v rámci <xref:System.Windows.Controls.Canvas> .  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 I když tento příklad používá a <xref:System.Windows.Controls.Canvas> obsahuje tři tečky, můžete použít prvky elipsy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje obsah, který není textový.  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Prvky tvaru – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
