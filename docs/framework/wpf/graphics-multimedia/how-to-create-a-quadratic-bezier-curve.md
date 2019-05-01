---
title: 'Postupy: Vytvoření kvadratické Bézierovy křivky'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a0b2145b4a5bba11186419fe680f2eca41949d6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054559"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="a4c49-102">Postupy: Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="a4c49-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="a4c49-103">Tento příklad ukazuje postup vytvoření kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="a4c49-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="a4c49-104">K vytvoření kvadratické Bézierovy křivky, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.QuadraticBezierSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="a4c49-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4c49-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4c49-105">Example</span></span>  
 <span data-ttu-id="a4c49-106">V následujících příkladech kvadratické Bézierovy křivky linie z (10,100) (300,100).</span><span class="sxs-lookup"><span data-stu-id="a4c49-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="a4c49-107">Křivka má řídicí bod (200,200).</span><span class="sxs-lookup"><span data-stu-id="a4c49-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="a4c49-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a4c49-108">[xaml]</span></span>  
  
 <span data-ttu-id="a4c49-109">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], syntaxe atributů lze použít k popisu cesty.</span><span class="sxs-lookup"><span data-stu-id="a4c49-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="a4c49-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a4c49-110">[xaml]</span></span>  
  
 <span data-ttu-id="a4c49-111">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a4c49-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a4c49-112">Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="a4c49-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="a4c49-113">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], mohou také nakreslit kvadratické Bézierovy křivky použití syntaxe elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="a4c49-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="a4c49-114">Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.</span><span class="sxs-lookup"><span data-stu-id="a4c49-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="a4c49-115">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="a4c49-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c49-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4c49-116">See also</span></span>

- [<span data-ttu-id="a4c49-117">Vytvoření oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="a4c49-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="a4c49-118">Vytvoření kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="a4c49-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
