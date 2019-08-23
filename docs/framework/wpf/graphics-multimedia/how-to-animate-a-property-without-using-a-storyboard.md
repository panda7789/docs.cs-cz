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
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963010"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="00a61-102">Postupy: Animace vlastnosti bez pomoci scénáře</span><span class="sxs-lookup"><span data-stu-id="00a61-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="00a61-103">Tento příklad ukazuje jeden způsob, jak použít animaci na vlastnost bez použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="00a61-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a61-104">Tato funkce není k dispozici [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="00a61-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="00a61-105">Informace o animování vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="00a61-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="00a61-106">Chcete-li použít místní animaci na vlastnost, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="00a61-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="00a61-107">Tato metoda používá dva parametry: a <xref:System.Windows.DependencyProperty> , který určuje vlastnost, která má být animována, a animaci, která má být použita pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="00a61-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00a61-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="00a61-108">Example</span></span>  
 <span data-ttu-id="00a61-109">Následující příklad ukazuje, jak animovat šířku a barvu <xref:System.Windows.Controls.Button>pozadí.</span><span class="sxs-lookup"><span data-stu-id="00a61-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="00a61-110">Různé třídy animace v <xref:System.Windows.Media.Animation> oboru názvů existují pro animování různých typů vlastností.</span><span class="sxs-lookup"><span data-stu-id="00a61-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="00a61-111">Další informace o animování vlastností najdete v tématu [Přehled animací](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00a61-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="00a61-112">Další informace o vlastnostech závislosti (typu vlastností, které jsou uvedeny v těchto příkladech) a jejich funkcích naleznete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00a61-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="00a61-113">Existují i jiné způsoby, jak animovat bez <xref:System.Windows.Media.Animation.Storyboard> použití objektů; další informace naleznete v tématu [Přehled postupů animace vlastností](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00a61-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a61-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00a61-114">See also</span></span>

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="00a61-115">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="00a61-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="00a61-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="00a61-116">Animation Overview</span></span>](animation-overview.md)
