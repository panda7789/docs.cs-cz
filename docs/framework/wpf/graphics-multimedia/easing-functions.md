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
# <a name="easing-functions"></a>Funkce usnadnění
Funkce usnadnění umožňují použít pro animace vlastní matematické vzorce. Například můžete chtít, aby objekt realisticky vynechal nebo choval, jako by byl na jaře. K aproximaci těchto efektů byste mohli použít klíčový rámec nebo dokonce i z animací a, ale to by vedlo k výraznému množství práce a animace bude méně přesná než při použití matematického vzorce.  
  
 Kromě vytvoření vlastní funkce náběh a dědění z <xref:System.Windows.Media.Animation.EasingFunctionBase>můžete použít jednu z několika funkcí usnadnění poskytovaných modulem runtime k vytvoření běžných efektů.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Odvolá pohyb animace mírně předtím, než se začne animovat v uvedené cestě.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Vytvoří skákající efekt.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí kruhové funkce.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animaci, která se podobá jarnímu kmitání a až do chvíle, kdy přijde do klidového režimu.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí exponenciálního vzorce.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>p</sup> , kde p je rovna <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnosti.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Vytvořte animaci, která zrychlí a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychlí a/nebo zpomaluje pomocí vzorce sinus.  
  
 Chcete-li použít funkci náběh a doběh pro animaci, `EasingFunction` použijte vlastnost animace a určete funkci náběh a doběh, která se má použít pro animaci. Následující příklad používá <xref:System.Windows.Media.Animation.BounceEase> funkci náběh a doběh <xref:System.Windows.Media.Animation.DoubleAnimation> pro vytvoření skákajícího efektu.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 V předchozím příkladu byla funkce náběhu a animací aplikována na animaci od/do/. Tyto funkce usnadnění můžete použít také pro animace klíčových snímků. Následující příklad ukazuje, jak používat klíčové snímky s funkcemi usnadnění, které jsou k nim přidružené, k vytvoření animace obdélníku, který se smlouvou nahoru, zpomaluje a pak rozbalí dolů (jak je to možné) a pak se zastaví.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Vlastnost lze použít pro změnu způsobu, jakým se chová funkce náběhu a nikoli. to znamená změnit způsob, jakým se animace interpoluje. Existují tři možné hodnoty, které můžete zadat pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace probíhá pomocí matematického vzorce spojeného s funkcí náběh/doběh.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje 100% interpolace minus výstup vzorce přidruženého k funkci náběh/doběh.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolace používá <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první polovinu animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> za druhou polovinu.  
  
 Následující grafy <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> ukazují různé hodnoty, kde *f*(*x*) představuje průběh animace a *t* představuje čas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![EasingMode grafy.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode grafy.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode grafy.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode grafy.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase s grafy různých easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![ExponentialEase grafy různých easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase s grafy různých easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase s grafy různých easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase s grafy různých easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase s grafy různých easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase pro různé EasingMode hodnoty](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Můžete použít <xref:System.Windows.Media.Animation.PowerEase> k vytvoření stejného chování jako <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase> <xref:System.Windows.Media.Animation.CubicEase>,, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnosti. Například pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> k <xref:System.Windows.Media.Animation.CubicEase>nahrazení, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.  
  
 Kromě používání funkcí usnadnění obsažených v době běhu můžete vytvořit vlastní funkce náběhu a dědění z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Následující příklad ukazuje, jak vytvořit jednoduchou vlastní funkci náběh a doběh. Pomocí přepsání <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody můžete přidat vlastní matematickou logiku pro chování funkce náběh/doběh.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
