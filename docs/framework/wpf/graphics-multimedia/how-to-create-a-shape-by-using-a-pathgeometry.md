---
title: 'Postupy: Vytvoření tvaru pomocí PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: b0ab703596612524881ab892a1095b0f49cd1551
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159312"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="bb0bd-102">Postupy: Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="bb0bd-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="bb0bd-103">Tento příklad ukazuje postup vytvoření tvaru použitím <xref:System.Windows.Media.PathGeometry> třídy.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="bb0bd-104"><xref:System.Windows.Media.PathGeometry> objekty se skládají z nejméně jednu <xref:System.Windows.Media.PathFigure> objektů; každý <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="bb0bd-105">Každý <xref:System.Windows.Media.PathFigure> samotný tvoří jeden nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představující připojených část obrázku nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="bb0bd-106">Segment typy zahrnují <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, a <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb0bd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb0bd-107">Example</span></span>  
 <span data-ttu-id="bb0bd-108">Následující příklad používá <xref:System.Windows.Media.PathGeometry> vytvořit trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="bb0bd-109"><xref:System.Windows.Media.PathGeometry> Se zobrazí pomocí <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="bb0bd-110">Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="bb0bd-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="bb0bd-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="bb0bd-112">Trojúhelník vytvořené pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="bb0bd-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="bb0bd-113">Předchozí příklad ukázal, jak vytvořit obrazec poměrně jednoduchý trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="bb0bd-114">A <xref:System.Windows.Media.PathGeometry> slouží také k vytvoření složitějších tvary, včetně oblouky křivky.</span><span class="sxs-lookup"><span data-stu-id="bb0bd-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="bb0bd-115">Příklady najdete v tématu [vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md), [vytvoření Kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md), a [vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="bb0bd-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="bb0bd-116">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="bb0bd-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0bd-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb0bd-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="bb0bd-118">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="bb0bd-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="bb0bd-119">Ukázka geometrie</span><span class="sxs-lookup"><span data-stu-id="bb0bd-119">Geometries Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159989)
