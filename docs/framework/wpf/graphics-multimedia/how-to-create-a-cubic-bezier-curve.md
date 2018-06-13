---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 6332129179e1934e5a37c7a1a40ef5f46ab669a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560101"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="62ef7-102">Postupy: Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="62ef7-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="62ef7-103">Tento příklad ukazuje postup vytvoření krychlový Bézierovu křivku.</span><span class="sxs-lookup"><span data-stu-id="62ef7-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="62ef7-104">Chcete-li vytvořit krychlový Bézierovu křivku, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.BezierSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="62ef7-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="62ef7-105">Chcete-li zobrazit výsledné geometry, použijte <xref:System.Windows.Shapes.Path> element, nebo použít je s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="62ef7-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="62ef7-106">V následujících příkladech se nevykreslí krychlový Bézierovu křivku z (10, 100) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="62ef7-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="62ef7-107">Křivku má ovládací prvek body (100, 0) a (200, 200).</span><span class="sxs-lookup"><span data-stu-id="62ef7-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62ef7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="62ef7-108">Example</span></span>  
 <span data-ttu-id="62ef7-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="62ef7-109">[xaml]</span></span>  
  
 <span data-ttu-id="62ef7-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít syntaxi zkrácené značek k popisu cestu.</span><span class="sxs-lookup"><span data-stu-id="62ef7-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="62ef7-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="62ef7-111">[xaml]</span></span>  
  
 <span data-ttu-id="62ef7-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit krychlový Bézierovu křivku pomocí značek object.</span><span class="sxs-lookup"><span data-stu-id="62ef7-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="62ef7-113">Tady je ekvivalentem předchozího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.</span><span class="sxs-lookup"><span data-stu-id="62ef7-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="62ef7-114">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="62ef7-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ef7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="62ef7-115">See Also</span></span>  
 [<span data-ttu-id="62ef7-116">Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="62ef7-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="62ef7-117">Vytvoření LineSegment v PathGeometry</span><span class="sxs-lookup"><span data-stu-id="62ef7-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [<span data-ttu-id="62ef7-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="62ef7-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [<span data-ttu-id="62ef7-119">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="62ef7-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
