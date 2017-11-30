---
title: "Přehled animací klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c4f4179087679ff891c705cf16693fc69c808d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="key-frame-animations-overview"></a>Přehled animací klíčových snímků
Toto téma vás seznámí s animací jednotlivých klíč. Animací klíč jednotlivých umožňují animace pomocí více než dvě cílové hodnoty a řídit metodu interpolace animace.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Tento přehled pochopit, měli byste se seznámit s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animace a časové osy. Úvod do animací, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pomáhá také se seznamte s ze/k/podle animace. Další informace naleznete v přehledu From/To/By animace.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Co je animace snímků klíč?  
 Jako From/k/podle animace, klíč rámce animace animuje hodnotu vlastnost target. Vytvoří přechod mezi jeho cílové hodnoty přes jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Ale při From/k/podle animace vytvoří přechod mezi dvěma hodnotami, jeden klíč rámce animace můžete vytvořit přechody mezi libovolný počet cílové hodnoty. Na rozdíl od From/k/podle animace, klíčových snímků animace nemá žádné From, chcete-li nebo podle vlastností, se kterou chcete nastavit své cílové hodnoty. Animace klíč snímku cílové hodnoty jsou popsány pomocí klíčových snímků objekty (proto termín, "animace jednotlivých klíč"). K určení cílové hodnoty má animace, můžete vytvořit objekty klíčových snímků a přidat je do animace <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekce. Když je animace spuštěna, přechází mezi snímky, které jste zadali.  
  
 Také podporuje více cílové hodnoty, některé metody klíč rámce i podporují několik metod interpolace. Metoda interpolace animace definuje, jak přechází z jedné hodnoty na další. Existují tři typy interpolace: diskrétních, lineární a splined.  
  
 Pro animaci s animace klíč snímků, dokončete následující kroky.  
  
-   Deklarování animace a zadejte jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, stejně jako pro z/do nebo podle animace.  
  
-   Pro každou cílovou hodnotu vytvořit klíče rámce příslušného typu, nastavte ho na hodnotu a <xref:System.Windows.Media.Animation.KeyTime>a přidejte ji do animace <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekce.  
  
-   Přiřadit k vlastnosti, stejně jako s From/k/By animace animace. Další informace o použití animace do vlastnosti pomocí scénáře najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pro animaci <xref:System.Windows.Shapes.Rectangle> element do čtyř různých umístění.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Jako From/k/podle animace, animace klíč rámce, můžete použít na vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard> v značek a kódu nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda v kódu. Můžete také používat animace rámce, klíč k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji na jeden nebo více vlastností. Další informace o různých způsobech použití animace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Animace klíč jednotlivých typů  
 Protože animací generovat hodnoty vlastností, existují různé animace typy pro typy jinou vlastnost. Pro vlastnost, která přebírá animaci <xref:System.Double> (například elementu <xref:System.Windows.FrameworkElement.Width%2A> vlastnost), použijte animace, která vytváří <xref:System.Double> hodnoty. Pro vlastnost, která přebírá animaci <xref:System.Windows.Point>, použijte animace, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Animace jednotlivých klíč třídy patří do <xref:System.Windows.Media.Animation> obor názvů a dodržovat následující konvence:  
  
 *\<Typ >*`AnimationUsingKeyFrames`  
  
 Kde  *\<typ >* je typ hodnoty, které animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující třídy animace jednotlivých klíč.  
  
|Typ vlastnosti|Odpovídající z/do nebo podle animace – třída|Podporované metody interpolace|  
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
 Stejně, jako jsou různé typy animací jednotlivých klíč pro animace různých typech vlastností, existují také různé typy objektů klíčových snímků: jeden pro každý typ hodnota animovaný a metodu interpolace podporovány. Typy klíčových snímků splňovat následující konvence:  
  
 *\<InterpolationMethod >\<typ >*`KeyFrame`  
  
 Kde  *\<InterpolationMethod >* je metodu interpolace používá klíčových snímků a  *\<typ >* je typ hodnoty, které animuje třídy. Animace klíč rámce, který podporuje všechny tři interpolace metody bude mít tři typy klíčových snímků, které můžete použít. Například můžete použít tři typy klíčů rámce s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, a <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (Interpolace metody jsou popsané v podrobností v další části).  
  
 Primárním účelem klíčových snímků je zadání <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Každý typ klíče rámce poskytuje tyto dvě vlastnosti.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Vlastnost určuje hodnota cíle pro tento klíč snímek.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Vlastnost určuje, kdy (v rámci má animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) klíče rámečku <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> je dosaženo.  
  
 Po zahájení klíčových snímků animace iteruje jeho klíčových snímků v pořadí podle jejich <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnosti.  
  
