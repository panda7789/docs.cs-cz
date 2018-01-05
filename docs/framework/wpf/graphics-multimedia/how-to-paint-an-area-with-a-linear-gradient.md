---
title: "Postupy: Vyplnění oblasti lineárním přechodem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec4ec2fc7ba99081eaafa6803d20c99bebc6c2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="69ca3-102">Postupy: Vyplnění oblasti lineárním přechodem</span><span class="sxs-lookup"><span data-stu-id="69ca3-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="69ca3-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LinearGradientBrush> třídy Malování oblast s lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="69ca3-104">V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> vykreslením s diagonálních lineárního přechodu, která přejde z žlutý do červené na modrou k vápna zeleně.</span><span class="sxs-lookup"><span data-stu-id="69ca3-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69ca3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="69ca3-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="69ca3-106">Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="69ca3-107">![Diagonálních lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="69ca3-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="69ca3-108">Chcete-li vytvořit vodorovné lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0,0.5) a (1,0.5).</span><span class="sxs-lookup"><span data-stu-id="69ca3-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="69ca3-109">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vykreslením s vodorovné lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="69ca3-110">Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="69ca3-111">![Vodorovné lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="69ca3-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="69ca3-112">Chcete-li vytvořit svislé lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0.5,0) a (0.5,1).</span><span class="sxs-lookup"><span data-stu-id="69ca3-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="69ca3-113">V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vykreslením s svislé lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="69ca3-114">Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69ca3-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="69ca3-115">![Svislé lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="69ca3-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69ca3-116">V příkladech v tomto tématu použijte výchozí souřadnicový systém pro nastavení body počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="69ca3-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="69ca3-117">Systém souřadnic výchozí je relativní vzhledem ke ohraničující pole: 0 znamená 0 procent ohraničujícího rámečku a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="69ca3-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="69ca3-118">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnost na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69ca3-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69ca3-119">Absolutní souřadnicový systém není relativně k ohraničující pole.</span><span class="sxs-lookup"><span data-stu-id="69ca3-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="69ca3-120">Hodnoty se interpretují přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="69ca3-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="69ca3-121">Další příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="69ca3-121">For additional examples, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="69ca3-122">Další informace o přechody a dalších typů štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="69ca3-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
