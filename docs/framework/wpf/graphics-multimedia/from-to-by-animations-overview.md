---
title: "Z na podle animací – přehled"
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
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5eba773a290f1100fcea411919c5c16558e01ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fromtoby-animations-overview"></a>Přehled animace od/komu/kým
Toto téma popisuje, jak použít z/do nebo podle animací pro animaci vlastností závislostí. From/k/podle animace vytvoří přechod mezi dvěma hodnotami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce animace. Úvod do animace funkce, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Co je animace z/do nebo podle?  
 From/k/podle animace je typ <xref:System.Windows.Media.Animation.AnimationTimeline> vytvářející přechod mezi hodnotu počáteční a koncovou hodnotu. Množství času, který přechodu potřebné k dokončení je dáno <xref:System.Windows.Media.Animation.Timeline.Duration%2A> této animace.  
  
 Můžete použít i From/k/animace do vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard> v značek a kódu, nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda v kódu. Můžete také používat animace From/To/By vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použít ji na jeden nebo více vlastností. Další informace o různých způsobech použití animace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
 Z/do nebo podle animací může mít více než dvě cílové hodnoty. Pokud budete potřebovat animace, která má více než dvě cílové hodnoty, použijte klíč rámce animace. Animací jednotlivých klíč jsou popsány v [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy z/do nebo podle animace  
 Protože animací generovat hodnoty vlastností, existují různé animace typy pro typy jinou vlastnost. Pro animaci vlastnost, která přebírá <xref:System.Double>, například <xref:System.Windows.FrameworkElement.Width%2A> vlastnost elementu, použijte animace, která vytváří <xref:System.Double> hodnoty. Pro vlastnost, která přebírá animaci <xref:System.Windows.Point>, použijte animace, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Animace z/do nebo pomocí třídy patří do <xref:System.Windows.Media.Animation> obor názvů a použijte následující konvence:  
  
 *\<Typ >*`Animation`  
  
 Kde  *\<typ >* je typ hodnoty, které animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující třídy animace z/do nebo podle.  
  
|Typ vlastnosti|Odpovídající z/do nebo pomocí třídy animace|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## <a name="target-values"></a>Cílové hodnoty  
 From/k/podle animace vytvoří přechod mezi dvě cílové hodnoty. Je běžné, můžete zadat počáteční hodnotu (nastavit pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost) a koncovou hodnotu (nastavit pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost). Můžete však také zadat jenom výchozí hodnotu, hodnotu cílové nebo hodnoty posunu. V těchto případech animace získá chybí hodnota cíle z vlastnosti, který je právě animace. Následující seznam popisuje různé způsoby, jak zadat cílové hodnoty animace.  
  
-   **Počáteční hodnota**  
  
     Použití <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost, pokud chcete explicitně zadat výchozí hodnotu animace. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost samostatně, nebo se <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> nebo <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost, přechody animace z této hodnoty na základní hodnotu animovaný vlastnosti.  
  
-   **Koncová hodnota**  
  
     Pokud chcete zadat koncovou hodnotu animace, použijte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost. Pokud použijete <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost samostatně animace získá jeho výchozí hodnotu z vlastnosti, který je právě animovaný nebo z výstupu jiné animace, který se použije pro stejnou vlastnost. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost společně s <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost explicitně zadat počáteční a koncové hodnoty pro animaci.  
  
-   **Hodnota posunutí**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost umožňuje určit posun místo explicitní počáteční nebo koncová hodnota pro animaci. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost animace Určuje, kolik animace změní hodnotu přes jeho trvání. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost samostatně nebo pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost animace přidá hodnota posunutí hodnotu vlastnosti nebo výstup jiné animace.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Pomocí z/do nebo podle hodnot  
 Následující části popisují způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti společně nebo samostatně.  
  
 Příklady v tomto oddílu každý používají <xref:System.Windows.Media.Animation.DoubleAnimation>, který je typem ze/k/podle animace, použije animaci <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> 10 vysoké nezávislé pixelů zařízení a 100 zařízení nezávislé pixelů.  
  
 I když každý příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation>, od, k a vlastnosti všech From/k/podle animace chovají stejně jako. I když každá z těchto příkladech používá <xref:System.Windows.Media.Animation.Storyboard>, můžete použít z/do nebo podle animací jinými způsoby. Další informace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z/do  
 Když nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnoty společně animace postupuje od hodnoty, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.  
  
 Následující příklad nastavuje <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> na 50 a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost 300. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Chcete-li  
 Když nastavíte jenom <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost, animace postupuje od základní hodnoty vlastnost animovaný nebo z výstupu skládání animace, která již byla použita pro stejnou vlastnost na hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Vlastnost.  
  
 ("Skládání animace" odkazuje <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling> animace, které dříve použito pro stejnou vlastnost, která je stále v platnosti, když aktuální animace byla použita pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> chování aby handoff.)  
  
 V následujícím příkladu se nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 300. Vzhledem k tomu, že nebyla určena žádná výchozí hodnota, <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu (100) <xref:System.Windows.FrameworkElement.Width%2A> vlastnost jako jeho výchozí hodnotu. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný od 100 na cílovou hodnotu animace 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Pomocí  
 Když nastavíte jenom <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost animace, animace postupuje od základní hodnoty vlastnosti, která je právě animovaný nebo z výstupu skládání animace součtem tuto hodnotu a hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost.  
  
 V následujícím příkladu se nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 300. Vzhledem k tomu, že v příkladu neurčuje počáteční hodnotu, <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost, 100, jako jeho výchozí hodnotu. Koncová hodnota je určen přidáním <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnotu animace, 300, na jeho výchozí hodnotu 100:400. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Z nebo podle  
 Když nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, animace postupuje od hodnoty, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu, která je zadána součet <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.  
  
 Následující příklad nastavuje <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> na 50 a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost 300. Koncová hodnota je určen přidáním <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnotu animace, 300, na jeho výchozí hodnotu 50:350. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>From  
 Pokud zadáte jenom <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> hodnotu animace, animace postupuje od hodnoty, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu vlastnosti, která je právě animovaný nebo na výstup skládání animace.  
  
 V následujícím příkladu se nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> na 50. Vzhledem k tomu, že nebyla určena žádná koncová hodnota, <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost, 100, jako jeho koncovou hodnotu. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>K/podle  
 Nastavíte-li <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost je ignorována.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Jiné typy animace  
 Z/do nebo podle animací nejsou jediným typem animací, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje: Poskytuje taky animací jednotlivých klíč a animací cestu.  
  
-   Klíč rámce animace animuje podél libovolný počet cílové hodnoty, popisuje použití klíčových snímků. Další informace najdete v tématu [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   Cesta animace generuje hodnoty výstup z <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [cesta animací přehled](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Můžete také vytvořit vlastní animace typy. Další informace najdete v tématu [vlastní animace přehled](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Přehled animací cesta](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Přehled vlastní animace](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [Z, k a ukázkové hodnoty Target animace](http://go.microsoft.com/fwlink/?LinkID=159988)
