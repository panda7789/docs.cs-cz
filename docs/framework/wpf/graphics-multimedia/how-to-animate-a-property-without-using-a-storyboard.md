---
title: 'Postupy: Animace vlastnosti bez pomoci pomoci scénáře'
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
ms.openlocfilehash: b76afeb0187065ff07c832363d3a52896aa36822
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371157"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="f1cb7-102">Postupy: Animace vlastnosti bez pomoci pomoci scénáře</span><span class="sxs-lookup"><span data-stu-id="f1cb7-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="f1cb7-103">Tento příklad ukazuje jeden ze způsobů použití animace vlastnosti bez použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="f1cb7-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1cb7-104">Tato funkce není k dispozici v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1cb7-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="f1cb7-105">Informace o animování vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="f1cb7-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="f1cb7-106">Chcete-li použít místní animace na vlastnost, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f1cb7-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="f1cb7-107">Tato metoda přebírá dva parametry: <xref:System.Windows.DependencyProperty> , který určuje vlastnost, která má animace a animace, který chcete použít pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f1cb7-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cb7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1cb7-108">Example</span></span>  
 <span data-ttu-id="f1cb7-109">Následující příklad ukazuje, jak animovat barva šířku a na pozadí <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f1cb7-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="f1cb7-110">Různé třídy animace v <xref:System.Windows.Media.Animation> oboru názvů existuje pro různé typy vlastností animace.</span><span class="sxs-lookup"><span data-stu-id="f1cb7-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="f1cb7-111">Další informace o animace vlastností najdete v tématu [přehled animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1cb7-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="f1cb7-112">Další informace o vlastnosti závislosti (typ vlastnosti, které jsou uvedeny v těchto příkladech) a jejich funkcích najdete v části [přehled vlastností závislosti](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1cb7-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="f1cb7-113">Existují jiné způsoby, jak animovat bez použití <xref:System.Windows.Media.Animation.Storyboard> objekty; Další informace najdete v tématu [přehled způsobů animace vlastností](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1cb7-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cb7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1cb7-114">See also</span></span>
- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="f1cb7-115">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="f1cb7-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="f1cb7-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="f1cb7-116">Animation Overview</span></span>](animation-overview.md)
