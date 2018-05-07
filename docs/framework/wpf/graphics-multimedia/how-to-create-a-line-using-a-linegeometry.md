---
title: 'Postupy: Vytvoření čáry použitím LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 8db33fc5c611dcbcae50c71ada1c6b6f9fd9bd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Postupy: Vytvoření čáry použitím LineGeometry
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LineGeometry> třída k popisu řádku. A <xref:System.Windows.Media.LineGeometry> je definován jeho počáteční a koncové body.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> element slouží k vykreslení řádku.  Vzhledem k tomu, že má řádek žádné oblasti <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> není zadán; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti se používají.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![Objekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Objekt LineGeometry čerpají z (10,20) na (100,130)  
  
 Třídy dalších jednoduchý geometrie zahrnují <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>. Tyto geometrie, jakož i složitější těch, můžete také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>. Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Vytvoření složeného tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Vytvoření tvaru pomocí PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
