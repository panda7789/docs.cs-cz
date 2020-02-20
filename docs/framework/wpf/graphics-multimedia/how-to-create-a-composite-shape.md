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
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452094"
---
# <a name="how-to-create-a-composite-shape"></a>Postupy: Vytvoření složeného tvaru
Tento příklad ukazuje, jak vytvořit složené tvary pomocí <xref:System.Windows.Media.Geometry> objektů a zobrazit je pomocí <xref:System.Windows.Shapes.Path> elementu. V následujícím příkladu jsou použity <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>a <xref:System.Windows.Media.RectangleGeometry> se <xref:System.Windows.Media.GeometryGroup> k vytvoření složeného tvaru. Geometrií se pak vykreslí pomocí elementu <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Složená geometrie vytvořená pomocí geometrie](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Složená geometrie  
  
 Složitější tvary, jako jsou mnohoúhelníky a tvary se zakřivenými segmenty, se dají vytvořit pomocí <xref:System.Windows.Media.PathGeometry>. Příklad ukazující, jak vytvořit tvar pomocí <xref:System.Windows.Media.PathGeometry>, naleznete v tématu [Vytvoření obrazce pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  I když tento příklad vykresluje obrazec na obrazovku pomocí elementu <xref:System.Windows.Shapes.Path>, lze použít také <xref:System.Windows.Media.Geometry> objektů k popisu obsahu <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. Mohou být také použity pro testování a testování přístupů.  
  
 Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).
