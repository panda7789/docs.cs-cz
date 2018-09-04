---
title: 'Postupy: Vytvoření složeného tvaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: 9892120d13a067586dbf6472a6873b6a52c2d8b4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515161"
---
# <a name="how-to-create-a-composite-shape"></a>Postupy: Vytvoření složeného tvaru
Tento příklad ukazuje, jak vytvořit složené obrazce pomocí <xref:System.Windows.Media.Geometry> objektů a jejich zobrazení pomocí <xref:System.Windows.Shapes.Path> elementu. V následujícím příkladu <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>a <xref:System.Windows.Media.RectangleGeometry> produkty slouží spolu s <xref:System.Windows.Media.GeometryGroup> vytvoření složeného tvaru. Geometrie jsou pak vykreslen <xref:System.Windows.Shapes.Path> elementu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Složený geometrie vytvořené pomocí GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Složený geometrie  
  
 Složitější obrazce, jako je například mnohoúhelníků a obrazců pomocí zakřivené segmenty, mohou být vytvořeny pomocí <xref:System.Windows.Media.PathGeometry>. Příklad ukazuje, jak vytvořit pomocí tvaru <xref:System.Windows.Media.PathGeometry>, naleznete v tématu [vytvoření tvaru použitím PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  I když v tomto příkladu vykreslí tvar na obrazovce pomocí <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> objekty také lze popsat její obsah <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. Může se také využít k oříznutí a spuštění testu.  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).
