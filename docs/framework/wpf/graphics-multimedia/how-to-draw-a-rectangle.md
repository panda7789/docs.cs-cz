---
title: "Postupy: Vykreslení obdélníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a>Postupy: Vykreslení obdélníku
Tento příklad ukazuje, jak k vykreslení obdélníku pomocí <xref:System.Windows.Shapes.Rectangle> elementu.  
  
 Kreslení obdélníku, vytvoření <xref:System.Windows.Shapes.Rectangle> elementu a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>. Chcete-li malovat uvnitř obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>. Rámeček přehled, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti.  
  
 Umožnit rámeček zaoblenými hranami, zadejte nepovinný <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastavit vlastnosti osy x a y poloměr se třemi tečkami, kterého má být zaokrouhleno rozích rámeček.  
  
 V následujícím příkladu dvě <xref:System.Windows.Shapes.Rectangle> elementy jsou vykreslovány <xref:System.Windows.Controls.Canvas>. Má první rámeček <xref:System.Windows.Media.Brushes.Blue%2A> vnitřních. Druhý rámeček má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřních, <xref:System.Windows.Media.Brushes.Black%2A> outline a zaoblenými hranami.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala obdélníků, můžete použít elementy obdélníku (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje. Ve skutečnosti jsou obzvláště užitečná pro zajištění pozadí části obdélníků <xref:System.Windows.Controls.Grid> panelů. Příklad, naleznete v části [tabulky přehled](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Rectangle>  
 [Ukázka elementy obrazce](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [Tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Tabulka – přehled](../../../../docs/framework/wpf/advanced/table-overview.md)
