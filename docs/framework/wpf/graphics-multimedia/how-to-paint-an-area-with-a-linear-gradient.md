---
title: 'Postupy: Vyplnění oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: aee9931fc366131ae492891cc4d0fff70b4a4441
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779994"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="d370a-102">Postupy: Vyplnění oblasti lineárním přechodem</span><span class="sxs-lookup"><span data-stu-id="d370a-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="d370a-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LinearGradientBrush> třídu pro vykreslení oblasti lineárním přechodem.</span><span class="sxs-lookup"><span data-stu-id="d370a-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="d370a-104">V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> vymalováním Úhlopříčný lineárním přechodem, který změní z žlutá červená na modrou k Limetkově zelená.</span><span class="sxs-lookup"><span data-stu-id="d370a-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d370a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d370a-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="d370a-106">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d370a-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="d370a-107">![Úhlopříčný lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="d370a-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="d370a-108">Chcete-li vytvořit horizontální lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0,0.5) a (1,0.5).</span><span class="sxs-lookup"><span data-stu-id="d370a-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="d370a-109">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s vodorovné lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="d370a-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="d370a-110">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d370a-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="d370a-111">![Vodorovné lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="d370a-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="d370a-112">Chcete-li vytvořit svislé lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0.5,0) a (0.5,1).</span><span class="sxs-lookup"><span data-stu-id="d370a-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="d370a-113">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s svislé lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="d370a-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="d370a-114">Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d370a-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="d370a-115">![Svislé lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="d370a-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d370a-116">Příklady v tomto tématu použijte výchozí souřadnicový systém pro nastavení bodů počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="d370a-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="d370a-117">Souřadnicový systém výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="d370a-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="d370a-118">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d370a-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d370a-119">Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="d370a-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="d370a-120">Hodnoty jsou interpretovány přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="d370a-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="d370a-121">Další příklady najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="d370a-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="d370a-122">Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d370a-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