-   Pokud žádné klíče rámce v době 0, animace vytvoří přechod mezi aktuální hodnota pro vlastnost target a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> první klíče rámce; jinak, animace výstupu hodnota začne hodnota první klíčových snímků.  
  
-   Animace vytvoří přechod mezi <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> první a druhý rámců klíče pomocí metodu interpolace určeného druhý klíčových snímků. Spustí přechod na první klíčových snímků <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a končí, když druhý klíčových snímků <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> je dosaženo.  
  
-   Animace bude pokračovat, vytváření přechodů mezi každou následné klíče snímek a jeho předchozí snímek klíče.  
  
-   Nakonec přechodů animace k hodnotě klíče rámce s největší klíče čas, je rovna nebo menší než je animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Pokud se má animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> je <xref:System.Windows.Duration.Automatic%2A> nebo jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A> shodnou s časem poslední klíčových snímků animace elementy end. Jinak, pokud má animace <xref:System.Windows.Duration> je větší než klíče čas poslední klíčových snímků animace blokování, dokud hodnota klíče rámce dosáhne konce své <xref:System.Windows.Duration>. Podobně jako všechny animace používá klíč rámce animace jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnosti k určení, zda drží ho konečná hodnota při ukončení jeho aktivní období. Další informace najdete v tématu [časování chování přehled](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> objekt definovaný v předchozím příkladu k předvedení jak <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pracovní vlastnosti.  
  
-   První klíčových snímků okamžitě nastaví má animace výstupní hodnotu na 0.  
  
-   Druhý klíč rámečku animuje od 0 do 350. Spustí po skončení první klíčových snímků (v čase = 0 s) a přehraje na 2 sekundy, v době ukončení = 0:0:2.  
  
-   Třetí klíče rámečku animuje z 350 na 50. Začne při ukončení druhý klíčových snímků (v čase = 2 sekundy) a přehraje 5 sekund, v době ukončení = 0:0:7.  
  
-   Čtvrtý klíče snímek animuje z 50 na 200. Začne při ukončení třetí klíčových snímků (v čase = 7 sekund) a přehraje 1 sekundy, v době ukončení = 0:0:8.  
  
-   Protože <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost animace byla nastavená na 10 sekund, animace obsahuje jeho konečná hodnota na 2 sekundy před ukončuje v čase = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>Metody interpolace  
 V předchozích částech uvedeno, že některé animací klíč jednotlivých podporují několik metod interpolace. Animace interpolace popisuje, jak animace přechází mezi hodnotami přes jeho trvání. Pokud vyberete typ klíče rámce pomocí animace, můžete definovat metodu interpolace pro tento segment klíčových snímků. Existují tři různé typy metod interpolace: lineární, diskrétní a splined.  
  
### <a name="linear-interpolation"></a>Lineární interpolace  
 Lineární interpolace postupuje animace s rychlostí konstantní hodnoty duration segmentu. Například pokud segment klíče rámce přechází od 0 do 10 přes v délce 5 sekund, animace bude výstup následujících hodnot v zadaném časy:  
  
|Čas|Hodnota výstupu|  
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
 S diskrétní interpolace funkce animace přejde z jednu hodnotu na další bez interpolace. Pokud segment klíče rámce přechází od 0 do 10 přes v délce 5 sekund, animace bude výstup následujících hodnot v zadaném časy:  
  
|Čas|Hodnota výstupu|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Všimněte si, jak animace nezmění jeho výstupní hodnotu až velmi konce doby trvání segmentu.  
  
 Splined interpolace je složitější. Je popsán v následující části.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Splined interpolace  
 Splined interpolace lze použít k dosažení realističtější časování účinky. Vzhledem k tomu, že animace se proto často používají pro přesnou důsledky, které se vyskytují v reálném světě, vývojáři může potřebovat přesně řízení zrychlení a zpomalení objektů a zavřete manipulaci s časování segmentů. Křivkový klíčových snímků umožňují animace s splined interpolace. Pomocí jiných klíčových snímků, můžete určit <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Křivkový klíče rámeček, je třeba také zadat <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. Následující příklad ukazuje jeden křivkový klíče rámeček pro <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Upozornění <xref:System.Windows.Media.Animation.KeySpline> vlastnost; která se liší od ostatních typů klíčových snímků díky křivkový klíčových snímků.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Počáteční bod, koncový bod a dva body ovládací prvek je definována krychlový Bézierovu křivku. <xref:System.Windows.Media.Animation.KeySpline> Vlastnost klíčových snímků křivkový definuje dvě řídicího bodu Bézierovy křivky, který rozšiřuje z (0,0) na (1,1). První řídicí bod řídí křivky faktor poloviny Bézierovy křivky a druhý bod řízení ovládací prvky faktor druhé polovině tématu segment Bézierovy křivky. Výsledný křivky popisuje rychlost změny pro tento snímek křivkový klíče. Tím strmější křivku, tím rychleji klíčových snímků změní jeho hodnoty. Jako křivku získá plošší, klíče rámečku změní jeho hodnoty pomaleji.  
  
 Můžete použít <xref:System.Windows.Media.Animation.KeySpline> chcete simulovat fyzické trajektorie jako návratem horních nebo kuličky nebo použít jiné "usnadňují v" a "doběhu" účinky pohybu animace. Pro uživatele interakce důsledky jako pozadí stmívačkami nebo ovládací prvek tlačítko odrazu může použít splined interpolace pro urychlení nebo zpomalit rychlost změny pro animace určitým způsobem.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> 0,1 1,0, který vytvoří následující Bézierovu křivku.  
  
 ![Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Klíče křivkový s kontrolní body (0,0, 1.0) a (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Tento klíčových snímků animuje rychle, když se začne, zpomaluje a pak urychluje znovu předtím, než ho ukončí.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> z 0.75,1.0 0.5,0.25, který vytvoří následující Bézierovu křivku.  
  
 ![Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Klíče křivkový s ovládacím prvkem body (0,25, 0,5) a (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Protože zakřivení Bézierovy křivky mění velmi málo, tento klíč rámce animuje téměř konstantní rychlostí; zpomaluje poněkud směrem k velmi ukončení.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pro animaci pozice rámečku. Protože <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> používá <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> objekty, přechod mezi každou hodnotu klíče rámce používá splined interpolace.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Splined interpolace může být obtížné porozumět; experimentování se jiné nastavení může pomoct. [Klíč křivkový animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160011) umožňuje změnu hodnoty klíče křivkový a prohlédněte si výsledek, obsahuje na animace.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>Kombinování metody interpolace  
 Klíčových snímků můžete použít s typy různých interpolace v jednom klíčových snímků animace. Při dvou klíčových snímků animace s jinou interpolace postupovat podle sebe navzájem, metodu interpolace druhý klíče rámce slouží k vytvořit přechod z první hodnoty druhou.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> se vytvoří tento interpolace lineární, splined a diskrétní používá.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Další informace o dobu trvání a časy, klíče  
 Jako jiné animace animací jednotlivých klíče mají <xref:System.Windows.Duration> vlastnost. Kromě určení má animace <xref:System.Windows.Duration>, musíte určit, jaká část této hodnotě DURATION dostane na každý klíčových snímků. Můžete k tomu popisující <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pro každou z klíčových snímků animace společnosti. Každý klíč rámečku <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> určuje při ukončení tohoto klíče rámečku.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Vlastnost neurčuje, jak dlouho hraje klíče čas. Množství času, kterou hraje klíčových snímků je určen podle při ukončení klíče rámečku, když předchozí klíče rámečku skončila a doba trvání animace na. Klíče časy může být určený jako hodnotu času v procentech nebo speciální hodnoty <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Následující seznam popisuje různé způsoby zadávání klíče časy.  
  
### <a name="timespan-values"></a>Časový interval hodnoty  
 Můžete použít <xref:System.TimeSpan> hodnoty k určení <xref:System.Windows.Media.Animation.KeyTime>. Hodnota by měla být větší než nebo rovna 0 a menší než doba trvání animace společnosti. Následující příklad ukazuje 10 sekund a jehož klíče časy jsou zadané jako hodnoty času čtyři klíčových snímků animace s určitou dobou trvání.  
  
-   První klíče rámečku animuje od základní hodnoty do 100 přes první 3 sekund končí v čase = 0:0:03.  
  
-   Druhý klíč rámečku animuje od 100 do 200. Spustí po skončení první klíčových snímků (v čase = 3 sekund) a přehraje 5 sekund, v době ukončení = 0:0:8.  
  
-   Třetí klíče rámečku animuje z hodnoty 200 na 500. Začne při ukončení druhý klíčových snímků (v čase = 8 sekund) a přehraje 1 sekundy, v době ukončení = 0:0:9.  
  
-   Čtvrtý klíče snímek animuje z 500 na 600. Začne při ukončení třetí klíčových snímků (v čase = 9 sekund) a přehraje 1 sekundy, v době ukončení = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Procentní hodnoty  
 Procentuální hodnota určuje, že klíče rámečku končí u některých podíl bude animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zadejte procento jako číslo následované `%` symbol. V kódu, můžete použít <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> metoda a předejte ji <xref:System.Double> procentuální hodnota. Hodnota musí být větší než nebo rovna 0 a menší než nebo rovna 100 procent. Následující příklad ukazuje, s určitou dobou trvání animace 10 sekund a čtyři klíčových snímků jsou zadány jejichž klíče časy jako procenta.  
  
-   První klíče rámečku animuje od základní hodnoty do 100 přes první 3 sekund končí v čase = 0:0:3.  
  
-   Druhý klíč rámečku animuje od 100 do 200. Spustí po skončení první klíčových snímků (v čase = 3 sekund) a přehraje 5 sekund, v době ukončení = 0:0:8 (0,8 * 10 = 8).  
  
-   Třetí klíče rámečku animuje z hodnoty 200 na 500. Začne při ukončení druhý klíčových snímků (v čase = 8 sekund) a přehraje 1 sekundy, v době ukončení = 0:0:9 (0,9 * 10 = 9).  
  
-   Čtvrtý klíče snímek animuje z 500 na 600. Začne při ukončení třetí klíčových snímků (v čase = 9 sekund) a přehraje 1 sekundy, v době ukončení = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Speciální hodnotu Uniform  
 Použití <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> časování, když chcete, aby každý klíčových snímků na stejnou dobu trvat.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> klíče čas rozdělí dobu, k dispozici stejně podle počtu klíčových snímků k určení koncového času každého klíče snímku. Následující příklad ukazuje animace v délce 10 sekund a čtyři klíčových snímků, jehož klíč krát nejsou zadané jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   První klíče rámečku animuje od základní hodnoty do 100 přes první 2,5 sekund končí v čase = 0:0:2.5.  
  
-   Druhý klíč rámečku animuje od 100 do 200. Spustí po skončení první klíčových snímků (v čase = 2,5 sekund) a přehraje přibližně 2,5 sekund, v době ukončení = 0:0:5.  
  
-   Třetí klíče rámečku animuje z hodnoty 200 na 500. Začne při ukončení druhý klíčových snímků (v čase = 5 sekund) a přehraje 2,5 sekund, v době ukončení = 0:0:7.5.  
  
-   Čtvrtý klíče snímek animuje z 500 na 600. Začne při ukončení druhý klíčových snímků (v čase = 7.5 sekund) a přehraje 2,5 sekund, v době ukončení = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Speciální hodnotu, pracovníky  
 Použití <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> časování, pokud chcete animace konstantní rychlostí.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> klíče čas přiděluje času dostupnosti podle délka jednotlivých klíčových snímků k určení doby trvání jednotlivých rámce.  To zajistí chování rychlosti nebo rychle animace zůstává konstantní.  Následující příklad ukazuje animace v délce 10 sekund a tři klíčových snímků, jehož klíč krát nejsou zadané jako <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Všimněte si, že, pokud je doba klíče poslední klíčových snímků <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, nastaví se doba jejího přeložit klíče do 100 procent. Pokud je to první klíče snímek vícesnímkovou animace je pracovníky, bude doba jejího přeložit klíče nastavena na hodnotu 0. (Pokud kolekce klíčových snímků obsahuje pouze jeden klíč snímek a je pracovníky klíčových snímků, doba jejího přeložit klíče se nastavit do 100 procent.)  
  
 Různé klíčových snímků v rámci jedné klíčových snímků animace může používat jinou dobu klíče typy.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Kombinace klíče časy, rámců klíče mimo pořadí  
 Klíčových snímků můžete použít jiné <xref:System.Windows.Media.Animation.KeyTime> hodnotu typy v stejné animace. A, i když se doporučuje, přidání klíčových snímků v pořadí, ve kterém by měla hrát, není nutné. Je schopen řešení mimo pořadí klíčových snímků animace a načasování systému. Klíčových snímků s neplatné klíče časy jsou ignorovány.  
  
 Následující seznam popisuje postup, podle kterého jsou klíče časy pro klíčových snímků animace klíč snímku.  
  
1.  Vyřešte <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
2.  Určit, že animace *celkový čas interpolace*, celkový čas, který potřebuje animace snímku klíč k dokončení dopředného iterací.  
  
    1.  Pokud se má animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> není <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>, interpolace celkový čas je hodnota je animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost.  
  
    2.  Jinak je největší interpolace celkový čas <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> hodnota mezi klíčových snímků, pokud žádný neexistuje.  
  
    3.  Celkový počet interpolace čas, jinak hodnota je 1 sekunda.  
  
3.  Použijte hodnotu interpolace celkový čas k vyřešení <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
4.  Vyřešit poslední klíčových snímků, je-li již nebyl vyřešen v předchozích krocích. Pokud <xref:System.Windows.Media.Animation.KeyTime> posledního klíčových snímků je <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, doba jejího přeložit bude rovnat interpolace celkový čas.  
  
     Pokud <xref:System.Windows.Media.Animation.KeyTime> první klíče rámečku je <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> a tento animace má více než na klíčových snímků, vyřešte jeho <xref:System.Windows.Media.Animation.KeyTime> hodnotu nula; Pokud je pouze jeden klíčový snímek a jeho <xref:System.Windows.Media.Animation.KeyTime> hodnota je <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, je přeložen na celkový počet čas interpolace, jak je popsáno v předchozím kroku.  
  
5.  Vyřešte zbývající <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty: každý získá stejný podíl času dostupnosti.  Během tohoto procesu nepřeložené <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty jsou dočasně považovány za <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty a získání dočasného přeložit čas.  
  
6.  Vyřešte <xref:System.Windows.Media.Animation.KeyTime> hodnoty klíče snímků se neurčené klíče časy pomocí klíče rámce nejbližší je deklarovaná, které byly vyřešeny problémy s <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
7.  Vyřešte zbývající <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> použít <xref:System.Windows.Media.Animation.KeyTime> hodnoty sousedních klíčů rámce k určení vypršela doba pro jejich vyřešení.  Cílem je zajistěte, aby byl rychlosti animace konstantní přeložit době klíčových snímků.  
  
8.  Seřadit klíčových snímků v pořadí přeložit času (primární klíč) a pořadí deklarace (sekundární klíč), tj., použijte stabilní řazení podle přeložit klíčových snímků <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.KeyTime>  
 <xref:System.Windows.Media.Animation.KeySpline>  
 <xref:System.Windows.Media.Animation.Timeline>  
 [Ukázka klíče křivkový animace](http://go.microsoft.com/fwlink/?LinkID=160011)  
 [Ukázka @keyframe, které určuje animace](http://go.microsoft.com/fwlink/?LinkID=160012)  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Přehled chování časování](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
