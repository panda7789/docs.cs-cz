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
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921824"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="63c27-102">Postupy: Vykreslení oblasti paprskovým přechodem</span><span class="sxs-lookup"><span data-stu-id="63c27-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="63c27-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídu pro vykreslení oblasti radiálním přechodem.</span><span class="sxs-lookup"><span data-stu-id="63c27-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c27-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="63c27-104">Example</span></span>  
 <span data-ttu-id="63c27-105">Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskového přechodu, který změní z žlutá červená na modrou k Limetkově zelená.</span><span class="sxs-lookup"><span data-stu-id="63c27-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="63c27-106">Následující obrázek znázorňuje přechodu z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="63c27-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="63c27-107">Zdůraznily zastaví přechodu.</span><span class="sxs-lookup"><span data-stu-id="63c27-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="63c27-108">![Přechodové zarážky v paprskového přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="63c27-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63c27-109">Příklady v tomto tématu použijte výchozí souřadnicový systém pro stanovení kontrolních bodů.</span><span class="sxs-lookup"><span data-stu-id="63c27-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="63c27-110">Systém souřadnic výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="63c27-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="63c27-111">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="63c27-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="63c27-112">Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="63c27-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="63c27-113">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="63c27-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="63c27-114">Pro další <xref:System.Windows.Media.RadialGradientBrush> příkladů, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="63c27-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="63c27-115">Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63c27-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
