---
title: Přehled animací klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 8eb590b07eae3b76b3a206b9731997a6bc2c90d7
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344906"
---
# <a name="key-frame-animations-overview"></a>Přehled animací klíčových snímků
Toto téma vás seznámí s animacemi klíčových snímků. Animace klíčových snímků umožňují animovat pomocí více než dvou cílových hodnot a řídit metodu interpolace animace.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li pochopit tento přehled, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] měli byste být obeznámeni s animacemi a časovými osy. Úvod k animacím najdete v tématu [Přehled animací](animation-overview.md). To také pomáhá být obeznámeni s From / To / By animace. Další informace naleznete v tématu –do/podle animace Přehled.  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>Co je animace klíčových snímků?  
 Podobně jako animace Od/Do/Podle animace klíčových snímků animuje hodnotu cílové vlastnosti. Vytvoří přechod mezi svými cílovými <xref:System.Windows.Media.Animation.Timeline.Duration%2A>hodnotami nad jeho . Však zatímco From/To/By animace vytvoří přechod mezi dvěma hodnotami, jeden klíčový snímek animace můžete vytvořit přechody mezi libovolný počet cílových hodnot. Na rozdíl od animace Od/Do/Podle animace klíčových snímků nemá žádné vlastnosti From, To nebo By, pomocí kterých chcete nastavit cílové hodnoty. Cílové hodnoty animace klíčových snímků jsou popsány pomocí objektů klíčových snímků (odtud termín "animace klíčových snímků"). Chcete-li určit cílové hodnoty animace, vytvořte objekty klíčových <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> snímků a přidejte je do kolekce animace. Po spuštění animace přechází mezi zadanými snímky.  
  
 Kromě podpory více cílových hodnot některé metody klíčových snímků dokonce podporují více metod interpolace. Metoda interpolace animace definuje, jak přechází z jedné hodnoty na další. Existují tři typy interpolací: diskrétní, lineární a splined.  
  
 Chcete-li animaci klíčových snímků animovat, proveďte následující kroky.  
  
- Deklarujte animaci a zadejte její <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, stejně jako byste pro animaci z/do/by.  
  
- Pro každou cílovou hodnotu vytvořte klíčový snímek <xref:System.Windows.Media.Animation.KeyTime>příslušného typu, nastavte jeho <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> hodnotu a přidejte ji do kolekce animace.  
  
