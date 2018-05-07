---
title: 'Postupy: Definice obdélníku pomocí RectangleGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 5d2ec6aec1eea8528ea6b43f72f4820b8bc19a37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Postupy: Definice obdélníku pomocí RectangleGeometry
Tento příklad popisuje postup použití <xref:System.Windows.Media.RectangleGeometry> třída k popisu obdélníku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.RectangleGeometry>.  Definované relativní pozici a dimenze obdélníku <xref:System.Windows.Rect> struktury. Je relativní pozici `50,50` a výška a šířka jsou obě `25` vytváření čtverce. Vykreslení obdélníku interior s <xref:System.Windows.Media.Brushes.LemonChiffon%2A> štětce a jeho přehled vykreslením s <xref:System.Windows.Media.Brushes.Black%2A> tahu s tloušťkou `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![Objekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 I když tento příklad používá <xref:System.Windows.Shapes.Path> element k vykreslení <xref:System.Windows.Media.RectangleGeometry>, existuje mnoho způsobů použití <xref:System.Windows.Media.RectangleGeometry> objekty. Například <xref:System.Windows.Media.RectangleGeometry> lze použít k určení <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> nebo <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.  
  
 Třídy dalších jednoduchý geometrie zahrnují <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>. Tyto geometrie, jakož i složitější těch, můžete také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Viz také  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Vytvoření složeného tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Vytvoření tvaru pomocí PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
