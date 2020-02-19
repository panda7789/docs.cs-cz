---
title: 'Postupy: Vykreslení oblasti radiálním přechodem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452750"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="72898-102">Postupy: Vykreslení oblasti radiálním přechodem</span><span class="sxs-lookup"><span data-stu-id="72898-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="72898-103">Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.RadialGradientBrush> k vykreslení oblasti s paprskovým přechodem.</span><span class="sxs-lookup"><span data-stu-id="72898-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72898-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="72898-104">Example</span></span>  
 <span data-ttu-id="72898-105">Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskovým přechodem, který přechází ze žluté na červenou na modrou zelenou.</span><span class="sxs-lookup"><span data-stu-id="72898-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="72898-106">Následující ilustrace znázorňuje přechod z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="72898-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="72898-107">Byla zvýrazněna zastávka přechodu.</span><span class="sxs-lookup"><span data-stu-id="72898-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="72898-108">![Přechodové zarážky v paprskovém přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="72898-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72898-109">Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení řídicích bodů.</span><span class="sxs-lookup"><span data-stu-id="72898-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="72898-110">Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 označuje 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="72898-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="72898-111">Tento systém souřadnic můžete změnit nastavením vlastnosti <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="72898-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="72898-112">Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli.</span><span class="sxs-lookup"><span data-stu-id="72898-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="72898-113">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="72898-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="72898-114">Další příklady <xref:System.Windows.Media.RadialGradientBrush> naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="72898-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="72898-115">Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="72898-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
