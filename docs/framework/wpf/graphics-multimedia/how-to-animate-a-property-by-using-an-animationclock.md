---
title: 'Postupy: Animace vlastnosti pomocí AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 4fa9efc593461d26eabaee5e2f62c1a17da1b543
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761010"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="d1279-102">Postupy: Animace vlastnosti pomocí AnimationClock</span><span class="sxs-lookup"><span data-stu-id="d1279-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="d1279-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Clock> objekty animovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1279-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="d1279-104">Existují tři způsoby, jak animovat vlastnost závislosti:</span><span class="sxs-lookup"><span data-stu-id="d1279-104">There are three ways to animate a dependency property:</span></span>  
  
- <span data-ttu-id="d1279-105">Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> a přidružte jej k vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="d1279-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
- <span data-ttu-id="d1279-106">Použití objektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> způsob, jak použít jediné <xref:System.Windows.Media.Animation.AnimationTimeline> cílové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1279-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
- <span data-ttu-id="d1279-107">Vytvoření <xref:System.Windows.Media.Animation.AnimationClock> ze <xref:System.Windows.Media.Animation.AnimationTimeline> a použít ji pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1279-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="d1279-108"><xref:System.Windows.Media.Animation.Storyboard> objekty a <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umožňují animace vlastnosti bez přímo vytváření a distribuci hodiny (příklady najdete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) a [animace vlastnosti bez Scénáře použití](how-to-animate-a-property-without-using-a-storyboard.md)); hodiny se vytvořila a distribuovala za vás automaticky.</span><span class="sxs-lookup"><span data-stu-id="d1279-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1279-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1279-109">Example</span></span>  
 <span data-ttu-id="d1279-110">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro dvě podobné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1279-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="d1279-111">Příklad ukazuje, jak interaktivní řízení <xref:System.Windows.Media.Animation.Clock> po jeho spuštění, naleznete v tématu [interaktivní řízení hodin](how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="d1279-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1279-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1279-112">See also</span></span>

- [<span data-ttu-id="d1279-113">Animace vlastnosti pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="d1279-113">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="d1279-114">Animace vlastnosti bez pomoci scénáře</span><span class="sxs-lookup"><span data-stu-id="d1279-114">Animate a Property Without Using a Storyboard</span></span>](how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="d1279-115">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="d1279-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
