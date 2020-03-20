---
title: Přehled chování časování
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145394"
---
# <a name="timing-behaviors-overview"></a>Přehled chování časování
Toto téma popisuje časování chování animací a jiných <xref:System.Windows.Media.Animation.Timeline> objektů.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste být obeznámeni se základními funkcemi animace. Další informace naleznete v tématu [Přehled animací](animation-overview.md).  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>Typy časové osy  
 A <xref:System.Windows.Media.Animation.Timeline> představuje segment času. Poskytuje vlastnosti, které umožňují určit délku tohoto segmentu, kdy by měl začít, kolikrát se bude opakovat, jak rychle čas postupuje v tomto segmentu a další.  
  
 Třídy, které dědí z třídy časové osy poskytují další funkce, jako je animace a přehrávání médií. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje následující <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ časové osy|Popis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstraktní základní <xref:System.Windows.Media.Animation.Timeline> třída pro objekty, které generují výstupní hodnoty pro animaci vlastností.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje výstup z mediálního souboru.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.TimelineGroup> Typ, který seskupuje <xref:System.Windows.Media.Animation.Timeline> a řídí podřízené objekty.|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ParallelTimeline> Typ, který poskytuje informace o cílení pro objekty časové osy, které obsahuje.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstraktní základní třída, která definuje chování časování.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstraktní třída <xref:System.Windows.Media.Animation.Timeline> pro objekty, které mohou obsahovat jiné <xref:System.Windows.Media.Animation.Timeline> objekty.|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>Vlastnosti, které řídí délku časové osy  
 A <xref:System.Windows.Media.Animation.Timeline> představuje segment času a délka časové osy může být popsána různými způsoby. Následující tabulka definuje několik termínů pro popis délky časové osy.  
  
