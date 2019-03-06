---
title: 'Postupy: Postupy: Vytvoření oblouku elipsy'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: bb4b4d99aab9daef70f446af176bb462b0661d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354346"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="18c25-102">Postupy: Postupy: Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="18c25-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="18c25-103">Tento příklad ukazuje, jak nakreslit oblouk elipsy. K vytvoření oblouku elipsy, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.ArcSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="18c25-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c25-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="18c25-104">Example</span></span>  
 <span data-ttu-id="18c25-105">V následujících příkladech oblouku elipsy linie z (10,100) (200,100).</span><span class="sxs-lookup"><span data-stu-id="18c25-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="18c25-106">Oblouk <xref:System.Windows.Media.ArcSegment.Size%2A> 100 podle 50 v pixelech nezávislých na zařízení, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stupňů, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> nastavení `true`a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="18c25-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="18c25-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="18c25-107">[xaml]</span></span>  
  
 <span data-ttu-id="18c25-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], syntaxe atributů lze použít k popisu cesty.</span><span class="sxs-lookup"><span data-stu-id="18c25-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="18c25-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="18c25-109">[xaml]</span></span>  
  
 <span data-ttu-id="18c25-110">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="18c25-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="18c25-111">Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="18c25-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="18c25-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit oblouku elipsy explicitně pomocí značky object.</span><span class="sxs-lookup"><span data-stu-id="18c25-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="18c25-113">Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="18c25-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="18c25-114">V tomto příkladu je součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="18c25-114">This example is part of a larger sample.</span></span> <span data-ttu-id="18c25-115">Úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="18c25-115">For the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c25-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18c25-116">See also</span></span>
- [<span data-ttu-id="18c25-117">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="18c25-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="18c25-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="18c25-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
