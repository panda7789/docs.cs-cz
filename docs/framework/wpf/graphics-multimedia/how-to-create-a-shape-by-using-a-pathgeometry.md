---
title: "Postupy: Vytvoření tvaru použitím PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31f77f0921bb018317834077f70e4623c47a4f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="f5332-102">Postupy: Vytvoření tvaru použitím PathGeometry</span><span class="sxs-lookup"><span data-stu-id="f5332-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="f5332-103">Tento příklad ukazuje, jak vytvořit obrazce pomocí <xref:System.Windows.Media.PathGeometry> třídy.</span><span class="sxs-lookup"><span data-stu-id="f5332-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="f5332-104"><xref:System.Windows.Media.PathGeometry>objekty, které se skládají z jedné nebo více <xref:System.Windows.Media.PathFigure> objekty; každá <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="f5332-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="f5332-105">Každý <xref:System.Windows.Media.PathFigure> se sám skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představuje připojené část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="f5332-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="f5332-106">Segment typy <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, a <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="f5332-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5332-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5332-107">Example</span></span>  
 <span data-ttu-id="f5332-108">Následující příklad používá <xref:System.Windows.Media.PathGeometry> vytvořit trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="f5332-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="f5332-109"><xref:System.Windows.Media.PathGeometry> Se zobrazí pomocí <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="f5332-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="f5332-110">Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f5332-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="f5332-111">![Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="f5332-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="f5332-112">Trojúhelník vytvořené pomocí Objekt PathGeometry</span><span class="sxs-lookup"><span data-stu-id="f5332-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="f5332-113">Předchozí příklad ukázal, jak vytvořit poměrně jednoduché obrazce trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="f5332-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="f5332-114">A <xref:System.Windows.Media.PathGeometry> lze také použít k vytvoření složitějších tvarů, včetně oblouky a křivek.</span><span class="sxs-lookup"><span data-stu-id="f5332-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="f5332-115">Příklady najdete v tématu [vytvořit eliptické oblouk](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [vytvořit krychlový Bézierovu křivku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), a [vytvořit kvadratické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="f5332-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="f5332-116">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="f5332-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5332-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5332-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="f5332-118">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="f5332-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="f5332-119">Ukázka geometrie</span><span class="sxs-lookup"><span data-stu-id="f5332-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)
