---
title: Přehled animací od od do posazení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186453"
---
# <a name="fromtoby-animations-overview"></a>Přehled animace od/komu/kým
Toto téma popisuje, jak používat animace Od/Do/Podle k animaci vlastností závislostí. A From/To/By animace vytvoří přechod mezi dvěma hodnotami.  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste být obeznámeni s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcemi animací. Úvod k funkcím animace najdete v tématu [Přehled animací](animation-overview.md).  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>Co je animace od/do/podle?  
 A From/To/By animace je <xref:System.Windows.Media.Animation.AnimationTimeline> typ, který vytváří přechod mezi počáteční hodnotou a koncovou hodnotou. Množství času, který trvá dokončení přechodu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> je určena této animace.  
  
 Můžete použít From/To/By animace na vlastnost <xref:System.Windows.Media.Animation.Storyboard> pomocí v značky a kód, nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody v kódu. Můžete také použít From/To/By Animace <xref:System.Windows.Media.Animation.AnimationClock> k vytvoření a použít ji na jednu nebo více vlastností. Další informace o různých metodách použití animací naleznete v [tématu Přehled technik animace vlastností](property-animation-techniques-overview.md).  
  
 Animace od/do/podle mohou mít maximálně dvě cílové hodnoty. Pokud požadujete animaci, která má více než dvě cílové hodnoty, použijte animaci klíčových snímků. Animace klíčových snímků jsou popsány v [přehledu animací klíčových snímků](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>Typy animací od/do/podle  
 Vzhledem k tomu, že animace generují hodnoty vlastností, existují různé typy animací pro různé typy vlastností. Chcete-li animovat <xref:System.Double>vlastnost, která <xref:System.Windows.FrameworkElement.Width%2A> trvá , například vlastnost prvku, použijte animaci, která vytváří <xref:System.Double> hodnoty. Chcete-li animovat <xref:System.Windows.Point>vlastnost, která trvá <xref:System.Windows.Point> , použijte animaci, která vytváří hodnoty a tak dále.  
  
 Třídy animací Od/Do/Podle patří do oboru <xref:System.Windows.Media.Animation> názvů a používají následující konvence pojmenování:  
  
 * \<Typ>*`Animation`  
  
 Kde * \<Type>* je typ hodnoty, kterou třída animuje.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující třídy animace Od/Do/Podle.  
  
|Typ vlastnosti|Odpovídající třída animace Od/Do/Podle|  
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
 A From/To/By animace vytvoří přechod mezi dvěma cílovými hodnotami. Je běžné zadat počáteční hodnotu (nastavte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ji pomocí vlastnosti) a koncovou <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnotu (nastavte ji pomocí vlastnosti). Můžete však také zadat pouze počáteční hodnotu, cílovou hodnotu nebo hodnotu odsazení. V těchto případech animace získá chybějící cílovou hodnotu z vlastnosti, která je právě animována. Následující seznam popisuje různé způsoby určení cílových hodnot animace.  
  
- **Počáteční hodnota**  
  
     Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> použijte, pokud chcete explicitně zadat počáteční hodnotu animace. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost samostatně, nebo <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> s <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastností nebo. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost, animace přechody z této hodnoty na základní hodnotu animované vlastnosti.  
  
- **Koncová hodnota**  
  
     Chcete-li určit koncovou hodnotu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> animace, použijte její vlastnost. Pokud použijete <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost samostatně, animace získá počáteční hodnotu z vlastnosti, která je právě animována nebo z výstupu jiné animace, která je použita na stejnou vlastnost. <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Vlastnost spolu s vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> můžete explicitně určit počáteční a koncové hodnoty animace.  
  
- **Hodnota posunu**  
  
     Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> umožňuje zadat posun namísto explicitní počáteční nebo koncová hodnota animace. Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animace určuje, jak moc animace změní hodnotu v průběhu jeho trvání. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost sám nebo <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> s vlastností. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost, animace přidá hodnotu posunu k základní hodnotě vlastnosti nebo k výstupu jiné animace.  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>Použití hodnot od/do/podle  
 Následující části popisují použití <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> , a vlastnosti společně nebo samostatně.  
  
 Příklady v této části <xref:System.Windows.Media.Animation.DoubleAnimation>každý použít , což je typ From/To/By <xref:System.Windows.FrameworkElement.Width%2A> animace, <xref:System.Windows.Shapes.Rectangle> animovat vlastnost, která je 10 pixelů nezávislých na zařízení vysoké a 100 zařízení nezávislé pixelů široký.  
  
 Přestože každý <xref:System.Windows.Media.Animation.DoubleAnimation>příklad používá , Od, Do a Podle vlastnosti všech From/To/By animace se chovají stejně. Přestože každý z těchto <xref:System.Windows.Media.Animation.Storyboard>příkladů používá , můžete použít From/To/By animace jinými způsoby. Další informace naleznete v [tématu Property Animation Techniques Overview](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Od/do  
 Když <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnoty a společně, animace postupuje z hodnoty, která je určena <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností, na hodnotu, která je určena <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastností.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 50 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> a jeho vlastnost 300. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Akce  
 Pokud nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> pouze vlastnost, animace postupuje ze základní hodnoty animované vlastnosti nebo z výstupu animace, která byla dříve použita na <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> stejnou vlastnost, na hodnotu, která je určena vlastností.  
  
 ("Skládání animace" odkazuje <xref:System.Windows.Media.Animation.ClockState.Active> na <xref:System.Windows.Media.Animation.ClockState.Filling> nebo animace, které dříve použity na stejnou vlastnost, která <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> je stále v platnosti, když byla použita aktuální animace pomocí chování předání.)  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> pouze <xref:System.Windows.Media.Animation.DoubleAnimation> vlastnost do 300. Vzhledem k tomu, <xref:System.Windows.Media.Animation.DoubleAnimation> že nebyla zadána žádná počáteční <xref:System.Windows.FrameworkElement.Width%2A> hodnota, použije základní hodnota (100) vlastnosti jako počáteční hodnotu. <xref:System.Windows.Shapes.Rectangle> Je <xref:System.Windows.FrameworkElement.Width%2A> animovaný od 100 do animace cílovou hodnotu 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Od  
 Pokud nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> pouze vlastnost animace, animace postupuje od základní hodnoty vlastnosti, která je právě animována, nebo z výstupu animace skládání <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> na součet této hodnoty a hodnotu, která je určena vlastností.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> pouze <xref:System.Windows.Media.Animation.DoubleAnimation> vlastnost do 300. Vzhledem k tomu, že příklad <xref:System.Windows.Media.Animation.DoubleAnimation> neurčuje počáteční <xref:System.Windows.FrameworkElement.Width%2A> hodnotu, použije základní hodnotu vlastnosti 100 jako počáteční hodnotu. Koncová hodnota je určena <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> přidáním hodnoty animace, 300, k jeho počáteční hodnotě 100: 400. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> je animovaný ze 100 na 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Od/podle  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Když nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti a animace, animace postupuje z hodnoty, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> která je určena vlastností, na <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> hodnotu, která je určena součtem vlastností a. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 50 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> a jeho vlastnost 300. Koncová hodnota je určena <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> přidáním hodnoty animace, 300, k jeho počáteční hodnotě, 50: 350. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>From  
 Zadáte-li pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> hodnotu animace, animace postupuje z hodnoty, která <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> je určena vlastností, na základní hodnotu vlastnosti, která je právě animována nebo výstup animace skládání.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> pouze <xref:System.Windows.Media.Animation.DoubleAnimation> vlastnost do 50. Vzhledem k tomu, <xref:System.Windows.Media.Animation.DoubleAnimation> že nebyla zadána žádná koncová hodnota, použije základní hodnota <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti 100 jako koncovou hodnotu. The <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný od 50 do <xref:System.Windows.FrameworkElement.Width%2A> základní hodnoty nemovitosti, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Do/podle  
 Pokud nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost je ignorována.  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>Jiné typy animací  
 Animace Od/Do/Podle nejsou jediným typem animací, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje: poskytuje také animace klíčových snímků a animace cest.  
  
- Animace klíčových snímků animuje libovolný počet cílových hodnot popsaných pomocí klíčových snímků. Další informace naleznete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
- Animace cesty generuje výstupní hodnoty <xref:System.Windows.Media.PathGeometry>z . Další informace naleznete v tématu [Path Animations Overview](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také umožňuje vytvářet vlastní typy animací. Další informace naleznete v tématu [Přehled vlastních animací](custom-animations-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animací cesty](path-animations-overview.md)
- [Přehled vlastních animací](custom-animations-overview.md)
- [Ukázka cílových hodnot od, do a podle animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
