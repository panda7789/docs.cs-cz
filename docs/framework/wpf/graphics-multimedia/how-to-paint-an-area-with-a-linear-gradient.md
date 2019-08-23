---
title: 'Postupy: Vykreslení oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916167"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="0acac-102">Postupy: Vykreslení oblasti lineárním přechodem</span><span class="sxs-lookup"><span data-stu-id="0acac-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="0acac-103">Tento příklad ukazuje, jak použít <xref:System.Windows.Media.LinearGradientBrush> třídu k vykreslení oblasti lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="0acac-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="0acac-104">V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> je vykreslen s úhlopříčným lineárním přechodem, který přechází ze žluté na červenou na modrou zelenou.</span><span class="sxs-lookup"><span data-stu-id="0acac-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0acac-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0acac-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="0acac-106">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="0acac-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0acac-107">![Diagonální lineární přechod](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="0acac-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="0acac-108">Chcete-li vytvořit vodorovný lineární přechod, <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> změňte <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush> na (0, 0,5) a (1, 0,5).</span><span class="sxs-lookup"><span data-stu-id="0acac-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="0acac-109">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> je vykreslen s vodorovným lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="0acac-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="0acac-110">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="0acac-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0acac-111">![Vodorovný lineární přechod](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="0acac-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="0acac-112">Chcete-li vytvořit svislý lineární přechod, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> hodnotu <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush> na (0.5, 0) a (0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="0acac-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="0acac-113">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> je vykreslen se svislým lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="0acac-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="0acac-114">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="0acac-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0acac-115">![Svislý lineární přechod](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="0acac-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0acac-116">Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení počátečních bodů a koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="0acac-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="0acac-117">Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 značí 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="0acac-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="0acac-118">Můžete změnit tento systém souřadnic nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnosti na hodnotu. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0acac-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0acac-119">Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli.</span><span class="sxs-lookup"><span data-stu-id="0acac-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="0acac-120">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="0acac-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="0acac-121">Další příklady naleznete v tématu [Ukázka štětce](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="0acac-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="0acac-122">Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0acac-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
