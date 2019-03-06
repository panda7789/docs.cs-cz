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
# <a name="easing-functions"></a>Funkce usnadnění
Funkcí usnadnění umožňují použít vlastní matematické vzorce animace. Například můžete objekt realisticky odraz nebo se chovat, jako by šlo o spring. Můžete použít k odhadu negativních dopadů klíčových snímků nebo dokonce od/Komu/kým animace, ale by to obnášelo značné množství práce a animace bude méně přesné než matematické vzorce.  
  
 Kromě vytvoření svoji vlastní funkci uvolnění děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>, jeden z několika funkcí usnadnění poskytovaný modulem runtime můžete použít k vytvoření běžné účinky.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Odvolá pohybu animace mírně před jeho zahájením animace v uvedené cestě.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Vytváří skákající efekt.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí, pomocí funkce cyklický.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animace, která se podobá spring oscilační vpřed a zpět, dokud jde o rozhraní rest.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí exponenciálního vzorce.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>p</sup> kde p je rovna <xref:System.Windows.Media.Animation.PowerEase.Power%2A>vlastnost.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Vytvořit animaci, která zrychluje a/nebo zpomalí pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Vytvoří animaci, která zrychluje a/nebo zpomalí pomocí vzorce sinus.  
  
 Chcete-li použít funkci zpomalení animace, použijte `EasingFunction` zadejte funkci uvolnění použít pro animaci vlastnosti animace. Následující příklad se vztahuje <xref:System.Windows.Media.Animation.BounceEase> funkce k uvolnění <xref:System.Windows.Media.Animation.DoubleAnimation> vytvořit skákající efekt.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 V předchozím příkladu funkci uvolnění aplikováno od/Komu/kým animace. Můžete také použít těchto funkcí usnadnění pro animace klíčových snímků. Následující příklad ukazuje, jak pomocí klíčových snímků k nim má přiřazené funkce usnadnění pro vytvoření animace obdélníku, který kontrakty směrem nahoru, může zpomalit, pak zvětší směrem dolů (jakoby klesá) a potom nedoručitelných zpráv a zastaví.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Můžete použít <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> změnit vlastnost změnit funkci zpomalení chování, to znamená, jak argument interpolaci animace. Existují tři možné hodnoty, které poskytnete pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace následuje matematické vzorce přidružený k funkci přechodu.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje interpolace 100 % minus výstup vzorec přidružený k funkci přechodu.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Použití interpolace <xref:System.Windows.Media.Animation.EasingMode.EaseIn> v první polovině animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> v druhé polovině.  
  
 Následující grafy ukazují různé hodnoty <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> kde *f*(*x*) představuje animace průběhu a *t* představuje čas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Vlastnosti EasingMode BackEase funkce ](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Vlastnosti EasingMode BounceEase funkce ](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Vlastnosti EasingMode CircleEase funkce ](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Vlastnosti EasingMode CubicEase funkce ](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Funkce ElasticEase s grafy různých režimů funkce Easing. ](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Funkce ExponentialEase grafy různých režimů funkce Easing. ](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Funkce QuarticEase s grafy různých režimů funkce Easing. ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Funkce QuadraticEase s grafy různých režimů funkce Easing](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Funkce QuarticEase s grafy různých režimů funkce Easing. ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Funkce QuinticEase s grafy různých režimů funkce Easing. ](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![Funkce pro různé hodnoty vlastnosti EasingMode SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Můžete použít <xref:System.Windows.Media.Animation.PowerEase> vytvoření stejné chování jako <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnost. Například, pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> pro nahrazení <xref:System.Windows.Media.Animation.CubicEase>, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.  
  
 Kromě použití funkcí usnadnění, které jsou součástí za běhu, můžete vytvořit vlastní funkce usnadnění děděním z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Následující příklad ukazuje, jak vytvořit jednoduchou funkci vlastní uvolnění. Můžete přidat vlastní logiku matematická pro chování funkci uvolnění tak, že přepíšete <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
