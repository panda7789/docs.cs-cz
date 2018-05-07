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
ms.openlocfilehash: 69620d81eb77eb76f21f099b30017b142d818457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Postupy: Vykreslení elipsy nebo kruhu
Tento příklad ukazuje, jak k vykreslení tři tečky a kroužky pomocí <xref:System.Windows.Shapes.Ellipse> elementu. Kreslení elipsy, vytvořit <xref:System.Windows.Shapes.Ellipse> elementu a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Použijte jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti k určení, <xref:System.Windows.Media.Brush> sloužící k vyplnění vnitřku se třemi tečkami. Použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti k určení, <xref:System.Windows.Media.Brush> sloužící k vyplnění obrys se třemi tečkami. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Vlastnost určuje Tloušťka obrysu třemi tečkami.  
  
 Kreslení kruh, zkontrolujte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> element rovna navzájem.  
  
 Následující příklad nevykresluje čtyři <xref:System.Windows.Shapes.Ellipse> elementů v rámci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala na symbol tří teček, můžete použít prvky třemi tečkami (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [Ukázka elementy obrazce](http://go.microsoft.com/fwlink/?LinkID=160037)
