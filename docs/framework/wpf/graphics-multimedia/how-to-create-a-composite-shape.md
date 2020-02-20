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
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="75928-102">Postupy: Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="75928-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="75928-103">Tento příklad ukazuje, jak vytvořit složené tvary pomocí <xref:System.Windows.Media.Geometry> objektů a zobrazit je pomocí <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="75928-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="75928-104">V následujícím příkladu jsou použity <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>a <xref:System.Windows.Media.RectangleGeometry> se <xref:System.Windows.Media.GeometryGroup> k vytvoření složeného tvaru.</span><span class="sxs-lookup"><span data-stu-id="75928-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="75928-105">Geometrií se pak vykreslí pomocí elementu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="75928-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75928-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="75928-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="75928-107">Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="75928-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="75928-108">![Složená geometrie vytvořená pomocí geometrie](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="75928-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="75928-109">Složená geometrie</span><span class="sxs-lookup"><span data-stu-id="75928-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="75928-110">Složitější tvary, jako jsou mnohoúhelníky a tvary se zakřivenými segmenty, se dají vytvořit pomocí <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="75928-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="75928-111">Příklad ukazující, jak vytvořit tvar pomocí <xref:System.Windows.Media.PathGeometry>, naleznete v tématu [Vytvoření obrazce pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="75928-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="75928-112">I když tento příklad vykresluje obrazec na obrazovku pomocí elementu <xref:System.Windows.Shapes.Path>, lze použít také <xref:System.Windows.Media.Geometry> objektů k popisu obsahu <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="75928-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="75928-113">Mohou být také použity pro testování a testování přístupů.</span><span class="sxs-lookup"><span data-stu-id="75928-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="75928-114">Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="75928-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>
