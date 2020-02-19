---
title: Přehled animací na základě
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448997"
---
# <a name="fromtoby-animations-overview"></a>Přehled animace od/komu/kým
V tomto tématu se dozvíte, jak použít animace z/na/pomocí animací k animování vlastností závislosti. Animace od/do/podle vytvoří přechod mezi dvěma hodnotami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Předpoklady  
 Pro pochopení tohoto tématu byste měli být obeznámeni s funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací. Úvod k funkcím animace najdete v tématu [Přehled animace](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Co je animace od/do/po?  
 Animace od/do/podle je typ <xref:System.Windows.Media.Animation.AnimationTimeline>, který vytvoří přechod mezi počáteční a koncovou hodnotou. Doba, po kterou trvá přechod dokončený, je určená <xref:System.Windows.Media.Animation.Timeline.Duration%2A> této animace.  
  
 Můžete použít animaci z/na/na vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard> v kódu a kódu nebo pomocí metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> v kódu. Můžete také použít animaci od/k/podle k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro jednu nebo více vlastností. Další informace o různých metodách použití animací naleznete v tématu [Přehled postupů animace vlastností](property-animation-techniques-overview.md).  
  
 Z animací z/do/by nemůžou mít víc než dvě cílové hodnoty. Pokud potřebujete animaci, která má více než dvě cílové hodnoty, použijte animaci klíčových snímků. Animace klíčových snímků jsou popsané v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy animací od/k/podle  
 Vzhledem k tomu, že animace generují hodnoty vlastností, existují různé typy animací pro různé typy vlastností. Chcete-li animovat vlastnost, která přebírá <xref:System.Double>, jako je například vlastnost <xref:System.Windows.FrameworkElement.Width%2A> elementu, použijte animaci, která vytvoří <xref:System.Double> hodnoty. Chcete-li animovat vlastnost, která přebírá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty atd.  
  
 Třídy animace od/do/podle patří do oboru názvů <xref:System.Windows.Media.Animation> a používají následující konvence pojmenování:  
  
 *typ\<>* `Animation`  
  
 Kde *\<typ >* je typ hodnoty, kterou třída animuje.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje následující třídy animace od/do/.  
  
|Typ vlastnosti|Odpovídající třída animace od/do/podle|  
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
 Animace od/do/podle vytvoří přechod mezi dvěma cílovými hodnotami. Je běžné zadat počáteční hodnotu (nastavte ji pomocí vlastnosti <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>) a koncovou hodnotu (nastavte ji pomocí vlastnosti <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>). Můžete ale také zadat pouze počáteční hodnotu, cílovou hodnotu nebo hodnotu posunu. V těchto případech animace získá chybějící cílovou hodnotu z vlastnosti, která je animovaná. Následující seznam popisuje různé způsoby, jak určit cílové hodnoty animace.  
  
- **Počáteční hodnota**  
  
     Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> použijte, pokud chcete explicitně zadat počáteční hodnotu animace. Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> lze použít samostatně nebo s vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> nebo <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Zadáte-li pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, animace přechází z této hodnoty na základní hodnotu animované vlastnosti.  
  
- **Koncová hodnota**  
  
     Chcete-li zadat koncovou hodnotu animace, použijte její vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>. Použijete-li vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> samostatně, animace získá svoji počáteční hodnotu z vlastnosti, která je animována nebo z výstupu jiné animace, která je použita na stejnou vlastnost. Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> spolu s vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> můžete použít k explicitnímu zadání počátečních a koncových hodnot pro animaci.  
  
- **Hodnota posunu**  
  
     Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> umožňuje zadat posun místo explicitní počáteční nebo koncové hodnoty pro animaci. Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animace určuje, kolik animace mění hodnotu v průběhu doby trvání. Vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> můžete použít samostatně nebo s vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Zadáte-li pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, animace přidá hodnotu posunu k základní hodnotě vlastnosti nebo výstupu jiné animace.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Použití hodnot z/na/podle  
 Následující části popisují, jak používat vlastnosti <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> společně nebo samostatně.  
  
 Příklady v této části používají <xref:System.Windows.Media.Animation.DoubleAnimation>, což je typ animace od/do/podle, který slouží k animování <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti <xref:System.Windows.Shapes.Rectangle>, která je na šířku nezávisle na zařízení s vysokou úrovní rozlišení a 100 pixelů.  
  
 Přestože každý příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation>, je z, do a podle vlastností všech animací z/do/podle stejného chování. I když každý z těchto příkladů používá <xref:System.Windows.Media.Animation.Storyboard>, můžete použít animace z/do/pomocí jiných způsobů. Další informace naleznete v tématu [Přehled technik animace vlastností](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z/na  
 Když nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnoty společně, animace pokračuje z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na hodnotu zadanou vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 Následující příklad nastaví vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 50 a jeho vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> na 300. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> animovaný z 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Akce  
 Když nastavíte pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, animace bude postupovat ze základní hodnoty animované vlastnosti nebo z výstupu sestavování animace, která byla dříve použita u stejné vlastnosti, na hodnotu zadanou vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 ("Animace sestavování" odkazuje na <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling> animaci, která se dřív použila u stejné vlastnosti, která je stále v platnosti, když se aktuální animace použila při použití <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> chování.)  
  
 Následující příklad nastaví pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 300. Vzhledem k tomu, že nebyla zadána žádná počáteční hodnota, používá <xref:System.Windows.Media.Animation.DoubleAnimation> jako počáteční hodnotu základní hodnotu (100) vlastnosti <xref:System.Windows.FrameworkElement.Width%2A>. <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> je animována z 100 na cílovou hodnotu animace 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Od společnosti  
 Když nastavíte pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animace, animace pokračuje ze základní hodnoty vlastnosti, která je animovaná, nebo z výstupu sestavování animace součtu hodnoty a hodnoty, která je určena vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 Následující příklad nastaví pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 300. Vzhledem k tomu, že příklad neurčuje počáteční hodnotu, používá <xref:System.Windows.Media.Animation.DoubleAnimation> základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti 100 jako počáteční hodnotu. Koncová hodnota je určena přidáním <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnoty animace (300) do počáteční hodnoty 100:400. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> animovaný z 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Od/po  
 Při nastavování vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animace pokračuje animace z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na hodnotu, která je určena součtem vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 Následující příklad nastaví vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 50 a jeho vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> na 300. Koncová hodnota je určena přidáním <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnoty animace (300) do počáteční hodnoty 50:350. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> animovaný z 50 do 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Z  
 Když zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> hodnotu animace, animace pokračuje z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, na základní hodnotu vlastnosti, která je animovaná nebo výstupem animace skládání.  
  
 Následující příklad nastaví pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 50. Vzhledem k tomu, že nebyla zadána koncová hodnota, používá <xref:System.Windows.Media.Animation.DoubleAnimation> jako koncovou hodnotu základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti 100. <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> je animována z 50 na základní hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Do/podle  
 Pokud nastavíte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> se ignoruje.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Další typy animací  
 Z animací z/do/by neexistují jediné typy animací, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují: také poskytuje animace klíčových snímků a animace cest.  
  
- Animace klíčových snímků se animuje spolu s libovolným počtem cílových hodnot popsaných pomocí klíčových snímků. Další informace najdete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
- Animace cest generuje výstupní hodnoty z <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [Přehled animací cest](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také umožňuje vytvářet vlastní typy animací. Další informace najdete v tématu [Přehled vlastních animací](custom-animations-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animací cesty](path-animations-overview.md)
- [Přehled vlastních animací](custom-animations-overview.md)
- [Ukázka cílových hodnot z, do a podle animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
