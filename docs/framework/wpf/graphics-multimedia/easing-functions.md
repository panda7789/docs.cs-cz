---
title: Funkce usnadnění
ms.date: 03/30/2017
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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965736"
---
# <a name="easing-functions"></a><span data-ttu-id="875a6-102">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="875a6-102">Easing Functions</span></span>
<span data-ttu-id="875a6-103">Funkce usnadnění umožňují použít pro animace vlastní matematické vzorce.</span><span class="sxs-lookup"><span data-stu-id="875a6-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="875a6-104">Například můžete chtít, aby objekt realisticky vynechal nebo choval, jako by byl na jaře.</span><span class="sxs-lookup"><span data-stu-id="875a6-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="875a6-105">K aproximaci těchto efektů byste mohli použít klíčový rámec nebo dokonce i z animací a, ale to by vedlo k výraznému množství práce a animace bude méně přesná než při použití matematického vzorce.</span><span class="sxs-lookup"><span data-stu-id="875a6-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="875a6-106">Kromě vytvoření vlastní funkce náběh a dědění z <xref:System.Windows.Media.Animation.EasingFunctionBase>můžete použít jednu z několika funkcí usnadnění poskytovaných modulem runtime k vytvoření běžných efektů.</span><span class="sxs-lookup"><span data-stu-id="875a6-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="875a6-107"><xref:System.Windows.Media.Animation.BackEase>: Odvolá pohyb animace mírně předtím, než se začne animovat v uvedené cestě.</span><span class="sxs-lookup"><span data-stu-id="875a6-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="875a6-108"><xref:System.Windows.Media.Animation.BounceEase>: Vytvoří skákající efekt.</span><span class="sxs-lookup"><span data-stu-id="875a6-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="875a6-109"><xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí kruhové funkce.</span><span class="sxs-lookup"><span data-stu-id="875a6-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="875a6-110"><xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="875a6-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="875a6-111"><xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animaci, která se podobá jarnímu kmitání a až do chvíle, kdy přijde do klidového režimu.</span><span class="sxs-lookup"><span data-stu-id="875a6-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="875a6-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí exponenciálního vzorce.</span><span class="sxs-lookup"><span data-stu-id="875a6-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="875a6-113"><xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>p</sup> , kde p je rovna <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="875a6-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="875a6-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="875a6-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="875a6-115"><xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="875a6-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="875a6-116"><xref:System.Windows.Media.Animation.QuinticEase>: Vytvořte animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="875a6-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="875a6-117"><xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce sinus.</span><span class="sxs-lookup"><span data-stu-id="875a6-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="875a6-118">Chcete-li použít funkci náběh a doběh pro animaci, `EasingFunction` použijte vlastnost animace a určete funkci náběh a doběh, která se má použít pro animaci.</span><span class="sxs-lookup"><span data-stu-id="875a6-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="875a6-119">Následující příklad používá <xref:System.Windows.Media.Animation.BounceEase> funkci náběh a doběh <xref:System.Windows.Media.Animation.DoubleAnimation> pro vytvoření skákajícího efektu.</span><span class="sxs-lookup"><span data-stu-id="875a6-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="875a6-120">V předchozím příkladu byla funkce náběhu a animací aplikována na animaci od/do/.</span><span class="sxs-lookup"><span data-stu-id="875a6-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="875a6-121">Tyto funkce usnadnění můžete použít také pro animace klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="875a6-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="875a6-122">Následující příklad ukazuje, jak používat klíčové snímky s funkcemi usnadnění, které jsou k nim přidružené, k vytvoření animace obdélníku, který se smlouvou nahoru, zpomaluje a pak rozbalí dolů (jak je to možné) a pak se zastaví.</span><span class="sxs-lookup"><span data-stu-id="875a6-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="875a6-123"><xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Vlastnost lze použít pro změnu způsobu, jakým se chová funkce náběhu a nikoli. to znamená změnit způsob, jakým se animace interpoluje.</span><span class="sxs-lookup"><span data-stu-id="875a6-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="875a6-124">Existují tři možné hodnoty, které můžete zadat pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="875a6-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="875a6-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace probíhá pomocí matematického vzorce spojeného s funkcí náběh/doběh.</span><span class="sxs-lookup"><span data-stu-id="875a6-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="875a6-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje 100% interpolace minus výstup vzorce přidruženého k funkci náběh/doběh.</span><span class="sxs-lookup"><span data-stu-id="875a6-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="875a6-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolace používá <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první polovinu animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> za druhou polovinu.</span><span class="sxs-lookup"><span data-stu-id="875a6-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="875a6-128">Následující grafy <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> ukazují různé hodnoty, kde *f*(*x*) představuje průběh animace a *t* představuje čas.</span><span class="sxs-lookup"><span data-stu-id="875a6-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="875a6-129">![EasingMode grafy.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="875a6-130">![BounceEase EasingMode grafy.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="875a6-131">![CircleEase EasingMode grafy.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="875a6-132">![CubicEase EasingMode grafy.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="875a6-133">![ElasticEase s grafy různých easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="875a6-134">![ExponentialEase grafy různých easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="875a6-135">![QuarticEase s grafy různých easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="875a6-136">![QuadraticEase s grafy různých easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="875a6-137">![QuarticEase s grafy různých easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="875a6-138">![QuinticEase s grafy různých easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="875a6-139">![SineEase pro různé EasingMode hodnoty](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="875a6-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="875a6-140">Můžete použít <xref:System.Windows.Media.Animation.PowerEase> k vytvoření stejného chování jako <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase> <xref:System.Windows.Media.Animation.CubicEase>,, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="875a6-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="875a6-141">Například pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> k <xref:System.Windows.Media.Animation.CubicEase>nahrazení, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="875a6-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="875a6-142">Kromě používání funkcí usnadnění obsažených v době běhu můžete vytvořit vlastní funkce náběhu a dědění z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="875a6-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="875a6-143">Následující příklad ukazuje, jak vytvořit jednoduchou vlastní funkci náběh a doběh.</span><span class="sxs-lookup"><span data-stu-id="875a6-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="875a6-144">Pomocí přepsání <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody můžete přidat vlastní matematickou logiku pro chování funkce náběh/doběh.</span><span class="sxs-lookup"><span data-stu-id="875a6-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
