---
title: 'Postupy: Animace vlastnosti bez pomoci scénáře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 18f8fb4edf5f71904335180e43dd65bd9910bdef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561011"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="40d4c-102">Postupy: Animace vlastnosti bez pomoci scénáře</span><span class="sxs-lookup"><span data-stu-id="40d4c-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="40d4c-103">Tento příklad ukazuje jeden ze způsobů použití animace do vlastnosti bez použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="40d4c-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40d4c-104">Tato funkce není k dispozici v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40d4c-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="40d4c-105">Informace o animaci na vlastnost ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="40d4c-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="40d4c-106">Chcete-li použít místní animace do vlastnosti, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="40d4c-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="40d4c-107">Tato metoda přebírá dva parametry: <xref:System.Windows.DependencyProperty> určující vlastností pro animaci a animace chcete použít pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="40d4c-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d4c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="40d4c-108">Example</span></span>  
 <span data-ttu-id="40d4c-109">Následující příklad ukazuje, jak animace barva šířky a pozadí <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="40d4c-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="40d4c-110">Různé třídy animace v <xref:System.Windows.Media.Animation> obor názvů existuje pro různé typy vlastností animace.</span><span class="sxs-lookup"><span data-stu-id="40d4c-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="40d4c-111">Další informace o animaci vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40d4c-111">For more information about animating properties, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="40d4c-112">Další informace o vlastnostech závislostí (typ vlastnosti, které jsou zobrazeny v těchto příkladech) a jejich funkce najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40d4c-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="40d4c-113">Jiné způsoby animace bez použití <xref:System.Windows.Media.Animation.Storyboard> objekty; Další informace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40d4c-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d4c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="40d4c-114">See Also</span></span>  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="40d4c-115">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="40d4c-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="40d4c-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="40d4c-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
