---
title: Přehled animace od na kým
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 9708a4d06e8a2aa65fb4d3bb959f4699237a2bc6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209148"
---
# <a name="fromtoby-animations-overview"></a>Přehled animace od/komu/kým
Toto téma popisuje způsob použití animace od/Komu/kým pro animaci vlastnosti závislosti. Od/Komu/kým animace vytvoří přechod mezi dvěma hodnotami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste se seznámit s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce animace. Úvod do funkce animace, najdete v článku [přehled animace](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Co je animace od/Komu/kým?  
 Od/Komu/kým animace je typ <xref:System.Windows.Media.Animation.AnimationTimeline> , který vytváří přechod mezi počáteční hodnotou a koncovou hodnotu. Množství času, který přijímá přechod k dokončení závisí <xref:System.Windows.Media.Animation.Timeline.Duration%2A> této animace.  
  
 Můžete použít od/Komu/kým animace vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard> značek a kódu, nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody v kódu. Animace From/To/By můžete také použít k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro jednu nebo více vlastností. Další informace o různých způsobech použití animací, najdete v článku [přehled způsobů animace vlastností](property-animation-techniques-overview.md).  
  
 Animace od/Komu/kým může mít maximálně dvě cílové hodnoty. Pokud budete potřebovat animaci, která má více než dvě cílové hodnoty, pomocí klíčových snímků animace. Animace klíčových snímků jsou popsány v [přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy animace od/Komu/kým  
 Protože animace hodnoty vlastností, existují jiné typy jiné vlastnosti. Animovat vlastnost, která přijímá <xref:System.Double>, například <xref:System.Windows.FrameworkElement.Width%2A> vlastnost elementu, použijte animaci, která vytváří <xref:System.Double> hodnoty. Animovat vlastnost, která přijímá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Animace od/Komu/kým třídy patřit do <xref:System.Windows.Media.Animation> obor názvů a použít následujícími zásadami vytváření názvů:  
  
 *\<Typ >* `Animation`  
  
 Kde  *\<typ >* je typ hodnoty, který animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje následující třídy animace od/Komu/kým.  
  
|Typ vlastnosti|Odpovídající od/Komu/kým třídy animace|  
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
 Od/Komu/kým animace vytvoří přechod mezi dvěma hodnotami Cíl. Je běžné nastavit počáteční hodnotu (nastavení s použitím <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost) a koncovou hodnotu (nastavení s použitím <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost). Ale můžete také zadat počáteční hodnotu, cílová hodnota nebo hodnoty posunu. Animace v těchto případech získává chybí cílová hodnota z vlastnost, která je právě animovat. Následující seznam popisuje různé způsoby, jak určit cílové hodnoty animace.  
  
-   **Počáteční hodnota**  
  
     Použití <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnosti, pokud chcete explicitně zadat počáteční hodnoty animace. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost samostatně nebo se <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> nebo <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost, přechody animace z této hodnoty na základní hodnotu animované vlastnosti.  
  
-   **Koncová hodnota**  
  
     Pokud chcete zadat koncovou hodnotu animace, použijte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost. Pokud používáte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost samostatně, animace získává svou výchozí hodnotu z vlastnosti, která je animované nebo z výstupu jiné animace, která se uplatňuje na stejnou vlastnost. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost spolu s <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost explicitně zadat počáteční a koncovou hodnotou pro animaci.  
  
-   **Hodnota posunu**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost umožňuje určit posun namísto explicitního počáteční nebo koncovou hodnotu pro animaci. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost animace Určuje, kolik animace používá změny hodnotu v průběhu jejího trvání. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost samostatně nebo se <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost. Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost animace přidá hodnotu posunu základní hodnoty vlastnosti nebo výstupní jiné animace.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Pomocí hodnoty od/Komu/kým  
 Následující části popisují způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti společně nebo samostatně.  
  
 Příklady v této části každé použití <xref:System.Windows.Media.Animation.DoubleAnimation>, což je typ od/Komu/kým animace, pro animaci <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> , který je 10 zařízeních nezávislých na pixelech vysoké a 100 zařízení nezávislé pixelů na šířku.  
  
 I když každý příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation>, od, Komu a kdo vlastnosti všech od/Komu/kým animace chovají identicky. I když každá z těchto příkladech se používá <xref:System.Windows.Media.Animation.Storyboard>, můžete použít animace od/Komu/kým jinými způsoby. Další informace najdete v tématu [přehled způsobů animace vlastností](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z/do  
 Při nastavení <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnoty animace postupuje od hodnoty, která je zadána společně <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> až 50 a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost 300. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Chcete-li  
 Při nastavení jenom <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost, animace postupuje od základní hodnotou animované vlastnosti nebo z výstupu skládání animace, která byla dříve nastavena na stejnou vlastnost na hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Vlastnost.  
  
 ("Vytváření animace" odkazuje na <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling> animaci, která dříve nastavena na stejnou vlastnost, která je stále v platnosti, když aktuální animace byla použita s použitím <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> chování při předání.)  
  
 Následující příklad nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 300. Protože nemá zadanou žádnou výchozí hodnotu, <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu (100) <xref:System.Windows.FrameworkElement.Width%2A> vlastnost jako svou výchozí hodnotu. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný od 100 do animace cílová hodnota 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Od společnosti  
 Při nastavení jenom <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost animace, animace postupuje od základní hodnoty, který je animované vlastnosti nebo z výstupu vytváření animací na součet dané hodnoty a hodnotu, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Vlastnost.  
  
 Následující příklad nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> do 300. Protože příklad neurčuje počáteční hodnotu <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost, 100, jako svou výchozí hodnotu. Koncová hodnota se určí tak, že přidáte <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnoty animace, 300, jeho počáteční hodnotu 100: 400. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Od/kým  
 Při nastavení <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, animace postupuje od hodnoty, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu, která je určená součtem <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> až 50 a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost 300. Koncová hodnota se určí tak, že přidáte <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hodnoty animace, 300, jeho počáteční hodnotu 50: 350. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>From  
 Pokud zadáte pouze <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> hodnoty animace, animace postupuje od hodnoty, která je zadána <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost, k základní hodnotě, která je animované vlastnosti nebo výstupní skládání animace.  
  
 Následující příklad nastaví jenom <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> na 50. Protože nemá zadanou žádnou koncovou hodnotu, <xref:System.Windows.Media.Animation.DoubleAnimation> používá základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost, 100, jako jeho koncovou hodnotu. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> je animovaný z 50 na základní hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Komu/kým  
 Nastavíte-li <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti animace, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost se ignoruje.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Jiné typy animací  
 Animace od/Komu/kým nejste pouze typ animace, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje: nabízí taky animace klíčových snímků a animace cesty.  
  
-   Animace klíčových snímků animuje podél libovolný počet cílové hodnoty popisují pomocí klíčových snímků. Další informace najdete v tématu [přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
-   Animace cesty vygeneruje výstupní hodnoty z <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [přehled animací cesty](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Můžete také vytvořit vlastní typy vlastní animace. Další informace najdete v tématu [Přehled vlastních animací](custom-animations-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animací cesty](path-animations-overview.md)
- [Přehled vlastních animací](custom-animations-overview.md)
- [Od, Komu a kdo ukázkové cílové hodnoty animace](https://go.microsoft.com/fwlink/?LinkID=159988)
