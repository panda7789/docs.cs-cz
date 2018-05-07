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
ms.openlocfilehash: 3ce7c1824dc53c154ba1091ea62c1b8950b757c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="easing-functions"></a>Funkce usnadnění
Funkce usnadnění můžete použít vlastní matematické vzorce pro své animace. Například můžete objekt reálně kolísají nebo chovat, jako by šlo na pružiny. Můžete použít klíč rámce, nebo i z/do nebo podle animací sblížit těchto důsledcích, ale bude potřeba významné množství práce a animace bude přesností menší než pomocí matematické vzorce.  
  
 Kromě vytvoření vlastní funkce nejvýraznější dědění ze <xref:System.Windows.Media.Animation.EasingFunctionBase>, jedním z několika nejvýraznější funkce poskytované modulem runtime můžete vytvořit běžné účinky.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Odvolá pohybu animace mírně předtím, než začne animace v uvedené cestě.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Vytvoří skákající efekt.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Vytvoří které zrychluje nebo zpomaluje pomocí funkce kruhový animace.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Vytvoří animace, která se podobá pružiny, oscilační a zpět, dokud dojde na rest.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí exponenciální vzorce.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>p</sup> kde p rovná <xref:System.Windows.Media.Animation.PowerEase.Power%2A>vlastnost.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Vytvoří animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Vytvoření animace, která zrychluje a zpomaluje pomocí vzorce *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Vytvoří které zrychluje nebo zpomaluje pomocí vzorce sinus animace.  
  
 Chování tyto funkce usnadnění pomocí následující ukázky můžete prozkoumat.  
  
 [Tuto ukázku spustit](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 Chcete-li použít nejvýraznější funkce animace, použijte `EasingFunction` vlastnost animace určovat nejvýraznější funkce, která se týkají animace. Následující příklad se vztahuje <xref:System.Windows.Media.Animation.BounceEase> funkce k usnadnění <xref:System.Windows.Media.Animation.DoubleAnimation> vytvořit skákající efekt.  
  
 [Tuto ukázku spustit](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 V předchozím příkladu byla použita nejvýraznější funkce k From/k/podle animace. Tyto funkce usnadnění může platit taky pro animací jednotlivých klíč. Následující příklad ukazuje, jak používat klíčových snímků s usnadnění funkce, které jsou přidruženy k vytváření animace obdélník, který kontrakty směrem nahoru, zpomaluje, potom rozšíří dolů (jakoby návratem) a pak nedoručitelných zpráv na určeném místě.  
  
 [Tuto ukázku spustit](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Můžete použít <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> vlastnost pro úpravu nejvýraznější funkce chování, který je změnit, jak argument interpolaci animace. Existují tři možné hodnoty můžete udělit pro <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolace následuje matematický vzorec přidružené nejvýraznější funkce.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolace následuje interpolace 100 % minus výstup vzorce přidružené nejvýraznější funkce.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Používá interpolace <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pro první polovinu animace a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> pro druhou polovinu.  
  
 Grafy níže ukazují různé hodnoty <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> kde *f*(*x*) představuje animace průběhu a *t* představuje čas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Vlastnosti EasingMode funkce BackEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Vlastnosti EasingMode funkce BounceEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Vlastnosti EasingMode funkce CircleEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Vlastnosti EasingMode funkce CubicEase ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Funkce ElasticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Grafy funkce ExponentialEase různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Funkce QuarticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Funkce QuadraticEase s grafy různých režimů funkce Easing](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Funkce QuarticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Funkce QuinticEase s grafy různých režimů funkce Easing. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![Funkce SineEase pro různé hodnoty vlastnosti EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Můžete použít <xref:System.Windows.Media.Animation.PowerEase> vytvořit stejné chování jako <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, a <xref:System.Windows.Media.Animation.QuinticEase> pomocí <xref:System.Windows.Media.Animation.PowerEase.Power%2A> vlastnost. Například, pokud chcete použít <xref:System.Windows.Media.Animation.PowerEase> nahradit pro <xref:System.Windows.Media.Animation.CubicEase>, zadejte <xref:System.Windows.Media.Animation.PowerEase.Power%2A> hodnotu 3.  
  
 Kromě používání funkce usnadnění, které jsou součástí běhu, můžete vytvořit vlastní nejvýraznější funkce, která dědí z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Následující příklad ukazuje, jak vytvořit jednoduché vlastní nejvýraznější funkcí. Můžete přidat vlastní Matematická logika pro chování nejvýraznější funkce přepsáním <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metoda.  
  
 [Tuto ukázku spustit](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
