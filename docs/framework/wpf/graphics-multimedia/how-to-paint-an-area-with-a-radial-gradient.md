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
ms.openlocfilehash: 75c28cd19ec0423589b6485884842468b89b5e8c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526788"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="7a822-102">Postupy: Vykreslení oblasti radiálním přechodem</span><span class="sxs-lookup"><span data-stu-id="7a822-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="7a822-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídu pro vykreslení oblasti radiálním přechodem.</span><span class="sxs-lookup"><span data-stu-id="7a822-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a822-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a822-104">Example</span></span>  
 <span data-ttu-id="7a822-105">Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskového přechodu, který změní z žlutá červená na modrou k Limetkově zelená.</span><span class="sxs-lookup"><span data-stu-id="7a822-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="7a822-106">Následující obrázek znázorňuje přechodu z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="7a822-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="7a822-107">Zdůraznily zastaví přechodu.</span><span class="sxs-lookup"><span data-stu-id="7a822-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="7a822-108">![Přechodové zarážky v paprskového přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="7a822-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a822-109">Příklady v tomto tématu použijte výchozí souřadnicový systém pro stanovení kontrolních bodů.</span><span class="sxs-lookup"><span data-stu-id="7a822-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="7a822-110">Souřadnicový systém výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="7a822-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="7a822-111">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="7a822-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="7a822-112">Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="7a822-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="7a822-113">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="7a822-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="7a822-114">Pro další <xref:System.Windows.Media.RadialGradientBrush> příkladů, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="7a822-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="7a822-115">Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a822-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
