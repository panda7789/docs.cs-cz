---
title: 'Postupy: Vyplnění oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452763"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="4b296-102">Postupy: Vyplnění oblasti lineárním přechodem</span><span class="sxs-lookup"><span data-stu-id="4b296-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="4b296-103">Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.LinearGradientBrush> k vykreslení oblasti lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="4b296-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="4b296-104">V následujícím příkladu je <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> vykreslen s úhlopříčným lineárním přechodem, který přechází ze žluté na červenou na modrou zelenou.</span><span class="sxs-lookup"><span data-stu-id="4b296-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b296-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b296-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="4b296-106">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="4b296-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b296-107">![Diagonální lineární přechod](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b296-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="4b296-108">Chcete-li vytvořit horizontální lineární přechod, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> na (0, 0,5) a (1, 0,5).</span><span class="sxs-lookup"><span data-stu-id="4b296-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="4b296-109">V následujícím příkladu je <xref:System.Windows.Shapes.Rectangle> vykreslen s vodorovným lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="4b296-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="4b296-110">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="4b296-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b296-111">![Vodorovný lineární přechod](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b296-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="4b296-112">Chcete-li vytvořit svislý lineární přechod, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> na (0,5, 0) a (0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="4b296-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="4b296-113">V následujícím příkladu je <xref:System.Windows.Shapes.Rectangle> vykreslen se svislým lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="4b296-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="4b296-114">Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="4b296-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b296-115">![Svislý lineární přechod](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b296-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b296-116">Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení počátečních bodů a koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4b296-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="4b296-117">Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 označuje 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="4b296-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="4b296-118">Tento systém souřadnic můžete změnit nastavením vlastnosti <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b296-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4b296-119">Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli.</span><span class="sxs-lookup"><span data-stu-id="4b296-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="4b296-120">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="4b296-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="4b296-121">Další příklady naleznete v tématu [Ukázka štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="4b296-121">For additional examples, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="4b296-122">Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4b296-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
