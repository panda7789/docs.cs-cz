---
title: 'Postupy: Vytvoření tvaru použitím PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452042"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="95827-102">Postupy: Vytvoření tvaru použitím PathGeometry</span><span class="sxs-lookup"><span data-stu-id="95827-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="95827-103">Tento příklad ukazuje, jak vytvořit obrazec pomocí třídy <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="95827-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="95827-104"><xref:System.Windows.Media.PathGeometry> objekty se skládají z jednoho nebo více objektů <xref:System.Windows.Media.PathFigure>; Každý <xref:System.Windows.Media.PathFigure> představuje jiný obrázek nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="95827-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="95827-105">Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="95827-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="95827-106">Typy segmentů zahrnují <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>a <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="95827-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95827-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="95827-107">Example</span></span>  
 <span data-ttu-id="95827-108">Následující příklad používá <xref:System.Windows.Media.PathGeometry> k vytvoření trojúhelníku.</span><span class="sxs-lookup"><span data-stu-id="95827-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="95827-109"><xref:System.Windows.Media.PathGeometry> se zobrazí pomocí elementu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="95827-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="95827-110">Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="95827-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="95827-111">![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="95827-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="95827-112">Trojúhelník vytvořený s PathGeometry</span><span class="sxs-lookup"><span data-stu-id="95827-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="95827-113">Předchozí příklad ukázal, jak vytvořit relativně jednoduchý tvar, trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="95827-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="95827-114"><xref:System.Windows.Media.PathGeometry> lze také použít k vytvoření složitějších tvarů, včetně elips a křivek.</span><span class="sxs-lookup"><span data-stu-id="95827-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="95827-115">Příklady naleznete v tématu [Vytvoření eliptického oblouku](how-to-create-an-elliptical-arc.md), [Vytvoření Bézierovy křivky krychle](how-to-create-a-cubic-bezier-curve.md)a [Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="95827-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="95827-116">Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="95827-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95827-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="95827-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="95827-118">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="95827-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="95827-119">Ukázka geometrií</span><span class="sxs-lookup"><span data-stu-id="95827-119">Geometries Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
