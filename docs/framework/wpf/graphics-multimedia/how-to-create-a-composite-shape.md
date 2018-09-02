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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43457080"
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="b25a9-102">Postupy: Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="b25a9-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="b25a9-103">Tento příklad ukazuje, jak vytvořit složené obrazce pomocí <xref:System.Windows.Media.Geometry> objektů a jejich zobrazení pomocí <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="b25a9-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="b25a9-104">V následujícím příkladu <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>a <xref:System.Windows.Media.RectangleGeometry> produkty slouží spolu s <xref:System.Windows.Media.GeometryGroup> vytvoření složeného tvaru.</span><span class="sxs-lookup"><span data-stu-id="b25a9-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="b25a9-105">Geometrie jsou pak vykreslen <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="b25a9-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b25a9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b25a9-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="b25a9-107">Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b25a9-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="b25a9-108">![Složený geometrie vytvořené pomocí GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="b25a9-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="b25a9-109">Složený geometrie</span><span class="sxs-lookup"><span data-stu-id="b25a9-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="b25a9-110">Složitější obrazce, jako je například mnohoúhelníků a obrazců pomocí zakřivené segmenty, mohou být vytvořeny pomocí <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="b25a9-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="b25a9-111">Příklad ukazuje, jak vytvořit pomocí tvaru <xref:System.Windows.Media.PathGeometry>, naleznete v tématu [vytvoření tvaru použitím PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="b25a9-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="b25a9-112">I když v tomto příkladu vykreslí tvar na obrazovce pomocí <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> objekty také lze popsat její obsah <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="b25a9-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="b25a9-113">Může se také využít k oříznutí a spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="b25a9-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="b25a9-114">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="b25a9-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
