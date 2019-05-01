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
ms.openlocfilehash: 146ca7017ee38ad5c1065e59662ac441e7bfbfe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965409"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Postupy: Definice obdélníku pomocí RectangleGeometry
Tento příklad popisuje způsob použití <xref:System.Windows.Media.RectangleGeometry> tříd k popisu obdélníku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.RectangleGeometry>.  Relativní pozice a rozměry obdélníku jsou definovány <xref:System.Windows.Rect> struktury. Relativní pozice je `50,50` a výška a šířka jsou obě `25` Vytvoření čtverce. Vnitřní obdélníku je vybarvené <xref:System.Windows.Media.Brushes.LemonChiffon%2A> štětce a jeho osnovy vymalováním s <xref:System.Windows.Media.Brushes.Black%2A> od ruky s tloušťkou `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Přestože tento příklad používá <xref:System.Windows.Shapes.Path> elementu k vykreslení <xref:System.Windows.Media.RectangleGeometry>, existuje mnoho způsobů použití <xref:System.Windows.Media.RectangleGeometry> objekty. Například <xref:System.Windows.Media.RectangleGeometry> slouží k určení <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> nebo <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.  
  
 Zahrnout další jednoduché geometrické třídy <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>. Tyto geometrie, jakož i složitější ty lze také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Viz také:

- [Přehled geometrie](geometry-overview.md)
- [Vytvoření složeného tvaru](how-to-create-a-composite-shape.md)
- [Vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
