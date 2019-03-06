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
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354502"
---
# <a name="easing-functions"></a><span data-ttu-id="6dd69-102">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="6dd69-102">Easing Functions</span></span>
<span data-ttu-id="6dd69-103">Funkcí usnadnění umožňují použít vlastní matematické vzorce animace.</span><span class="sxs-lookup"><span data-stu-id="6dd69-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="6dd69-104">Například můžete objekt realisticky odraz nebo se chovat, jako by šlo o spring.</span><span class="sxs-lookup"><span data-stu-id="6dd69-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="6dd69-105">Můžete použít k odhadu negativních dopadů klíčových snímků nebo dokonce od/Komu/kým animace, ale by to obnášelo značné množství práce a animace bude méně přesné než matematické vzorce.</span><span class="sxs-lookup"><span data-stu-id="6dd69-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="6dd69-106">Kromě vytvoření svoji vlastní funkci uvolnění děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>, jeden z několika funkcí usnadnění poskytovaný modulem runtime můžete použít k vytvoření běžné účinky.</span><span class="sxs-lookup"><span data-stu-id="6dd69-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="6dd69-107"><xref:System.Windows.Media.Animation.BackEase>: Odvolá pohybu animace mírně před jeho zahájením animace v uvedené cestě.</span><span class="sxs-lookup"><span data-stu-id="6dd69-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="6dd69-108"><xref:System.Windows.Media.Animation.BounceEase>: Vytváří skákající efekt.</span><span class="sxs-lookup"><span data-stu-id="6dd69-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="6dd69-109"><xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí, pomocí funkce cyklický.</span><span class="sxs-lookup"><span data-stu-id="6dd69-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="6dd69-110"><xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="6dd69-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="6dd69-111"><xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animace, která se podobá spring oscilační vpřed a zpět, dokud jde o rozhraní rest.</span><span class="sxs-lookup"><span data-stu-id="6dd69-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="6dd69-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí exponenciálního vzorce.</span><span class="sxs-lookup"><span data-stu-id="6dd69-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="6dd69-113"><xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>p</sup> kde p je rovna <xref:System.Windows.Media.Animation.PowerEase.Power%2A>vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6dd69-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="6dd69-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="6dd69-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="6dd69-115"><xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="6dd69-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="6dd69-116"><xref:System.Windows.Media.Animation.QuinticEase>: Vytvořit animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="6dd69-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="6dd69-117"><xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce sinus.</span><span class="sxs-lookup"><span data-stu-id="6dd69-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="6dd69-118">Chcete-li použít funkci zpomalení animace, použijte `EasingFunction` zadejte funkci uvolnění použít pro animaci vlastnosti animace.</span><span class="sxs-lookup"><span data-stu-id="6dd69-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="6dd69-119">Následující příklad se vztahuje <xref:System.Windows.Media.Animation.BounceEase> funkce k uvolnění <xref:System.Windows.Media.Animation.DoubleAnimation> vytvořit skákající efekt.</span><span class="sxs-lookup"><span data-stu-id="6dd69-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="6dd69-120">V předchozím příkladu funkci uvolnění aplikováno od/Komu/kým animace.</span><span class="sxs-lookup"><span data-stu-id="6dd69-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="6dd69-121">Můžete také použít těchto funkcí usnadnění pro animace klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="6dd69-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="6dd69-122">Následující příklad ukazuje, jak pomocí klíčových snímků k nim má přiřazené funkce usnadnění pro vytvoření animace obdélníku, který kontrakty směrem nahoru, může zpomalit, pak zvětší směrem dolů (jakoby klesá) a potom nedoručitelných zpráv a zastaví.</span><span class="sxs-lookup"><span data-stu-id="6dd69-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="6dd69-123">Můžete použít <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> změnit vlastnost změnit funkci zpomalení chování, to znamená, jak argument interpolaci animace.</span><span class="sxs-lookup"><span data-stu-id="6dd69-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="6dd69-124">Existují tři možné hodnoty, které poskytnete pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="6dd69-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="6dd69-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace následuje matematické vzorce přidružený k funkci přechodu.</span><span class="sxs-lookup"><span data-stu-id="6dd69-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="6dd69-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje interpolace 100 % minus výstup vzorec přidružený k funkci přechodu.</span><span class="sxs-lookup"><span data-stu-id="6dd69-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="6dd69-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Použití interpolace <xref:System.Windows.Media.Animation.EasingMode.EaseIn> v první polovině animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> v druhé polovině.</span><span class="sxs-lookup"><span data-stu-id="6dd69-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="6dd69-128">Následující grafy ukazují různé hodnoty <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> kde *f*(*x*) představuje animace průběhu a *t* představuje čas.</span><span class="sxs-lookup"><span data-stu-id="6dd69-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="6dd69-129">![Vlastnosti EasingMode BackEase funkce ](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="6dd69-130">![Vlastnosti EasingMode BounceEase funkce ](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="6dd69-131">![Vlastnosti EasingMode CircleEase funkce ](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="6dd69-132">![Vlastnosti EasingMode CubicEase funkce ](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="6dd69-133">![Funkce ElasticEase s grafy různých režimů funkce Easing. ](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="6dd69-134">![Funkce ExponentialEase grafy různých režimů funkce Easing. ](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="6dd69-135">![Funkce QuarticEase s grafy různých režimů funkce Easing. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="6dd69-136">![Funkce QuadraticEase s grafy různých režimů funkce Easing](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="6dd69-137">![Funkce QuarticEase s grafy různých režimů funkce Easing. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="6dd69-138">![Funkce QuinticEase s grafy různých režimů funkce Easing. ](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="6dd69-139">![Funkce pro různé hodnoty vlastnosti EasingMode SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6dd69-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dd69-140">Můžete použít <xref:System.Windows.Media.Animation.PowerEase> vytvoření stejné chování jako <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6dd69-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="6dd69-141">Například, pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> pro nahrazení <xref:System.Windows.Media.Animation.CubicEase>, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="6dd69-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="6dd69-142">Kromě použití funkcí usnadnění, které jsou součástí za běhu, můžete vytvořit vlastní funkce usnadnění děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="6dd69-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="6dd69-143">Následující příklad ukazuje, jak vytvořit jednoduchou funkci vlastní uvolnění.</span><span class="sxs-lookup"><span data-stu-id="6dd69-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="6dd69-144">Můžete přidat vlastní logiku matematická pro chování funkci uvolnění tak, že přepíšete <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6dd69-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
