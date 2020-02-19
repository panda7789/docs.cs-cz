---
title: 'Postupy: Vytvoření kvadratické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452068"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="5619a-102">Postupy: Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="5619a-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="5619a-103">Tento příklad ukazuje, jak vytvořit kvadratickou Bézierovu křivku.</span><span class="sxs-lookup"><span data-stu-id="5619a-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="5619a-104">Chcete-li vytvořit kvadratickou Bézierovu křivku, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.QuadraticBezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="5619a-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5619a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5619a-105">Example</span></span>  
 <span data-ttu-id="5619a-106">V následujících příkladech je kvadratická Bézierova křivka vykreslena z (10 100) do (300 100).</span><span class="sxs-lookup"><span data-stu-id="5619a-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="5619a-107">Křivka má řídicí bod (200 200).</span><span class="sxs-lookup"><span data-stu-id="5619a-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="5619a-108">formátu</span><span class="sxs-lookup"><span data-stu-id="5619a-108">[xaml]</span></span>  
  
 <span data-ttu-id="5619a-109">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete použít syntaxi atributu k popisu cesty.</span><span class="sxs-lookup"><span data-stu-id="5619a-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="5619a-110">formátu</span><span class="sxs-lookup"><span data-stu-id="5619a-110">[xaml]</span></span>  
  
 <span data-ttu-id="5619a-111">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, což je verze <xref:System.Windows.Media.PathGeometry>s světlejší váhou.</span><span class="sxs-lookup"><span data-stu-id="5619a-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="5619a-112">Další informace naleznete na stránce [syntaxe označení cesty](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="5619a-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="5619a-113">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze také nakreslit kvadratickou Bézierovu křivku pomocí syntaxe elementů objektu.</span><span class="sxs-lookup"><span data-stu-id="5619a-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="5619a-114">Následující příklad je ekvivalentní k předchozímu příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5619a-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="5619a-115">Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="5619a-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5619a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5619a-116">See also</span></span>

- [<span data-ttu-id="5619a-117">Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="5619a-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="5619a-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="5619a-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
