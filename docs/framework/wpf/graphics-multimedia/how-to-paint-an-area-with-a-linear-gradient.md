---
title: 'Postupy: Vyplnění oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367242"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="aef49-102">Postupy: Vyplnění oblasti lineárním přechodem</span><span class="sxs-lookup"><span data-stu-id="aef49-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="aef49-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LinearGradientBrush> třídu pro vykreslení oblasti lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="aef49-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="aef49-104">V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> vymalováním Úhlopříčný lineárním přechodem, který změní z žlutá červená na modrou k Limetkově zelená.</span><span class="sxs-lookup"><span data-stu-id="aef49-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aef49-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aef49-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="aef49-106">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aef49-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="aef49-107">![Úhlopříčný lineárního přechodu](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="aef49-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="aef49-108">Chcete-li vytvořit horizontální lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0,0.5) a (1,0.5).</span><span class="sxs-lookup"><span data-stu-id="aef49-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="aef49-109">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s vodorovné lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="aef49-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="aef49-110">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aef49-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="aef49-111">![Vodorovné lineárního přechodu](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="aef49-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="aef49-112">Chcete-li vytvořit svislé lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0.5,0) a (0.5,1).</span><span class="sxs-lookup"><span data-stu-id="aef49-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="aef49-113">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s svislé lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="aef49-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="aef49-114">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aef49-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="aef49-115">![Svislé lineárního přechodu](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="aef49-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aef49-116">Příklady v tomto tématu použijte výchozí souřadnicový systém pro nastavení bodů počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="aef49-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="aef49-117">Systém souřadnic výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="aef49-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="aef49-118">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aef49-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aef49-119">Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="aef49-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="aef49-120">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="aef49-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="aef49-121">Další příklady najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="aef49-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="aef49-122">Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aef49-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
