---
title: 'Postupy: Vykreslení oblasti paprskovým přechodem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916101"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="1600e-102">Postupy: Vykreslení oblasti paprskovým přechodem</span><span class="sxs-lookup"><span data-stu-id="1600e-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="1600e-103">Tento příklad ukazuje, jak použít <xref:System.Windows.Media.RadialGradientBrush> třídu k vykreslení oblasti paprskovým přechodem.</span><span class="sxs-lookup"><span data-stu-id="1600e-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1600e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1600e-104">Example</span></span>  
 <span data-ttu-id="1600e-105">Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskovým přechodem, který přechází ze žluté na červenou na modrou zelenou.</span><span class="sxs-lookup"><span data-stu-id="1600e-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="1600e-106">Následující ilustrace znázorňuje přechod z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="1600e-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="1600e-107">Byla zvýrazněna zastávka přechodu.</span><span class="sxs-lookup"><span data-stu-id="1600e-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="1600e-108">![Přechodové zarážky v paprskovém přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="1600e-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1600e-109">Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení řídicích bodů.</span><span class="sxs-lookup"><span data-stu-id="1600e-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="1600e-110">Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 značí 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="1600e-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="1600e-111">Můžete změnit tento systém souřadnic nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnosti na hodnotu. <xref:System.Windows.Media.BrushMappingMode.Absolute></span><span class="sxs-lookup"><span data-stu-id="1600e-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="1600e-112">Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli.</span><span class="sxs-lookup"><span data-stu-id="1600e-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="1600e-113">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="1600e-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="1600e-114">Další <xref:System.Windows.Media.RadialGradientBrush> příklady naleznete v [ukázce štětce](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="1600e-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="1600e-115">Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1600e-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
