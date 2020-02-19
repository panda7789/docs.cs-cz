---
title: 'Postupy: Vytvoření kubické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452107"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="25510-102">Postupy: Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="25510-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="25510-103">Tento příklad ukazuje, jak vytvořit Bézierovu křivku krychle.</span><span class="sxs-lookup"><span data-stu-id="25510-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="25510-104">Chcete-li vytvořit Bézierovu křivku krychle, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="25510-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="25510-105">Chcete-li zobrazit výslednou geometrii, použijte prvek <xref:System.Windows.Shapes.Path> nebo jej použijte s <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="25510-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="25510-106">V následujících příkladech je vykreslená křivka krychle z (10, 100) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="25510-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="25510-107">Křivka má kontrolní body (100, 0) a (200, 200).</span><span class="sxs-lookup"><span data-stu-id="25510-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25510-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="25510-108">Example</span></span>  
 <span data-ttu-id="25510-109">formátu</span><span class="sxs-lookup"><span data-stu-id="25510-109">[xaml]</span></span>  
  
 <span data-ttu-id="25510-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete k popisu cesty použít syntaxi zkráceného označení.</span><span class="sxs-lookup"><span data-stu-id="25510-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="25510-111">formátu</span><span class="sxs-lookup"><span data-stu-id="25510-111">[xaml]</span></span>  
  
 <span data-ttu-id="25510-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze také kreslit krychlovou Bézierovu křivku pomocí značek objektů.</span><span class="sxs-lookup"><span data-stu-id="25510-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="25510-113">Následující příklad je ekvivalentní k předchozímu příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25510-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="25510-114">Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="25510-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25510-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="25510-115">See also</span></span>

- [<span data-ttu-id="25510-116">Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="25510-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="25510-117">Vytvoření LineSegment v PathGeometry</span><span class="sxs-lookup"><span data-stu-id="25510-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="25510-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="25510-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="25510-119">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="25510-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
