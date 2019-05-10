---
title: Přehled animací klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 5c0e574ea494bedc1c359d38cda0d17bbb03fcdf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645339"
---
# <a name="key-frame-animations-overview"></a>Přehled animací klíčových snímků
Toto téma vás seznámí s animací klíčových snímků. Animace klíčových snímků vám umožní pomocí více než dva cílových hodnot animace a řídit metodu interpolace animace společnosti.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Tento přehled informace o tom, měli byste se seznámit s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animace a časových os. Úvod do animace, najdete v článku [přehled animace](animation-overview.md). Pomáhá také se seznámit s animace od/Komu/kým. Další informace najdete v tématu Přehled animací From/To/By.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Co je animace klíčových snímků?  
 Od/Komu/kým, jako je hodnota vlastnosti cílové animuje animace klíčových snímků animace. Vytvoří přechod mezi jeho cílové hodnoty prostřednictvím jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Ale při od/Komu/kým animace vytvoří přechod mezi dvěma hodnotami, jeden animace klíčových snímků můžete vytvořit přechody mezi libovolný počet cílových hodnot. Na rozdíl od od/Komu/kým má animace klíčových snímků animace, bez From, pro nebo podle vlastností, pomocí kterého se má nastavit jeho cílové hodnoty. Cílových hodnot animace klíčových snímků jsou popsány pomocí klíčových snímků objektů (proto výraz, "animace klíčových snímků"). K určení cílových hodnot animace, můžete vytvořit klíčový snímek objekty a přidat je do animace <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekce. Při spuštění animace bude přecházet mezi snímky, které jste zadali.  
  
 Kromě podpory více cílových hodnot, některé metody klíčových snímků i podporují více metod interpolace. Metodu interpolace animace definuje, jak bude přecházet z jedné hodnoty na další. Existují tři typy interpolace: diskrétní lineární a splined.  
  
 Chcete-li animace pomocí klíčových snímků animace, proveďte následující kroky.  
  
- Deklarace animace a určit jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, stejně jako byste to udělali pro animace od/Komu/kým.  
  
- Pro každou cílovou hodnotu vytvořit klíčový snímek příslušného typu, nastavte ho na hodnotu a <xref:System.Windows.Media.Animation.KeyTime>a přidejte ho do animace <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekce.  
  