- Přidružte animaci k vlastnosti, stejně jako u animace Od/Do/Podle. Další informace o použití animace na vlastnost pomocí scénáře, najdete v [tématu Přehled scénářů](storyboards-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> k animaci <xref:System.Windows.Shapes.Rectangle> prvku do čtyř různých umístění.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Stejně jako from/to/by animace, animace klíčových snímků lze <xref:System.Windows.Media.Animation.Storyboard> použít na vlastnost pomocí v <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> značky a kódu nebo pomocí metody v kódu. Animaci klíčových snímků můžete také <xref:System.Windows.Media.Animation.AnimationClock> použít k vytvoření a použití na jednu nebo více vlastností. Další informace o různých metodách použití animací naleznete v [tématu Přehled technik animace vlastností](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>Typy animací klíčových snímků  
 Vzhledem k tomu, že animace generují hodnoty vlastností, existují různé typy animací pro různé typy vlastností. Chcete-li animovat <xref:System.Double> vlastnost, která trvá <xref:System.Windows.FrameworkElement.Width%2A> (například vlastnost prvku), <xref:System.Double> použijte animaci, která vytváří hodnoty. Chcete-li animovat <xref:System.Windows.Point>vlastnost, která trvá , <xref:System.Windows.Point> použijte animaci, která vytváří hodnoty a tak dále.  
  
 Třídy animace klíčových snímků <xref:System.Windows.Media.Animation> patří do oboru názvů a dodržují následující konvence pojmenování:  
  
 * \<Typ>*`AnimationUsingKeyFrames`  
  
 Kde * \<Type>* je typ hodnoty, kterou třída animuje.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující třídy animace klíčových snímků.  
  
|Typ vlastnosti|Odpovídající z/do/podle třídy animace|Podporované interpolační metody|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Diskrétní|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Diskrétní, Lineární, Splined|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>Cílové hodnoty (klíčové snímky) a klíčové časy  
 Stejně jako existují různé typy animací klíčových snímků pro animaci různých typů vlastností, existují také různé typy objektů klíčových snímků: jeden pro každý typ animované hodnoty a podporovaná metoda interpolace. Typy klíčových snímků dodržují následující konvence pojmenování:  
  
 *>typu \<>metody InterpolationMethod \<*`KeyFrame`  
  
 Kde * \<InterpolationMethod>* je metoda interpolace klíčový snímek používá a * \<Typ>* je typ hodnoty, která třída animuje. Animace klíčových snímků, která podporuje všechny tři metody interpolace, bude mít tři typy klíčových snímků, které můžete použít. Můžete například použít tři typy klíčových <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>snímků <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>s : <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, , a . (Interpolační metody jsou podrobně popsány v pozdější části.)  
  
 Primárním účelem klíčového snímku <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> je <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>určení a a . Každý typ klíčového snímku poskytuje tyto dvě vlastnosti.  
  
- Vlastnost <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> určuje cílovou hodnotu pro tento klíčový snímek.  
  
- Vlastnost <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> určuje, kdy (v rámci <xref:System.Windows.Media.Animation.Timeline.Duration%2A>animace) <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> klíčový snímek je dosaženo.  
  
 Když začne animace klíčových snímků, iterátprostřed prostřednictvím klíčových snímků v pořadí definovaném jejich <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnostmi.  
  
- Pokud neexistuje žádný klíčový snímek v čase 0, animace vytvoří přechod mezi <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> aktuální hodnotou cílové vlastnosti a prvního klíčového snímku; v opačném případě se výstupní hodnota animace stane hodnotou prvního klíčového snímku.  
  
- Animace vytvoří přechod mezi <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> prvním a druhým klíčovým snímkem pomocí interpolační metody určené druhým klíčovým snímkem. Přechod začíná prvním klíčovým snímkem <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a končí po <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> dosažení druhého klíčového snímku.  
  
- Animace pokračuje a vytváří přechody mezi každým následujícím klíčovým snímkem a jeho předchozím klíčovým snímkem.  
  
- Nakonec animace přechody na hodnotu klíčového snímku s největší čas klíče, který je <xref:System.Windows.Media.Animation.Timeline.Duration%2A>roven nebo menší než animace .  
  
 Pokud <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animace je <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jeho se rovná čas poslední klíčový snímek, animace končí. V opačném případě, <xref:System.Windows.Duration> pokud animace je větší než čas klíče poslední klíčový snímek, animace obsahuje hodnotu klíčového snímku, dokud nedosáhne konce jeho <xref:System.Windows.Duration>. Stejně jako všechny animace, animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> klíčových snímků používá svou vlastnost k určení, zda obsahuje konečnou hodnotu, když dosáhne konce aktivní období. Další informace naleznete v tématu [Přehled chování časování](timing-behaviors-overview.md).  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> objekt definovaný v předchozím příkladu <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> k předvedení fungování vlastností a.  
  
- První klíčový snímek okamžitě nastaví výstupní hodnotu animace na hodnotu 0.  
  
- Druhý klíčový snímek animuje od 0 do 350. Spustí se po ukončení prvního klíčového snímku (v čase = 0 sekund) a hraje se po dobu 2 sekund, končí v čase = 0:0:2.  
  
- Třetí klíčový snímek animuje od 350 do 50. Spustí se, když druhý klíčový snímek skončí (v čase = 2 sekundy) a hraje po dobu 5 sekund, končí v čase = 0:0:7.  
  
- Čtvrtý klíčový snímek animuje od 50 do 200. Spustí se, když třetí klíčový snímek skončí (v čase = 7 sekund) a hraje se po dobu 1 sekundy, končí v čase = 0:0:8.  
  
- Vzhledem <xref:System.Windows.Media.Animation.Timeline.Duration%2A> k tomu, že vlastnost animace byla nastavena na 10 sekund, animace obsahuje jeho konečnou hodnotu po dobu dvou sekund před koncem v čase = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>Interpolační metody  
 Předchozí části uvedené, že některé animace klíčových snímků podporují více metod interpolace. Interpolace animace popisuje, jak animace přechody mezi hodnotami v průběhu jeho trvání. Výběrem typu klíčového snímku, který použijete s animací, můžete definovat metodu interpolace pro tento segment klíčových snímků. Existují tři různé typy metod interpolace: lineární, diskrétní a splined.  
  
### <a name="linear-interpolation"></a>Lineární interpolace  
 Při lineární interpolaci animace postupuje konstantní rychlostí trvání segmentu. Pokud například segment klíčového snímku přejde z 0 na 10 po dobu 5 sekund, animace vynese následující hodnoty v určených časech:  
  
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
 Při diskrétní interpolaci se funkce animace přeskakuje z jedné hodnoty na druhou bez interpolace. Pokud segment klíčového snímku přejde z 0 na 10 po dobu trvání 5 sekund, animace vynese následující hodnoty v určených časech:  
  
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
  
 Všimněte si, jak animace nezmění svou výstupní hodnotu až do samého konce trvání segmentu.  
  
 Splined interpolace je složitější. Je popsán v další části.  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>Splined Interpolace  
 Splined interpolace může být použita k dosažení realističtější časování efekty. Vzhledem k tomu, že animace se tak často používají k napodobování efektů, ke kterým dochází v reálném světě, mohou vývojáři potřebovat jemné řízení zrychlení a zpomalení objektů a úzkou manipulaci segmentů časování. Klíčové snímky spline umožňují animovat pomocí interpolace splined. U jiných klíčových snímků <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>zadáte a a . Pomocí klíčového snímku spline zadáte <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>také . Následující příklad ukazuje jeden klíčový snímek <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>spline pro . Všimněte <xref:System.Windows.Media.Animation.KeySpline> si nemovitosti; to je to, co dělá spline klíčový snímek odlišný od ostatních typů klíčových snímků.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Kubická Bezierova křivka je definována počátečním bodem, koncovým bodem a dvěma řídicími body. Vlastnost <xref:System.Windows.Media.Animation.KeySpline> klíčového snímku spline definuje dva řídicí bod Bezierovy křivky, který sahá od (0,0) do (1,1). První řídicí bod ovládá faktor křivky první poloviny Bezierovy křivky a druhý řídicí bod řídí faktor křivky druhé poloviny Bezierova segmentu. Výsledná křivka popisuje rychlost změny pro tento klíčový snímek spline. Čím strmější je křivka, tím rychleji klíčový snímek mění své hodnoty. Jak se křivka stává plošší, klíčový snímek mění své hodnoty pomaleji.  
  
 Můžete použít <xref:System.Windows.Media.Animation.KeySpline> k simulaci fyzické trajektorie, jako je padající voda nebo skákací koule, nebo použít jiné efekty "snadnost v" a "zmírnit" na pohybanimace. U efektů interakce s uživatelem, jako je zeslábnutí pozadí nebo odskok ovládacího tlačítka, můžete použít sférou interpolace, abyste urychlili nebo zpomalili rychlost změny animace určitým způsobem.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> a 0,1 1,0, který vytvoří následující Bezierovu křivku.  
  
 ![Bezierova křivka](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Klíčná křivka s řídicími body (0,0, 1,0) a (1,0, 0,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Tento klíčový snímek se rychle animuje, když začíná, zpomaluje a pak se znovu zrychluje, než skončí.  
  
 Následující příklad určuje <xref:System.Windows.Media.Animation.KeySpline> a-z 0.5,0.25 0.75,1.0, který vytvoří následující Bezierovu křivku.  
  
 ![Bezierova křivka](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Klíčná křivka s řídicími body (0,25, 0,5) a (0,75; 1,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Vzhledem k tomu, že zakřivení Bezierovy křivky se mění velmi málo, tento klíčový snímek se animuje téměř konstantní rychlostí; zpomaluje poněkud ke svému samému konci.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> k animaci polohy obdélníku. Vzhledem <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> k tomu, že objekty používá, použije přechod mezi jednotlivými hodnotami klíčového snímku interpolaci splined.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Splined interpolace může být obtížné pochopit; experimentování s různými nastaveními může pomoci. [Ukázka animace spline klíče](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) umožňuje změnit hodnoty křivky spline kláves a zobrazit výsledek, který má na animaci.  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>Kombinace interpolačních metod  
 Klíčové snímky s různými typy interpolace můžete použít v animaci jednoho klíčového snímku. Když dvě animace klíčových snímků s různými interpolacemi následují, použije se metoda interpolace druhého klíčového snímku k vytvoření přechodu z první hodnoty na druhou.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> je vytvořen a, který používá lineární, splined a diskrétní interpolaci.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>Další informace o délce trvání a době platnosti klíčů  
 Stejně jako ostatní animace mají animace <xref:System.Windows.Duration> klíčových snímků vlastnost. Kromě určení animace <xref:System.Windows.Duration>je třeba určit, jaká část této doby trvání je dána každému klíčovému snímku. Uděláte to tak, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> že popopisujete pro každý klíčový snímek animace. Každý klíčový snímek <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> určuje, kdy tento klíčový snímek skončí.  
  
 Vlastnost <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> neurčuje, jak dlouho se hraje čas klíče. Doba přehrávání klíčového snímku je určena ukončením klíčového snímku, ukončením předchozího klíčového snímku a dobou trvání animace. Klíčové časy mohou být určeny jako časová hodnota, <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>procento nebo jako speciální hodnoty nebo .  
  
 Následující seznam popisuje různé způsoby určení doby klíče.  
  
### <a name="timespan-values"></a>Hodnoty časového posunu  
 Hodnoty můžete <xref:System.TimeSpan> použít k <xref:System.Windows.Media.Animation.KeyTime>určení . Hodnota by měla být větší nebo rovna 0 a menší než nebo rovna trvání animace. Následující příklad ukazuje animaci s dobou trvání 10 sekund a čtyři klíčové snímky, jejichž klíčové časy jsou určeny jako časové hodnoty.  
  
- První klíčový snímek animuje ze základní hodnoty na 100 během prvních 3 sekund, končící v čase = 0:0:03.  
  
- Druhý klíčový snímek animuje od 100 do 200. Spustí se po skončení prvního klíčového snímku (v čase = 3 sekundy) a hraje se po dobu 5 sekund, končí v čase = 0:0:8.  
  
- Třetí klíčový snímek animuje od 200 do 500. Spustí se, když druhý klíčový snímek skončí (v čase = 8 sekund) a hraje se po dobu 1 sekundy, končí v čase = 0:0:9.  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Spustí se, když třetí klíčový snímek končí (v čase = 9 sekund) a hraje po dobu 1 sekundy, končící v čase = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Procentuální hodnoty  
 Procentuální hodnota určuje, že klíčový snímek končí <xref:System.Windows.Media.Animation.Timeline.Duration%2A>v určitém procentu animace . V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]písmenu a) určíte procento `%` jako číslo následované symbolem. V kódu použijete <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> metodu a <xref:System.Double> předáte ji označující procento. Hodnota musí být větší nebo rovna 0 a menší nebo rovna 100 procent. Následující příklad ukazuje animaci s dobou trvání 10 sekund a čtyři klíčové snímky, jejichž klíčové časy jsou určeny jako procenta.  
  
- První klíčový snímek animuje ze základní hodnoty na 100 během prvních 3 sekund, končící v čase = 0:0:3.  
  
- Druhý klíčový snímek animuje od 100 do 200. Spustí se po skončení prvního klíčového snímku (v čase = 3 sekundy) a hraje se po dobu 5 sekund, končí v čase = 0:0:8 (0,8 * 10 = 8).  
  
- Třetí klíčový snímek animuje od 200 do 500. Spustí se, když druhý klíčový snímek skončí (v čase = 8 sekund) a přehraje se po dobu 1 sekundy, končí v čase = 0:0:9 (0,9 * 10 = 9).  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Spustí se, když třetí klíčový snímek končí (v čase = 9 sekund) a hraje se po dobu 1 sekundy, končí v čase = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Speciální hodnota, Uniforma  
 Časování použijte, <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> pokud chcete, aby každý klíčový snímek zabral stejnou dobu.  
  
 Klíčový <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> čas vydělí dostupný čas rovnoměrně počtem klíčových snímků, aby se určil čas ukončení každého klíčového snímku. Následující příklad ukazuje animaci s dobou trvání 10 sekund a <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>čtyři klíčové snímky, jejichž klíčové časy jsou určeny jako .  
  
- První klíčový snímek animuje ze základní hodnoty na 100 během prvních 2,5 sekundy, končící v čase = 0:0:2.5.  
  
- Druhý klíčový snímek animuje od 100 do 200. Spustí se po ukončení prvního klíčového snímku (v čase = 2,5 sekundy) a přehraje se přibližně 2,5 sekundy a končí v čase = 0:0:5.  
  
- Třetí klíčový snímek animuje od 200 do 500. Spustí se, když druhý klíčový snímek skončí (v čase = 5 sekund) a hraje se po dobu 2,5 sekundy, končí v čase = 0:0:7.5.  
  
- Čtvrtý klíčový snímek animuje od 500 do 600. Spustí se, když druhý klíčový snímek skončí (v čase = 7,5 sekundy) a hraje se po dobu 2,5 sekundy, končí v čase = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Speciální hodnota, tempo  
 Časování použijte, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> když chcete animovat konstantní rychlostí.  
  
 Čas <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> klíče přiděluje dostupný čas podle délky každého klíčového snímku k určení doby trvání každého snímku.  To bude poskytovat chování, které rychlost nebo tempo animace zůstává konstantní.  Následující příklad ukazuje animaci s dobou trvání 10 sekund a <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>tři klíčové snímky, jejichž klíčové časy jsou určeny jako .  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Všimněte si, že pokud je <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> čas <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>klíče posledního klíčového snímku nebo , jeho přeložený čas klíče bude nastaven na 100 procent. Pokud první klíčový snímek v animaci s více snímkem přecházel, bude jeho vyřešený čas klíče nastaven na 0. (Pokud kolekce klíčových snímků obsahuje pouze jeden klíčový snímek a jedná se o klíčový snímek s tempem, bude jeho čas vyřešeného klíče nastaven na 100 procent.)  
  
 Různé klíčové snímky v rámci animace jednoho klíčového snímku mohou používat různé typy času kláves.  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>Kombinace časů klíčů, mimopořadí klíčových snímků  
 Klíčové snímky s různými <xref:System.Windows.Media.Animation.KeyTime> typy hodnot můžete použít ve stejné animaci. A i když se doporučuje přidat klíčové snímky v pořadí, ve kterém by měly hrát, není to nutné. Animační a časovací systém je schopen vyřešit mimopořadí klíčových snímků. Klíčové snímky s neplatnými časy klíčů jsou ignorovány.  
  
 Následující seznam popisuje postup, podle kterého jsou vyřešeny klíčové časy pro klíčové snímky animace klíčových snímků.  
  
1. Vyřešte <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> hodnoty.  
  
2. Určete *celkovou dobu interpolace*animace , celkový čas, který trvá animace klíčových snímků k dokončení iterace vpřed.  
  
    1. Pokud animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> není <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>, celková doba interpolace je hodnota <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti animace.  
  
    2. V opačném případě je celková <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> doba interpolace největší hodnotou zadanou mezi klíčovými snímky, pokud existují.  
  
    3. V opačném případě je celková doba interpolace 1 sekunda.  
  
3. K vyřešení <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> hodnot použijte hodnotu celkové doby interpolace.  
  
4. Vyřešte poslední klíčový snímek, pokud ještě nebyl vyřešen v předchozích krocích. <xref:System.Windows.Media.Animation.KeyTime> Pokud je <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> poslední klíčový snímek nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, jeho vyřešený čas se bude rovnat celkovému času interpolace.  
  
     <xref:System.Windows.Media.Animation.KeyTime> Pokud první klíčový snímek <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> je a tato animace má více <xref:System.Windows.Media.Animation.KeyTime> než na klíčových snímků, vyřešit jeho hodnotu na nulu; pokud existuje pouze jeden klíčový <xref:System.Windows.Media.Animation.KeyTime> snímek a jeho hodnota je <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, je vyřešen a celkový čas interpolace, jak je popsáno v předchozím kroku.  
  
5. Vyřešit <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> zbývající hodnoty: každý z nich má stejný podíl na dostupném čase.  Během tohoto procesu <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> nevyřešené hodnoty <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> jsou dočasně považovány za hodnoty a získat dočasný vyřešený čas.  
  
6. Vyřešte <xref:System.Windows.Media.Animation.KeyTime> hodnoty klíčových snímků s neurčenými časy klíčů pomocí <xref:System.Windows.Media.Animation.KeyTime> klíčových snímků deklarovaných jako nejbližší, které mají vyřešené hodnoty.  
  
7. Vyřešte zbývající <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> hodnoty. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> pomocí <xref:System.Windows.Media.Animation.KeyTime> hodnot sousedních klíčových snímků určete jejich vyřešený čas.  Cílem je zajistit, aby rychlost animace byla konstantní kolem vyřešeného času tohoto klíčového snímku.  
  
8. Seřaďte klíčové snímky podle vyřešeného času (primární klíč) a pořadí deklarace (sekundární klíč), tj. <xref:System.Windows.Media.Animation.KeyTime>  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Ukázka animace Spline klíče](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
- [Přehled chování časování](timing-behaviors-overview.md)
