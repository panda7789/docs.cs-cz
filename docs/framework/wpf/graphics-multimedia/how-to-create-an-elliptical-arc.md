---
title: 'Postupy: Vytvoření oblouku elipsy'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 7ca7d06aa25f8dfae648d8c54c8b95cc277ffbf9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393832"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="852c3-102">Postupy: Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="852c3-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="852c3-103">Tento příklad ukazuje, jak nakreslit oblouk elipsy. K vytvoření oblouku elipsy, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.ArcSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="852c3-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="852c3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="852c3-104">Example</span></span>  
 <span data-ttu-id="852c3-105">V následujících příkladech oblouku elipsy linie z (10,100) (200,100).</span><span class="sxs-lookup"><span data-stu-id="852c3-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="852c3-106">Oblouk <xref:System.Windows.Media.ArcSegment.Size%2A> 100 podle 50 v pixelech nezávislých na zařízení, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stupňů, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> nastavení `true`a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="852c3-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="852c3-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="852c3-107">[xaml]</span></span>  
  
 <span data-ttu-id="852c3-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], syntaxe atributů lze použít k popisu cesty.</span><span class="sxs-lookup"><span data-stu-id="852c3-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="852c3-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="852c3-109">[xaml]</span></span>  
  
 <span data-ttu-id="852c3-110">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="852c3-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="852c3-111">Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="852c3-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="852c3-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit oblouku elipsy explicitně pomocí značky object.</span><span class="sxs-lookup"><span data-stu-id="852c3-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="852c3-113">Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="852c3-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="852c3-114">V tomto příkladu je součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="852c3-114">This example is part of a larger sample.</span></span> <span data-ttu-id="852c3-115">Úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="852c3-115">For the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852c3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="852c3-116">See Also</span></span>  
 [<span data-ttu-id="852c3-117">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="852c3-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="852c3-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="852c3-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
