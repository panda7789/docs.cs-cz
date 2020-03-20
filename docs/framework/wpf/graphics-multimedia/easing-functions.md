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
# <a name="easing-functions"></a>Funkce usnadnění
Funkce náběhu/doběhu umožňují použít vlastní matematické vzorce na animace. Můžete například chtít, aby se objekt realisticky odrazil nebo se choval, jako by byl na pružině. Můžete použít Key-Frame nebo dokonce From/To/By animace pro aproximaci těchto efektů, ale to by trvalo značné množství práce a animace by bylo méně přesné než pomocí matematického vzorce.  
  
 Kromě vytvoření vlastní funkce náběhu/doběhu děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>, můžete použít jednu z několika funkcí náběhu/doběhu poskytovaných modulem runtime k vytvoření běžných efektů.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Mírně zatáhne pohyb animace, než začne animovat v uvedené cestě.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Vytvoří efekt odrážení.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí kruhové funkce.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animaci, která se podobá jarní oscilesmu tam a zpět, dokud neodpočívá.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí exponenciálního vzorce.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*( <xref:System.Windows.Media.Animation.PowerEase.Power%2A> *t*) = *t*<sup>p,</sup> kde p se rovná vlastnosti.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Vytvořte animaci, která zrychluje a/nebo zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychluje nebo zpomaluje pomocí sinusového vzorce.  
  
 Chcete-li použít funkci náběhu/doběhu na animaci, použijte `EasingFunction` vlastnost animace a určete funkci náběhu/doběhu, která se má na animaci použít. Následující příklad použije <xref:System.Windows.Media.Animation.BounceEase> funkci náběhu/doběhu na a <xref:System.Windows.Media.Animation.DoubleAnimation> a a vytvoří efekt odrážení.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 V předchozím příkladu byla funkce náběhu/odsuzování použita na animaci From/To/By. Tyto funkce náběhu/doběhu můžete také použít na animace klíčových snímků. Následující příklad ukazuje, jak pomocí klíčových snímků s funkcemi náběhu/doběhu, které jsou s nimi spojeny, k vytvoření animace obdélníku, který se smršťuje směrem nahoru, zpomaluje, pak se rozšiřuje směrem dolů (jako by padal) a pak se odrazí na zastávku.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Vlastnost můžete použít ke změně způsobu, jakým se vyvíjí funkce náběhu/doběhu, to znamená, že změníte způsob interpolace animace. Existují tři možné hodnoty, <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>které můžete uvést:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace se řídí matematickým vzorcem přidruženým k funkci náběhu/doběhu.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje 100% interpolaci mínus výstup vzorce spojeného s funkcí náběhu/doběhu.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolace používá <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první <xref:System.Windows.Media.Animation.EasingMode.EaseOut> polovinu animace a pro druhou polovinu.  
  
 Níže uvedené grafy ukazují <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> různé hodnoty, kde *f*(*x*) představuje průběh animace a *t* představuje čas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Grafy BackEase EasingMode.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode grafy.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode grafy.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode grafy.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase s grafy různých režimů náběhu/doběhu.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![ExponenciálníUsnadnit grafy různých režimů náběhu/doběhu.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase s grafy různých režimů náběhu/doběhu.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase s grafy různých režimů náběhu/doběhu](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase s grafy různých režimů náběhu/doběhu.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase s grafy různých režimů náběh/doběhu.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase pro různé hodnoty EasingMode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Můžete vytvořit <xref:System.Windows.Media.Animation.PowerEase> stejné chování jako <xref:System.Windows.Media.Animation.CubicEase> <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, <xref:System.Windows.Media.Animation.QuinticEase> a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> pomocí vlastnosti. Chcete-li například použít <xref:System.Windows.Media.Animation.PowerEase> jako <xref:System.Windows.Media.Animation.CubicEase>náhradu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , zadejte hodnotu 3.  
  
 Kromě použití funkcí náběhu/doběhu zahrnutých v běhu můžete vytvořit vlastní funkce <xref:System.Windows.Media.Animation.EasingFunctionBase>náběhu/doběhu děděním z aplikace . Následující příklad ukazuje, jak vytvořit jednoduchou vlastní funkci náběhu/doběhu. Můžete přidat vlastní matematickou logiku pro to, jak <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> se chová funkce náběhu/doběhu přepsáním metody.
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
