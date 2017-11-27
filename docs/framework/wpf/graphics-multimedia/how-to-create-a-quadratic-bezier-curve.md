---
title: "Postupy: Vytvoření kvadratické Bézierovy křivky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8320889f931e4482091b15bd9295c77a36d6d1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="4d902-102">Postupy: Vytvoření kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="4d902-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="4d902-103">Tento příklad ukazuje postup vytvoření kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="4d902-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="4d902-104">Chcete-li vytvořit kvadratické Bézierovy křivky, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.QuadraticBezierSegment> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d902-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d902-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d902-105">Example</span></span>  
 <span data-ttu-id="4d902-106">V následujících příkladech je kvadratické Bézierovy křivky čerpají z (10,100) na (300,100).</span><span class="sxs-lookup"><span data-stu-id="4d902-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="4d902-107">Křivku má řídicí bod (200,200).</span><span class="sxs-lookup"><span data-stu-id="4d902-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="4d902-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="4d902-108">[xaml]</span></span>  
  
 <span data-ttu-id="4d902-109">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete pomocí syntaxe atribut popisující cestu.</span><span class="sxs-lookup"><span data-stu-id="4d902-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="4d902-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="4d902-110">[xaml]</span></span>  
  
 <span data-ttu-id="4d902-111">(Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4d902-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4d902-112">Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="4d902-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="4d902-113">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], může také kreslení kvadratické Bézierovy křivky pomocí syntaxe element objektu.</span><span class="sxs-lookup"><span data-stu-id="4d902-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="4d902-114">Tady je ekvivalentem předchozího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.</span><span class="sxs-lookup"><span data-stu-id="4d902-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="4d902-115">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="4d902-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d902-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d902-116">See Also</span></span>  
 [<span data-ttu-id="4d902-117">Vytvoření eliptické oblouk</span><span class="sxs-lookup"><span data-stu-id="4d902-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="4d902-118">Vytvoření krychlový Bézierovu křivku</span><span class="sxs-lookup"><span data-stu-id="4d902-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
