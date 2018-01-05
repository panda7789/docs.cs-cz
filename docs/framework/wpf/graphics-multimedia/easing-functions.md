---
title: "Funkce usnadnění"
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
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 570a065d3f28befe8db4887ff908c3bd60a639a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="easing-functions"></a><span data-ttu-id="973a2-102">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="973a2-102">Easing Functions</span></span>
<span data-ttu-id="973a2-103">Funkce usnadnění můžete použít vlastní matematické vzorce pro své animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="973a2-104">Například můžete objekt reálně kolísají nebo chovat, jako by šlo na pružiny.</span><span class="sxs-lookup"><span data-stu-id="973a2-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="973a2-105">Můžete použít klíč rámce, nebo i z/do nebo podle animací sblížit těchto důsledcích, ale bude potřeba významné množství práce a animace bude přesností menší než pomocí matematické vzorce.</span><span class="sxs-lookup"><span data-stu-id="973a2-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="973a2-106">Kromě vytvoření vlastní funkce nejvýraznější dědění ze <xref:System.Windows.Media.Animation.EasingFunctionBase>, jedním z několika nejvýraznější funkce poskytované modulem runtime můžete vytvořit běžné účinky.</span><span class="sxs-lookup"><span data-stu-id="973a2-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="973a2-107"><xref:System.Windows.Media.Animation.BackEase>: Odvolá pohybu animace mírně předtím, než začne animace v uvedené cestě.</span><span class="sxs-lookup"><span data-stu-id="973a2-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="973a2-108"><xref:System.Windows.Media.Animation.BounceEase>: Vytvoří skákající efekt.</span><span class="sxs-lookup"><span data-stu-id="973a2-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="973a2-109"><xref:System.Windows.Media.Animation.CircleEase>: Vytvoří které zrychluje nebo zpomaluje pomocí funkce kruhový animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="973a2-110"><xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="973a2-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="973a2-111"><xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animace, která se podobá pružiny, oscilační a zpět, dokud dojde na rest.</span><span class="sxs-lookup"><span data-stu-id="973a2-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="973a2-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí exponenciální vzorce.</span><span class="sxs-lookup"><span data-stu-id="973a2-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="973a2-113"><xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>p</sup> kde je rovno p<xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="973a2-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="973a2-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="973a2-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="973a2-115"><xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="973a2-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="973a2-116"><xref:System.Windows.Media.Animation.QuinticEase>: Vytvoření animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="973a2-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="973a2-117"><xref:System.Windows.Media.Animation.SineEase>: Vytvoří které zrychluje nebo zpomaluje pomocí vzorce sinus animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="973a2-118">Chování tyto funkce usnadnění pomocí následující ukázky můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="973a2-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="973a2-119">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="973a2-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="973a2-120">Chcete-li použít nejvýraznější funkce animace, použijte `EasingFunction` vlastnost animace určovat nejvýraznější funkce, která se týkají animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="973a2-121">Následující příklad se vztahuje <xref:System.Windows.Media.Animation.BounceEase> funkce k usnadnění <xref:System.Windows.Media.Animation.DoubleAnimation> vytvořit skákající efekt.</span><span class="sxs-lookup"><span data-stu-id="973a2-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="973a2-122">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="973a2-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="973a2-123">V předchozím příkladu byla použita nejvýraznější funkce k From/k/podle animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="973a2-124">Tyto funkce usnadnění může platit taky pro animací jednotlivých klíč.</span><span class="sxs-lookup"><span data-stu-id="973a2-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="973a2-125">Následující příklad ukazuje, jak používat klíčových snímků s usnadnění funkce, které jsou přidruženy k vytváření animace obdélník, který kontrakty směrem nahoru, zpomaluje, potom rozšíří dolů (jakoby návratem) a pak nedoručitelných zpráv na určeném místě.</span><span class="sxs-lookup"><span data-stu-id="973a2-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="973a2-126">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="973a2-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="973a2-127">Můžete použít <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> vlastnost pro úpravu nejvýraznější funkce chování, který je změnit, jak argument interpolaci animace.</span><span class="sxs-lookup"><span data-stu-id="973a2-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="973a2-128">Existují tři možné hodnoty můžete udělit pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="973a2-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="973a2-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace následuje matematický vzorec přidružené nejvýraznější funkce.</span><span class="sxs-lookup"><span data-stu-id="973a2-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="973a2-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje interpolace 100 % minus výstup vzorce přidružené nejvýraznější funkce.</span><span class="sxs-lookup"><span data-stu-id="973a2-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="973a2-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Používá interpolace <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první polovinu animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> pro druhou polovinu.</span><span class="sxs-lookup"><span data-stu-id="973a2-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="973a2-132">Grafy níže ukazují různé hodnoty <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> kde *f*(*x*) představuje animace průběhu a *t* představuje čas.</span><span class="sxs-lookup"><span data-stu-id="973a2-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="973a2-133">![Vlastnosti EasingMode funkce BackEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="973a2-134">![Vlastnosti EasingMode funkce BounceEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="973a2-135">![Vlastnosti EasingMode funkce CircleEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="973a2-136">![Vlastnosti EasingMode funkce CubicEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="973a2-137">![Funkce ElasticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="973a2-138">![Grafy funkce ExponentialEase různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="973a2-139">![Funkce QuarticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="973a2-140">![Funkce QuadraticEase s grafy různých režimů funkce Easing](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="973a2-141">![Funkce QuarticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="973a2-142">![Funkce QuinticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="973a2-143">![Funkce SineEase pro různé hodnoty vlastnosti EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="973a2-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="973a2-144">Můžete použít <xref:System.Windows.Media.Animation.PowerEase> vytvořit stejné chování jako <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="973a2-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="973a2-145">Například, pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> nahradit pro <xref:System.Windows.Media.Animation.CubicEase>, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="973a2-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="973a2-146">Kromě používání funkce usnadnění, které jsou součástí běhu, můžete vytvořit vlastní nejvýraznější funkce, která dědí z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="973a2-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="973a2-147">Následující příklad ukazuje, jak vytvořit jednoduché vlastní nejvýraznější funkcí.</span><span class="sxs-lookup"><span data-stu-id="973a2-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="973a2-148">Můžete přidat vlastní Matematická logika pro chování nejvýraznější funkce přepsáním <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="973a2-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="973a2-149">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="973a2-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
