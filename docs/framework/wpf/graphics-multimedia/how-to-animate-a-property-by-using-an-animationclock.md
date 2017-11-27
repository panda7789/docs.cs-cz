---
title: "Postupy: Animace vlastnosti pomocí AnimationClock"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47df7aaad45000bc8c761a9bb9022d37e0f0828c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="d72f1-102">Postupy: Animace vlastnosti pomocí AnimationClock</span><span class="sxs-lookup"><span data-stu-id="d72f1-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="d72f1-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Clock> objekty, které se použije animaci vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d72f1-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="d72f1-104">Existují tři způsoby, jak animace vlastnosti závislosti:</span><span class="sxs-lookup"><span data-stu-id="d72f1-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="d72f1-105">Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> a přidružte ji k vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="d72f1-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="d72f1-106">Pomocí objektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda použití jedné <xref:System.Windows.Media.Animation.AnimationTimeline> pro vlastnost target.</span><span class="sxs-lookup"><span data-stu-id="d72f1-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="d72f1-107">Vytvoření <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> a použijte ho pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d72f1-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="d72f1-108"><xref:System.Windows.Media.Animation.Storyboard>objekty a <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda umožňují animace vlastnosti bez přímo vytváření a distribuci hodiny (příklady najdete v tématu [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) a [animace vlastnosti bez Použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); hodiny jsou vytvořen a distribuován pro vás automaticky.</span><span class="sxs-lookup"><span data-stu-id="d72f1-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d72f1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d72f1-109">Example</span></span>  
 <span data-ttu-id="d72f1-110">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použijte ho pro dvě podobné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d72f1-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="d72f1-111">Příklad znázorňující postup interaktivně řízení <xref:System.Windows.Media.Animation.Clock> po zahájení, najdete v části [interaktivně řízení hodiny, které](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="d72f1-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72f1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d72f1-112">See Also</span></span>  
 [<span data-ttu-id="d72f1-113">Animace vlastnost pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="d72f1-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="d72f1-114">Animace vlastnost bez použití scénáře</span><span class="sxs-lookup"><span data-stu-id="d72f1-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="d72f1-115">Vlastnost animace techniky – přehled</span><span class="sxs-lookup"><span data-stu-id="d72f1-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
