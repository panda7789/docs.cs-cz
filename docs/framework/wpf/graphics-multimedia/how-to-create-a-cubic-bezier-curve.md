---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 36544abc774b7fe82c2ff47483cfedd6fb13e344
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115567"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="b3a52-102">Postupy: Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="b3a52-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="b3a52-103">Tento příklad ukazuje postup vytvoření kubické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="b3a52-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="b3a52-104">K vytvoření kubické Bézierovy křivky, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.BezierSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="b3a52-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="b3a52-105">Chcete-li zobrazit výsledné geometrie, použijte <xref:System.Windows.Shapes.Path> element, nebo použít je s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="b3a52-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="b3a52-106">V následujících příkladech kubické Bézierovy křivky přenesou z (10, 100) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="b3a52-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="b3a52-107">Křivka má ovládací prvek body (100, 0) a (200, 200).</span><span class="sxs-lookup"><span data-stu-id="b3a52-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3a52-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3a52-108">Example</span></span>  
 <span data-ttu-id="b3a52-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="b3a52-109">[xaml]</span></span>  
  
 <span data-ttu-id="b3a52-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít k popisu cesty syntaxe zkrácený značek.</span><span class="sxs-lookup"><span data-stu-id="b3a52-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="b3a52-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="b3a52-111">[xaml]</span></span>  
  
 <span data-ttu-id="b3a52-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit kubické Bézierovy křivky pomocí značky object.</span><span class="sxs-lookup"><span data-stu-id="b3a52-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="b3a52-113">Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.</span><span class="sxs-lookup"><span data-stu-id="b3a52-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="b3a52-114">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="b3a52-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a52-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3a52-115">See also</span></span>

- [<span data-ttu-id="b3a52-116">Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="b3a52-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="b3a52-117">Vytvoření LineSegment v PathGeometry</span><span class="sxs-lookup"><span data-stu-id="b3a52-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="b3a52-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="b3a52-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="b3a52-119">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="b3a52-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