|Označení|Popis|Vlastnosti||||  
|----------|-----------------|----------------|-|-|-|  
|Jednoduchá doba trvání|Doba, po kterou časová osa trvá k vytvoření jedné předsunuté iterace.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jedno opakování|Doba, po kterou se časová osa přehrává <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> jednou dopředu, a pokud je vlastnost pravdivá, přehraje se jednou pozpátku.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktivní období|Doba, po kterou časová osa dokončí všechna opakování <xref:System.Windows.Media.Animation.RepeatBehavior> určená jeho vlastností.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>Vlastnost Duration  
 Jak již bylo zmíněno, časová osa představuje segment času. Délka tohoto segmentu je určena časovou osou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Když časová osa dosáhne konce své doby trvání, přestane se přehrávat. Pokud má časová osa podřízené časové osy, přestanou se také přehrávat. V případě animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> určuje, jak dlouho trvá animace přechod z jeho počáteční hodnotu na jeho koncovou hodnotu. Doba trvání časové osy se někdy nazývá jeho *jednoduchá doba trvání*, rozlišovat mezi dobou trvání jedné iterace a celkovou dobou přehrávání animace včetně opakování. Dobu trvání můžete určit pomocí konečné časové hodnoty <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>zvláštních hodnot nebo . Doba trvání animace by měla <xref:System.Windows.Duration.TimeSpan%2A> vyřešit na hodnotu, takže může přecházet mezi hodnotami.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Časové osy <xref:System.Windows.Media.Animation.Storyboard> kontejneru, například <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Duration.Automatic%2A>a , mají výchozí dobu trvání , což znamená, že se automaticky ukončí, když jejich poslední dítě přestane hrát. Následující příklad <xref:System.Windows.Media.Animation.Storyboard> ukazuje, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jehož překládá na pět sekund, doba <xref:System.Windows.Media.Animation.DoubleAnimation> trvá všechny jeho podřízené objekty k dokončení.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Nastavením <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy <xref:System.Windows.Duration.TimeSpan%2A> kontejneru na hodnotu můžete vynutit <xref:System.Windows.Media.Animation.Timeline> přehrávání déle nebo kratší, než by přehrávala podřízená objekty. Pokud nastavíte hodnotu, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> která je menší než délka podřízených <xref:System.Windows.Media.Animation.Timeline> objektů <xref:System.Windows.Media.Animation.Timeline> časové osy kontejneru, podřízené objekty přestanou hrát, když to udělá časová osa kontejneru. Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.Storyboard> z předchozích příkladů na tři sekundy. V důsledku toho <xref:System.Windows.Media.Animation.DoubleAnimation> první zastaví postupující po třech sekundách, když má animovaný šířku cílového obdélníku na 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>Vlastnost RepeatBehavior  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> řídí, <xref:System.Windows.Media.Animation.Timeline> kolikrát opakuje jeho jednoduché trvání. Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnosti můžete určit, kolikrát se časová osa přehraje (iterace) <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>nebo celkovou dobu, po kterou má být přehrávána (opakování). <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A> V obou případech animace prochází tolik spuštění začátku do konce podle potřeby vyplnit požadovaný počet nebo dobu trvání. Ve výchozím nastavení mají časové `1.0`osy počet iterací , což znamená, že se přehrávají jednou a vůbec se neopakují.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, <xref:System.Windows.Media.Animation.DoubleAnimation> aby se hra pro dvojnásobek jeho jednoduché trvání zadáním počtu iterace.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Další příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, <xref:System.Windows.Media.Animation.DoubleAnimation> aby se hra pro polovinu jeho jednoduché trvání.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Pokud nastavíte vlastnost <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>a <xref:System.Windows.Media.Animation.Timeline> , opakování, dokud se nezastaví interaktivně nebo systémem časování. Následující příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, <xref:System.Windows.Media.Animation.DoubleAnimation> aby se hra neomezeně dlouho.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Další příklad naleznete v [tématu Opakování animace](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>Vlastnost AutoReverse  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> určuje, <xref:System.Windows.Media.Animation.Timeline> zda bude hrát dozadu na konci každé iterace vpřed. Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> a `true`do ; v důsledku toho animuje od nuly do 100 a pak od 100 do nuly. Hraje se celkem 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Při použití <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> hodnoty k <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> určení <xref:System.Windows.Media.Animation.Timeline> of <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a vlastnost, která <xref:System.Windows.Media.Animation.Timeline> je `true`, jedno opakování se skládá z jedné iterace vpřed následuje jeden zpětit.  Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> z předchozího příkladu <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> na a ze dvou. V důsledku toho <xref:System.Windows.Media.Animation.DoubleAnimation> se přehrává po dobu 20 sekund: vpřed po dobu pěti sekund, pozpátku po dobu pěti sekund, vpřed po dobu 5 sekund znovu a pak dozadu po dobu pěti sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Pokud časová osa kontejneru obsahuje podřízené <xref:System.Windows.Media.Animation.Timeline> objekty, obrátí se, když se tak stane časová osa kontejneru. Další příklady najdete [v tématu Určení, zda se časová osa automaticky obrátí](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>Vlastnost BeginTime  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> umožňuje určit, kdy se spustí časová osa.  Počáteční čas časové osy je relativní vzhledem k nadřazené časové ose. Počáteční čas nula sekund znamená, že časová osa začíná, jakmile se spustí nadřazený čas; jakákoli jiná hodnota vytvoří posun mezi tím, kdy se začne přehrávat nadřazená časová osa, a přehráváním podřízené časové osy. Například počáteční čas dvou sekund znamená, že časová osa se začne přehrávat, když její nadřazená doba dosáhne času dvou sekund. Ve výchozím nastavení mají všechny časové osy počáteční čas nula sekund. Můžete také nastavit čas zahájení časové `null`osy na , který zabrání spuštění časové osy. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]písmenu a) zadáte hodnotu null pomocí [rozšíření x:Null Markup Extension](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Všimněte si, že počáteční čas není použit pokaždé, když se časová osa opakuje z důvodu jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> nastavení. Pokud byste měli vytvořit animaci s <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund a <xref:System.Windows.Media.Animation.RepeatBehavior> a <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, by bylo 10 sekund zpoždění před animace hrál poprvé, ale ne pro každé následné opakování. Pokud by se však nadřazená časová osa animace restartovala nebo opakovala, došlo by k 10sekundové prodlevě.  
  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> je užitečná pro ohromující časové osy. Následující příklad vytvoří, <xref:System.Windows.Media.Animation.Storyboard> který <xref:System.Windows.Media.Animation.DoubleAnimation> má dva podřízené objekty. První animace má <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund a druhá <xref:System.Windows.Media.Animation.Timeline.Duration%2A> má 3 sekundy. Příklad nastaví <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> druhou <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund tak, aby se <xref:System.Windows.Media.Animation.DoubleAnimation> po prvních koncích začal přehrávat.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>FillBehavior Vlastnost  
 Když <xref:System.Windows.Media.Animation.Timeline> dosáhne konce jeho celkové aktivní trvání, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost určuje, zda se zastaví nebo drží jeho poslední hodnotu. Animace s <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "drží" jeho výstupní hodnotu: vlastnost, která je animována zachová poslední hodnotu animace. Hodnota příčin, <xref:System.Windows.Media.Animation.FillBehavior.Stop> které animace zastavit ovlivňuje jeho cílovou vlastnost po jejím ukončení.  
  
 Následující příklad vytvoří, <xref:System.Windows.Media.Animation.Storyboard> který <xref:System.Windows.Media.Animation.DoubleAnimation> má dva podřízené objekty. Oba <xref:System.Windows.Media.Animation.DoubleAnimation> objekty <xref:System.Windows.FrameworkElement.Width%2A> animovat z <xref:System.Windows.Shapes.Rectangle> 0 do 100. Prvky <xref:System.Windows.Shapes.Rectangle> mají neanimované <xref:System.Windows.FrameworkElement.Width%2A> hodnoty 500 [pixelů nezávislých na zařízení].  
  
- Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> první <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>na , výchozí hodnotu. V důsledku toho šířka Rectangle zůstane na 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> ukončení.  
  
- Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> second <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena <xref:System.Windows.Media.Animation.FillBehavior.Stop>na . Výsledkem je, <xref:System.Windows.FrameworkElement.Width%2A> že <xref:System.Windows.Shapes.Rectangle> druhý vrátí na 500 <xref:System.Windows.Media.Animation.DoubleAnimation> po koncích.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Vlastnosti, které řídí rychlost časové osy  
 Třída <xref:System.Windows.Media.Animation.Timeline> poskytuje tři vlastnosti pro určení jeho rychlost:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Určuje tuto rychlost vzhledem k nadřazené <xref:System.Windows.Media.Animation.Timeline>hodnotě, kdy čas postupuje pro . Hodnoty větší než jeden zvýšit <xref:System.Windows.Media.Animation.Timeline> rychlost <xref:System.Windows.Media.Animation.Timeline> a jeho podřízené objekty; hodnoty mezi nulou a jedním zpomalit. Hodnota jednoho označuje, <xref:System.Windows.Media.Animation.Timeline> že postupuje stejným tempem jako jeho nadřazený. Nastavení <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> časové osy kontejneru <xref:System.Windows.Media.Animation.Timeline> ovlivňuje také všechny jeho podřízené objekty.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Určuje procento časové <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osy, která byla využita k urychlení. Příklad najdete v [tématu Jak: Urychlit nebo zpomalit animaci](how-to-accelerate-or-decelerate-an-animation.md).
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- Určuje procento časové <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osy, která byla vynaložena na zpomalení. Příklad najdete v [tématu Jak: Urychlit nebo zpomalit animaci](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Animace a časování přehledu systému](animation-and-timing-system-overview.md)
- [Přehled událostí časování](timing-events-overview.md)
- [Témata s postupy](animation-and-timing-how-to-topics.md)
- [Ukázka chování časování animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
