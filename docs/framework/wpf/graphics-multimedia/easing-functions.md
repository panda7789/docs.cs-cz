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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186502"
---
# <a name="easing-functions"></a><span data-ttu-id="a19aa-102">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="a19aa-102">Easing Functions</span></span>
<span data-ttu-id="a19aa-103">Funkce náběhu/doběhu umožňují použít vlastní matematické vzorce na animace.</span><span class="sxs-lookup"><span data-stu-id="a19aa-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="a19aa-104">Můžete například chtít, aby se objekt realisticky odrazil nebo se choval, jako by byl na pružině.</span><span class="sxs-lookup"><span data-stu-id="a19aa-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="a19aa-105">Můžete použít Key-Frame nebo dokonce From/To/By animace pro aproximaci těchto efektů, ale to by trvalo značné množství práce a animace by bylo méně přesné než pomocí matematického vzorce.</span><span class="sxs-lookup"><span data-stu-id="a19aa-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="a19aa-106">Kromě vytvoření vlastní funkce náběhu/doběhu děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>, můžete použít jednu z několika funkcí náběhu/doběhu poskytovaných modulem runtime k vytvoření běžných efektů.</span><span class="sxs-lookup"><span data-stu-id="a19aa-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="a19aa-107"><xref:System.Windows.Media.Animation.BackEase>: Mírně zatáhne pohyb animace, než začne animovat v uvedené cestě.</span><span class="sxs-lookup"><span data-stu-id="a19aa-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="a19aa-108"><xref:System.Windows.Media.Animation.BounceEase>: Vytvoří efekt odrážení.</span><span class="sxs-lookup"><span data-stu-id="a19aa-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="a19aa-109"><xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí kruhové funkce.</span><span class="sxs-lookup"><span data-stu-id="a19aa-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="a19aa-110"><xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="a19aa-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="a19aa-111"><xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animaci, která se podobá jarní oscilesmu tam a zpět, dokud neodpočívá.</span><span class="sxs-lookup"><span data-stu-id="a19aa-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="a19aa-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí exponenciálního vzorce.</span><span class="sxs-lookup"><span data-stu-id="a19aa-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="a19aa-113"><xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*( <xref:System.Windows.Media.Animation.PowerEase.Power%2A> *t*) = *t*<sup>p,</sup> kde p se rovná vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a19aa-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="a19aa-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="a19aa-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="a19aa-115"><xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="a19aa-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="a19aa-116"><xref:System.Windows.Media.Animation.QuinticEase>: Vytvořte animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="a19aa-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="a19aa-117"><xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí sinusového vzorce.</span><span class="sxs-lookup"><span data-stu-id="a19aa-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="a19aa-118">Chcete-li použít funkci náběhu/doběhu na animaci, použijte `EasingFunction` vlastnost animace a určete funkci náběhu/doběhu, která se má na animaci použít.</span><span class="sxs-lookup"><span data-stu-id="a19aa-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="a19aa-119">Následující příklad použije <xref:System.Windows.Media.Animation.BounceEase> funkci náběhu/doběhu na a <xref:System.Windows.Media.Animation.DoubleAnimation> a a vytvoří efekt odrážení.</span><span class="sxs-lookup"><span data-stu-id="a19aa-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="a19aa-120">V předchozím příkladu byla funkce náběhu/odsuzování použita na animaci From/To/By.</span><span class="sxs-lookup"><span data-stu-id="a19aa-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="a19aa-121">Tyto funkce náběhu/doběhu můžete také použít na animace klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="a19aa-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="a19aa-122">Následující příklad ukazuje, jak pomocí klíčových snímků s funkcemi náběhu/doběhu, které jsou s nimi spojeny, k vytvoření animace obdélníku, který se smršťuje směrem nahoru, zpomaluje, pak se rozšiřuje směrem dolů (jako by padal) a pak se odrazí na zastávku.</span><span class="sxs-lookup"><span data-stu-id="a19aa-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="a19aa-123"><xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Vlastnost můžete použít ke změně způsobu, jakým se vyvíjí funkce náběhu/doběhu, to znamená, že změníte způsob interpolace animace.</span><span class="sxs-lookup"><span data-stu-id="a19aa-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="a19aa-124">Existují tři možné hodnoty, <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>které můžete uvést:</span><span class="sxs-lookup"><span data-stu-id="a19aa-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="a19aa-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace se řídí matematickým vzorcem přidruženým k funkci náběhu/doběhu.</span><span class="sxs-lookup"><span data-stu-id="a19aa-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="a19aa-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje 100% interpolaci mínus výstup vzorce spojeného s funkcí náběhu/doběhu.</span><span class="sxs-lookup"><span data-stu-id="a19aa-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="a19aa-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolace používá <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první <xref:System.Windows.Media.Animation.EasingMode.EaseOut> polovinu animace a pro druhou polovinu.</span><span class="sxs-lookup"><span data-stu-id="a19aa-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="a19aa-128">Níže uvedené grafy ukazují <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> různé hodnoty, kde *f*(*x*) představuje průběh animace a *t* představuje čas.</span><span class="sxs-lookup"><span data-stu-id="a19aa-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="a19aa-129">![Grafy BackEase EasingMode.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="a19aa-130">![BounceEase EasingMode grafy.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="a19aa-131">![CircleEase EasingMode grafy.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="a19aa-132">![CubicEase EasingMode grafy.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="a19aa-133">![ElasticEase s grafy různých režimů náběhu/doběhu.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="a19aa-134">![ExponenciálníUsnadnit grafy různých režimů náběhu/doběhu.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="a19aa-135">![QuarticEase s grafy různých režimů náběhu/doběhu.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="a19aa-136">![QuadraticEase s grafy různých režimů náběhu/doběhu](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="a19aa-137">![QuarticEase s grafy různých režimů náběhu/doběhu.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="a19aa-138">![QuinticEase s grafy různých režimů náběh/doběhu.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="a19aa-139">![SineEase pro různé hodnoty EasingMode](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="a19aa-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a19aa-140">Můžete vytvořit <xref:System.Windows.Media.Animation.PowerEase> stejné chování jako <xref:System.Windows.Media.Animation.CubicEase> <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, <xref:System.Windows.Media.Animation.QuinticEase> a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a19aa-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="a19aa-141">Chcete-li například použít <xref:System.Windows.Media.Animation.PowerEase> jako <xref:System.Windows.Media.Animation.CubicEase>náhradu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , zadejte hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="a19aa-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="a19aa-142">Kromě použití funkcí náběhu/doběhu zahrnutých v běhu můžete vytvořit vlastní funkce <xref:System.Windows.Media.Animation.EasingFunctionBase>náběhu/doběhu děděním z aplikace .</span><span class="sxs-lookup"><span data-stu-id="a19aa-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="a19aa-143">Následující příklad ukazuje, jak vytvořit jednoduchou vlastní funkci náběhu/doběhu.</span><span class="sxs-lookup"><span data-stu-id="a19aa-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="a19aa-144">Můžete přidat vlastní matematickou logiku pro to, jak <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> se chová funkce náběhu/doběhu přepsáním metody.</span><span class="sxs-lookup"><span data-stu-id="a19aa-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
