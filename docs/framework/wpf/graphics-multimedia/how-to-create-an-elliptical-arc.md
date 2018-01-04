---
title: "Postupy: Vytvoření oblouku elipsy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e11f3e0035c00bbc280b658c0931d57c37524f93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="114c6-102">Postupy: Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="114c6-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="114c6-103">Tento příklad ukazuje, jak k vykreslení eliptické oblouk. Chcete-li vytvořit eliptické oblouk, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.ArcSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="114c6-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="114c6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="114c6-104">Example</span></span>  
 <span data-ttu-id="114c6-105">V následujících příkladech je eliptické oblouk čerpají z (10,100) na (200,100).</span><span class="sxs-lookup"><span data-stu-id="114c6-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="114c6-106">Má oblouk <xref:System.Windows.Media.ArcSegment.Size%2A> 100 podle 50 pixelů nezávislé na zařízení, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stupňů, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> nastavení `true`a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="114c6-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="114c6-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="114c6-107">[xaml]</span></span>  
  
 <span data-ttu-id="114c6-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete pomocí syntaxe atribut popisující cestu.</span><span class="sxs-lookup"><span data-stu-id="114c6-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="114c6-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="114c6-109">[xaml]</span></span>  
  
 <span data-ttu-id="114c6-110">(Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="114c6-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="114c6-111">Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="114c6-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="114c6-112">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také nakreslit oblouk eliptické explicitně pomocí značek object.</span><span class="sxs-lookup"><span data-stu-id="114c6-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="114c6-113">Tady je ekvivalentní k předchozím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="114c6-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="114c6-114">Tato ukázka je součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="114c6-114">This example is part of a larger sample.</span></span> <span data-ttu-id="114c6-115">Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="114c6-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114c6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="114c6-116">See Also</span></span>  
 [<span data-ttu-id="114c6-117">Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="114c6-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="114c6-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="114c6-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