- Přidružit animaci vlastnosti, stejně jako byste to udělali s od/Komu/kým animace. Další informace o použití animace vlastnosti pomocí scénáře najdete v tématu [přehled scénářů](storyboards-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pro animaci <xref:System.Windows.Shapes.Rectangle> element do čtyř různých umístění.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Od/Komu/kým, jako je animace, animace klíčových snímků je použít na vlastnost s použitím <xref:System.Windows.Media.Animation.Storyboard> značek a kódu nebo s použitím <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody v kódu. Animace klíčových snímků můžete také použít k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro jednu nebo více vlastností. Další informace o různých způsobech použití animací, najdete v článku [přehled způsobů animace vlastností](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Typy animace klíčových snímků  
 Protože animace hodnoty vlastností, existují jiné typy jiné vlastnosti. Animovat vlastnost, která přijímá <xref:System.Double> (jako je například elementu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost), použijte animaci, která vytváří <xref:System.Double> hodnoty. Animovat vlastnost, která přijímá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Animace klíčových snímků třídy patřit do <xref:System.Windows.Media.Animation> obor názvů a dodržovat následujícími zásadami vytváření názvů:  
  
 *\<Typ >* `AnimationUsingKeyFrames`  
  
 Kde  *\<typ >* je typ hodnoty, který animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje následující třídy animace klíčových snímků.  
  
|Typ vlastnosti|Třída odpovídající animace od/Komu/kým|Podporované metody interpolace|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Diskrétní, lineární, Splined|  
  
<a name="animation_target_values"></a>   
## <a name="target-values-key-frames-and-key-times"></a>Cílové hodnoty (klíčových snímků) a časy klíč  
 Stejně jako existují různé typy animací klíčových snímků pro animaci vlastnosti různých typů, existují také různé typy objektů klíčový snímek: jeden pro každý typ hodnoty animace a metodu interpolace podporována. Klíčový snímek typy dodržovat následujícími zásadami vytváření názvů:  
  
 *\<InterpolationMethod >\<typ >* `KeyFrame`  
  
 Kde  *\<InterpolationMethod >* interpolace metoda používá klíčové rámečku a  *\<typ >* je typ hodnoty, který animuje třídy. Animace klíčových snímků, která podporuje všechny tři interpolace metody bude mít tři typy klíčový snímek, které můžete použít. Například můžete použít tři typy klíčový snímek s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, a <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (Interpolace metody jsou popsány podrobně v další části).  
  
 Hlavním účelem klíčový snímek je k určení <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Každý typ klíčový snímek poskytuje tyto dvě vlastnosti.  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Určuje vlastnost Cílová hodnota klíčových snímků.  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Vlastnost určuje, kdy (v rámci animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) klíčové rámečku <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> je dosaženo.  
  
 Po zahájení animace klíčových snímků iteruje její klíčové snímky v pořadí určeném parametrem jejich <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnosti.  
  
- Pokud neexistuje žádný klíčových snímků v čase 0, animace vytvoří přechod mezi aktuální hodnotu pro vlastnost target a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> první klíčové rámečku; v opačném případě animace výstupní hodnota se stane hodnotou první klíčové rámečku.  
  
- Animace vytvoří přechod mezi <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> z prvního a druhého klíčové snímky, metodou interpolace určené druhý klíčový snímek. Přechod začíná prvním klíčový snímek <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a končí, když druhé klíčové rámečku <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> je dosaženo.  
  
- Animace pokračuje, vytváření přechody mezi každé následné klíčového snímku a jeho předchozí klíčové rámečku.  
  
- Nakonec animace přechody hodnota klíčový snímek s časem na největší klíče, který se rovná nebo je menší, než se animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Pokud se animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> je <xref:System.Windows.Duration.Automatic%2A> nebo jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A> je roven času poslední klíčový snímek animace elementy end. Jinak, pokud se animace <xref:System.Windows.Duration> je větší než klíčovým momentem poslední klíčový snímek animace obsahuje hodnotu klíčového snímku, dokud ho dosáhne konce jeho <xref:System.Windows.Duration>. Podobně jako všechny animace klíčových snímků animace používá jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a určí, zda jej drží konečnou hodnotu dosáhne konce jeho aktivní období. Další informace najdete v tématu [přehled chování časování](timing-behaviors-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> objekt definovaný v předchozím příkladu k předvedení jak <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnosti práce.  
  
- Výstupní hodnoty animace první klíčové rámečku okamžitě nastaví na hodnotu 0.  
  
- Druhý klíčový snímek animuje od 0 do 350. Spustí po ukončení první klíčových snímků (v době = 0 sekund) a přehraje na 2 sekundy, koncové době = 0:0:2.  
  
- Třetí klíčový snímek animuje z 350 na 50. Začne při ukončení druhého klíčové rámečku (v době = 2 sekundy) a přehraje po dobu 5 sekund, koncové době = 0:0:7.  
  
- Čtvrtý klíčový snímek animuje z 50 na 200. Začne při ukončení třetí klíčových snímků (v době = 7 sekund) a přehraje na 1 sekundu koncové době = 0:0:8.  
  
- Vzhledem k tomu, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost animace byla nastavena na 10 sekund, animace uchovává svou poslední hodnotu 2 sekundy před koncové v době = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>Interpolace metody  
 V předchozích částech uvedeno, že některé animace klíčových snímků podporují více metod interpolace. Interpolace animace popisuje, jak animace přechody mezi hodnotami přes vlastnost duration. Výběrem typu klíčový snímek pomocí animace, můžete definovat metodu interpolace pro tento segment klíčový snímek. Existují tři různé typy metod interpolace: lineární, diskrétní a splined.  
  
### <a name="linear-interpolation"></a>Lineární interpolace  
 Pomocí lineární interpolace animace průběhu tempu trvání segmentu. Například, pokud segment klíčový snímek přechází od 0 do 10 průběhu 5 sekund, animace bude výstup následujících hodnot v zadaném časy:  
  
|Time|Výstupní hodnota|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Diskrétní interpolace  
 Diskrétní interpolace animace funkce přejde z jednu hodnotu na další bez interpolace. Pokud segment klíčový snímek přechází od 0 do 10 průběhu 5 sekund, animace bude výstup následujících hodnot v zadaném časy:  
  
|Time|Výstupní hodnota|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Všimněte si, jak animace nezmění jeho výstupní hodnoty do konce velmi trvání segmentu.  
  
 Splined interpolace je složitější. Je popsané v další části.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Splined interpolace  
 Splined interpolace lze použít k dosažení víc odpovídají realitě účinky časování. Protože animace se proto často používají k napodobují efekty, ke kterým dochází v reálném světě, vývojáři může potřebovat jemné ovládací prvek zrychlení a zpomalení objektů a zavřete manipulaci s časování segmentů. Klíčové snímky SpLine umožňují splined interpolace animace. U dalších klíčových snímků, můžete zadat <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. U křivkový klíčový snímek, můžete také zadat <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. Následující příklad ukazuje klíčové rámečku jedné křivky pro <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Všimněte si, že <xref:System.Windows.Media.Animation.KeySpline> vlastnost; díky liší od ostatních typů klíčové snímky spline klíčový snímek.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Kubické Bézierovy křivky je definován tak, že počáteční bod, koncový bod a dva ovládací prvek body. <xref:System.Windows.Media.Animation.KeySpline> Vlastnost klíčové rámečku křivkový definuje dva řídicí bod Bézierovy křivky, který vede od (0; 0) na (1,1). Určuje první řídicí bod křivky faktor v první polovině roku Bézierovu křivku, a druhý řídicí bod řídí faktor křivky v druhé polovině segmentu Bézierovy křivky. Výsledný křivky popisuje rychlost změny pro klíčový rámec tohoto křivky. Tím strmější křivku, tím rychleji klíčový snímek změní jeho hodnoty. Protože křivka získá plošší, klíčové rámečku změní jeho hodnoty pomaleji.  
  
 Můžete použít <xref:System.Windows.Media.Animation.KeySpline> chcete simulovat fyzické trajektorie jako spadající vody nebo kuličky nebo použít jiné "usnadnění v" a "doběhu" efekty animace pohybu. Pro efekty interakce uživatele jako pozadí pomalu nebo ovládací prvek tlačítko odrazu můžete použít splined interpolace urychlit nebo zpomalit rychlost změny pro animaci určitým způsobem.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> 0,1 1,0, která vytvoří následující Bézierovu křivku.  
  
 ![Bézierovy křivky](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Klíče křivky pomocí kontrolních bodů (0.0; 1.0) a (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Toto klíčové rámečku animuje rychle při jeho začíná, může zpomalit a potom zrychluje znovu předtím, než ho ukončí.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> z 0.5,0.25 0.75,1.0, která vytvoří následující Bézierovu křivku.  
  
 ![Bézierovy křivky](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Klíče křivky s ovládacím prvkem body (0,25; 0,5) a (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Protože zaoblení Bézierovu křivku mění velmi malý, tento klíčový snímek animuje téměř konstantní rychlostí; To může zpomalit trochu směrem k velmi ukončení.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pro animaci pozici obdélníku. Vzhledem k tomu, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> používá <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> objekty, přechod mezi každou hodnotu klíčového snímku používá splined interpolace.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Splined interpolace může být obtížné porozumět; pomůže experimentovat s různými nastaveními. [Ukázkové animace křivkový klíč](https://go.microsoft.com/fwlink/?LinkID=160011) vám umožní změnit hodnoty klíče křivky a zobrazit výsledek na animace.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>Kombinování interpolace metody  
 Můžete pomocí interpolace různé typy v jeden klíčový snímek animace klíčových snímků. Když dva animace klíčových snímků s jinou interpolace za sebou, metodu interpolace druhé klíčové rámečku slouží k vytvoření přechodu z první hodnoty na druhý.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> vytvoření této interpolace lineární splined a diskrétní používá.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Další informace o době trvání a časy klíče  
 Stejně jako jiné animace klíčových snímků animace mít <xref:System.Windows.Duration> vlastnost. Kromě zadání animace <xref:System.Windows.Duration>, je třeba zadat, jaká část tento čas dostane na každý klíčový snímek. To provedete tak, že s popisem <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pro každou animace klíčových snímků. Každý klíčový snímek <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> určuje po ukončení tohoto klíčové rámečku.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Vlastnost neurčuje, jak dlouho hraje klíčovým momentem. Množství času, které hraje klíčový snímek je určeno po ukončení klíčový snímek, ukončení předchozí klíčový snímek a doba trvání animace. Klíče časy může být zadané jako hodnotu času v procentech nebo jako speciální hodnoty <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Následující seznam popisuje různé způsoby určení klíče časy.  
  
### <a name="timespan-values"></a>Hodnoty TimeSpan  
 Můžete zadat <xref:System.TimeSpan> hodnoty k určení <xref:System.Windows.Media.Animation.KeyTime>. Hodnota by měla být větší než nebo rovna 0 a menší než doba trvání animace. Následující příklad ukazuje s určitou dobou trvání animace 10 sekund a čtyři klíčové snímky, jejichž klíče časy specifikované hodnoty času.  
  
- První klíčové rámečku animuje od základní hodnoty 100 přes první 3 sekundy, koncové době = 0:0:03.  
  
- Druhý klíčový snímek animuje ze 100 na 200. Spustí po ukončení první klíčových snímků (v době = 3 sekund) a přehraje po dobu 5 sekund, koncové době = 0:0:8.  
  
- Třetí klíčový snímek animuje z hodnoty 200 na 500. Začne při ukončení druhého klíčové rámečku (v době = 8 sekund) a přehraje na 1 sekundu koncové době = 0:0:9.  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Začne při ukončení třetí klíčových snímků (v době = 9 sekund) a přehraje na 1 sekundu koncové době = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Procento hodnoty  
 Procentuální hodnota určuje, že klíčový snímek končí určité procento animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zadejte procento jako čísla následované `%` symbol. V kódu, můžete použít <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> metoda a předat ji <xref:System.Double> procentuální hodnota. Hodnota musí být větší než nebo rovna 0 a menší nebo rovna 100 procent. Následující příklad ukazuje s určitou dobou trvání animace 10 sekund a čtyři klíčové snímky, jejichž klíče časy jsou určené jako procenta.  
  
- První klíčové rámečku animuje od základní hodnoty 100 přes první 3 sekundy, koncové době = 0:0:3.  
  
- Druhý klíčový snímek animuje ze 100 na 200. Spustí po ukončení první klíčových snímků (v době = 3 sekund) a přehraje po dobu 5 sekund, koncové době = 0:0:8 (0,8 * 10 = 8).  
  
- Třetí klíčový snímek animuje z hodnoty 200 na 500. Začne při ukončení druhého klíčové rámečku (v době = 8 sekund) a přehraje na 1 sekundu koncové době = 0:0:9 (0.9 * 10 = 9).  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Začne při ukončení třetí klíčových snímků (v době = 9 sekund) a přehraje na 1 sekundu koncové době = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Zvláštní hodnota, Uniform  
 Použití <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> časování, pokud chcete, aby každý klíčový rámec stejné množství času se.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> dostupný čas klíčovým momentem stejně vydělí počtem klíčových snímků určit čas ukončení každý klíčový snímek. Následující příklad ukazuje animace s určitou dobou trvání 10 sekund a čtyři klíčové snímky krát jejichž klíče jsou zadány jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
- První klíčové rámečku animuje od základní hodnoty 100 nad prvních 2,5 sekund koncové době = 0:0:2.5.  
  
- Druhý klíčový snímek animuje ze 100 na 200. Spustí po ukončení první klíčových snímků (v době = 2,5 sekund) a přehraje přibližně 2,5 sekund koncové době = 0:0:5.  
  
- Třetí klíčový snímek animuje z hodnoty 200 na 500. Začne při ukončení druhého klíčové rámečku (v době = 5 sekund) a přehraje 2,5 sekund koncové době = 0:0:7.5.  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Začne při ukončení druhého klíčové rámečku (v době = 7.5 sekund) a přehraje 2,5 sekund koncové době = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Zvláštní hodnota tempem  
 Použití <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> časování, pokud chcete animovat tempu.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> klíčovým momentem přiděluje čas dostupnosti podle délku každého klíčové snímky k určení doby trvání jednotlivých snímků.  Získají tak chování rychlost nebo rychlost animace zůstává konstantní.  Následující příklad ukazuje animace s určitou dobou trvání 10 sekund a tří klíčových snímků krát jejichž klíče jsou zadány jako <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Všimněte si, že pokud je klíčovým momentem poslední klíčové rámečku <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, nastaví se jeho vyřešení klíčovým momentem do 100 procent. Pokud je první klíče snímek s více snímky animace tempem, jeho vyřešení klíčovým momentem se nastaví na hodnotu 0. (Pokud klíčový rámec kolekce obsahuje pouze jeden klíčový snímek a je tempem klíčový snímek, jeho vyřešení klíčovým momentem se nastavit na 100 procent.)  
  
 Různých klíčových snímků v rámci jednoho klíčového snímku animace může pomocí různých klíčovým momentem typů.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Kombinace klíče časy, snímků klíče mimo pořadí  
 Použitím klíčových snímků můžete použít s různými <xref:System.Windows.Media.Animation.KeyTime> typů ve stejném animace hodnot. A i když se doporučuje, přidejte klíčové snímky v pořadí, ve kterém by měl přehrát, není nutné. Animace a časování systém je dokáže řešení mimo pořadí klíčových snímků. Klíčové snímky pomocí neplatné klíče časy jsou ignorovány.  
  
 Následující seznam popisuje postup, kterým jsou klíče časy pro klíčové snímky animace klíčových snímků.  
  
1. Vyřešit <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
2. Určit, animace *celkový čas interpolace*, celkový čas potřebný animace klíčových snímků dokončete dopředné iterace.  
  
    1. Pokud se animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> není <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>, interpolace celkový čas je hodnota animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost.  
  
    2. V opačném případě je největší interpolace celkový čas <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> hodnotu zadanou mezi klíčové snímky, pokud nějaké existují.  
  
    3. V opačném případě interpolace celkový čas je 1 sekunda.  
  
3. Celkový počet interpolace časovou hodnotu použijte k vyřešení <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
4. Vyřešit poslední klíčový snímek, je-li se už vyřešené v předchozích krocích. Pokud <xref:System.Windows.Media.Animation.KeyTime> posledního klíčového snímku je <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, jeho vyřešení čas bude rovnat interpolace celkový čas.  
  
     Pokud <xref:System.Windows.Media.Animation.KeyTime> první klíčové rámečku je <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> a tuto animaci má více než pro klíčové snímky vyřešit jeho <xref:System.Windows.Media.Animation.KeyTime> hodnotu nula, pokud existuje pouze jeden klíčový snímek a jeho <xref:System.Windows.Media.Animation.KeyTime> hodnotu <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, je přeložen na celkový počet čas umožňuje stručně popsat, jak je popsáno v předchozím kroku.  
  
5. Vyřešit zbývající <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty:, každý získá stejný podíl času dostupnosti.  Během tohoto procesu nevyřešené <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty jsou dočasně považovány za <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty a získat dočasný přeložit čas.  
  
6. Vyřešit <xref:System.Windows.Media.Animation.KeyTime> hodnoty použitím klíčových snímků s použitím klíčových snímků nejbližší je deklarovaná, které byly vyřešeny nespecifikované klíče časy <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
7. Vyřešit zbývající <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> použít <xref:System.Windows.Media.Animation.KeyTime> hodnoty sousedních klíčové snímky k určení doby jejich vyřešení.  Cílem je zajistit, aby rychlosti animace konstantní přeložit době klíčový snímek.  
  
8. Řazení klíčových snímků v pořadí doby vyřešení (primární klíč) a pořadí deklarace (sekundární klíč), to znamená, použijte stabilní řazení podle přeložit klíčový snímek <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Ukázka animace klíčových křivky](https://go.microsoft.com/fwlink/?LinkID=160011)
- [Ukázka animace klíčových snímků](https://go.microsoft.com/fwlink/?LinkID=160012)
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
- [Přehled chování časování](timing-behaviors-overview.md)
