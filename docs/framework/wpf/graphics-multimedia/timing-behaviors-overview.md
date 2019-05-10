---
title: Přehled chování časování
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 1433583c4c8e20533e7e18f1722d5481ffed3bbc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625676"
---
# <a name="timing-behaviors-overview"></a>Přehled chování časování
Toto téma popisuje chování časování animací a jiných <xref:System.Windows.Media.Animation.Timeline> objekty.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, byste měli znát základní animace funkce. Další informace najdete v tématu [přehled animace](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Typy časové osy  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment, který času. Poskytuje vlastnosti, které vám umožní zadat délku segmentu, když by se měl spustit, kolikrát bude opakovat, jak rychle čas postupuje v daném segmentu a další.  
  
 Třídy, které dědí z třídy časová osa poskytují další funkce, jako je přehrávání animace a média. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje následující <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ osy|Popis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstraktní základní třída pro <xref:System.Windows.Media.Animation.Timeline> objekty, které generují výstupní hodnoty animace vlastností.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje výstup z mediální soubor.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Typ <xref:System.Windows.Media.Animation.TimelineGroup> podřazených skupiny a ovládací prvky <xref:System.Windows.Media.Animation.Timeline> objekty.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Typ <xref:System.Windows.Media.Animation.ParallelTimeline> poskytující cílení informace pro časovou osu objekty, které obsahuje.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstraktní základní třída, která definuje chování časování|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstraktní třída pro <xref:System.Windows.Media.Animation.Timeline> objekty, které mohou obsahovat jiné <xref:System.Windows.Media.Animation.Timeline> objekty.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Vlastnosti, které řídí délku časové osy  
 A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a délka časovou osu lze popsat různými způsoby. Následující tabulka definuje několik podmínek pro popis délka časové osy.  
  
|Termín|Popis|Vlastnosti||||  
|----------|-----------------|----------------|-|-|-|  
|Jednoduché doba trvání|Dlouhá doba časové osy přístupu do jednoho dopředné iterace.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jednoho opakování|Doba, která je potřebná pro časovou osu přehrávání vpřed po a pokud <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost má hodnotu true, přehrávat pozpátku jednou.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktivního období|Doba, která je potřebná pro časovou osu pro dokončení všech opakování není určené jeho <xref:System.Windows.Media.Animation.RepeatBehavior> vlastnost.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Vlastnost doby trvání  
 Jak už jsme zmínili časovou osu reprezentuje segment, který času. Délka tohoto segmentu je určena na časové ose <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Pokud časové osy dosáhne konce jeho trvání, zastaví se přehrávání. Pokud na časové ose bylo podřízených časových os, přestane také přehrávání. V případě animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu. Doba trvání časové osy se někdy označuje jako jeho *jednoduché trvání*, k rozlišení mezi dobou trvání jedné iterace a celková délka času přehrávání animace, včetně opakování. Můžete určit dobu trvání pomocí omezené časové hodnoty nebo speciálními hodnotami <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>. Doba trvání animace musí se překládat na <xref:System.Windows.Duration.TimeSpan%2A> hodnoty, takže můžete přecházet mezi hodnotami.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Časové osy kontejneru, jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí po jejich posledního podřízeného zastaví přehrávání. Následující příklad ukazuje <xref:System.Windows.Media.Animation.Storyboard> jehož <xref:System.Windows.Media.Animation.Timeline.Duration%2A> přeloží na pět sekund, dobu trvá, jeho dceřiný <xref:System.Windows.Media.Animation.DoubleAnimation> objektů k dokončení.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Tím, že nastavíte <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osy kontejneru a <xref:System.Windows.Duration.TimeSpan%2A> hodnotu, můžete vynutit přehrávání delší nebo kratší než jeho dceřiný <xref:System.Windows.Media.Animation.Timeline> objekty se bude přehrávat. Pokud jste nastavili <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na hodnotu, která je menší než délka podřízené časové osy kontejneru <xref:System.Windows.Media.Animation.Timeline> objekty, podřízené <xref:System.Windows.Media.Animation.Timeline> objekty zastavit přehrávání, když provádí na časové ose kontejneru. Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.Duration%2A> z <xref:System.Windows.Media.Animation.Storyboard> z předchozích příkladů do tří sekund. V důsledku toho první <xref:System.Windows.Media.Animation.DoubleAnimation> zastaví průběh po tři sekundy, kdy se má animovat šířka cílového obdélníku do 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Vlastnost RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, kolikrát bude správce opakovat jednoduché interval. Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, můžete určit, kolikrát časovou osu přehrávání (iterace <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) nebo celková délka čas by měl play (o opakování <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). V obou případech se animace prochází podle potřeby zadejte požadovaný počet nebo dobu trvání spuštění mnoho začátku do konce. Ve výchozím nastavení, mají časové osy nepředstavuje počet iterací z `1.0`, což znamená, že Přehrát jednou a neopakuje vůbec.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> přehrát dvakrát jeho jednoduchý dobu zadáním nepředstavuje počet iterací.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> Hrajte poloviční jednoduché trvání.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Pokud jste nastavili <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> k <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> opakuje, dokud se zastaví interaktivně nebo v systému časování. V následujícím příkladu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> přehrát po neomezenou dobu.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Další příklad naleznete v tématu [opakování animace](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Autoreverse – vlastnost  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Vlastnost určuje, zda <xref:System.Windows.Media.Animation.Timeline> se přehraje zpětně na konci každé iterace vpřed. Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> k `true`; v důsledku toho animuje od nuly do 100 a ze 100 na hodnotu nula. Hraje pro celkem 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Při použití <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> hodnotu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost, která <xref:System.Windows.Media.Animation.Timeline> je `true`, jednoho opakování se skládá z jednoho dopředné iterace, následovaný jednou zpětně iterace.  Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation> z předchozího příkladu k <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> dvou. V důsledku toho <xref:System.Windows.Media.Animation.DoubleAnimation> přehraje po dobu 20 sekund: předávání pro předávání pět sekund, zpětné pět sekund, po dobu 5 sekund znovu a pak zpět na pět sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Pokud se časové osy kontejner má podřízený <xref:System.Windows.Media.Animation.Timeline> objektů, se obrátí na časové ose kontejneru provede. Další příklady najdete v tématu [zadejte časové ose automatické rezervace](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Vlastnost BeginTime  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Vlastnost vám umožní zadat při spuštění časové osy.  Čas zahájení časové osy je relativní vzhledem k její nadřazené časové osy. Počáteční čas nula sekund znamená, že na časové ose spustí jako jeho nadřazený spustí; jakákoli jiná hodnota vytvoří posun mezi při spuštění na nadřazené časové ose přehrávání a kdy hraje podřízené časové osy. Například čas zahájení dvou sekund znamená, že na časové ose se začne přehrávat při jeho nadřazený objekt dosáhla čas 2 sekundy. Ve výchozím nastavení mají všechny časové osy čas zahájení nula sekund. Můžete také nastavit časové osy čas pro zahájení `null`, která zabraňuje spuštění na časové ose. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zadejte hodnotu null pomocí [x: Null – rozšíření značek](../../xaml-services/x-null-markup-extension.md).  
  
 Všimněte si, že je čas zahájení použít pokaždé, když se opakuje časovou osu z důvodu jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> nastavení. Pokud byste chtěli vytvořit animaci s <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund a <xref:System.Windows.Media.Animation.RepeatBehavior> z <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, by docházet k 10 sekundách zpoždění opakování animace poprvé, ale ne pro každé po sobě jdoucích opakování. Ale pokud časovou osu animace nadřazené restartování nebo opakujte, 10 sekund by dojít ke zpoždění.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Vlastnost je užitečná pro odstupňování časové osy. Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard> , který má dva podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty. Má první animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund, a druhý <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 sekundy. V příkladu je nastavena <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> druhého <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, takže se začne přehrávat po prvním <xref:System.Windows.Media.Animation.DoubleAnimation> skončí.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>Fillbehavior – vlastnost  
 Když <xref:System.Windows.Media.Animation.Timeline> dosáhne konce jeho celkové trvání aktivní <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost určuje, zda se zastaví, nebo uchovává svou poslední hodnotu. Animace s <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "obsahuje" jeho výstupní hodnota: animované vlastnosti zachová poslední hodnotu animace. Hodnota <xref:System.Windows.Media.Animation.FillBehavior.Stop> , která způsobí zastavení animace po jeho skončení by to ovlivnilo její vlastnost target.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard> , který má dva podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty. Obě <xref:System.Windows.Media.Animation.DoubleAnimation> animace objektů <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> od 0 do 100. <xref:System.Windows.Shapes.Rectangle> Elementy mají jiné animovat <xref:System.Windows.FrameworkElement.Width%2A> hodnoty 500 [zařízeních nezávislých na pixelech].  
  
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnosti prvního <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena na <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, výchozí hodnota. V důsledku toho zůstane šířkou pravoúhelníku 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> skončí.  
  
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost druhého <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena na <xref:System.Windows.Media.Animation.FillBehavior.Stop>. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> druhého <xref:System.Windows.Shapes.Rectangle> se vrátí do 500 po <xref:System.Windows.Media.Animation.DoubleAnimation> skončí.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Vlastnosti, které řídí rychlosti časové osy  
 <xref:System.Windows.Media.Animation.Timeline> Třída poskytuje tři vlastnosti k určení jeho rychlost:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – Tento kurz, relativně k nadřazenému, jakou dobu postupuje pro Určuje <xref:System.Windows.Media.Animation.Timeline>. Hodnoty větší než jedna zvýšení rychlosti <xref:System.Windows.Media.Animation.Timeline> a jeho podřízených <xref:System.Windows.Media.Animation.Timeline> objektů; hodnoty mezi 0 a 1 zpomalit ho. Hodnota objektu znamená, že <xref:System.Windows.Media.Animation.Timeline> postupuje za stejnou sazbu jako jeho nadřazený objekt. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Časové osy kontejneru ovlivní všechny jeho podřízené <xref:System.Windows.Media.Animation.Timeline> také objekty.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – Určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy strávený zrychlení. Příklad najdete v tématu [jak: Zrychlení a zpomalení animace](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -Určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy strávený zpomalení. Příklad najdete v tématu [jak: Zrychlení a zpomalení animace](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled animace a systému časování](animation-and-timing-system-overview.md)
- [Přehled událostí časování](timing-events-overview.md)
- [Témata s postupy](animation-and-timing-how-to-topics.md)
- [Ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970)
