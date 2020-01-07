---
title: Přehled chování časování
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559947"
---
# <a name="timing-behaviors-overview"></a>Přehled chování časování
Toto téma popisuje chování časování animací a dalších <xref:System.Windows.Media.Animation.Timeline> objektů.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Pro pochopení tohoto tématu byste měli být obeznámeni se základními funkcemi animace. Další informace najdete v [přehledu animace](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Typy časové osy  
 <xref:System.Windows.Media.Animation.Timeline> představuje segment času. Poskytuje vlastnosti, které vám umožní určit délku tohoto segmentu, kdy by měl začít, kolikrát se bude opakovat, jak dlouho se v tomto segmentu a dalších.  
  
 Třídy, které dědí z třídy Timeline, poskytují další funkce, jako je například animace a přehrávání multimédií. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje následující typy <xref:System.Windows.Media.Animation.Timeline>.  
  
|Typ časové osy|Popis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstraktní základní třída pro objekty <xref:System.Windows.Media.Animation.Timeline>, které generují výstupní hodnoty pro animování vlastností.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje výstup z mediálního souboru.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Typ <xref:System.Windows.Media.Animation.TimelineGroup>, který seskupí a řídí podřízené objekty <xref:System.Windows.Media.Animation.Timeline>.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Typ <xref:System.Windows.Media.Animation.ParallelTimeline>, který poskytuje informace o cílení pro objekty časové osy, které obsahuje.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstraktní základní třída, která definuje chování časování.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstraktní třída pro objekty <xref:System.Windows.Media.Animation.Timeline>, které mohou obsahovat další objekty <xref:System.Windows.Media.Animation.Timeline>.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Vlastnosti, které řídí délku časové osy  
 <xref:System.Windows.Media.Animation.Timeline> představuje segment času a délku časové osy lze popsat různými způsoby. Následující tabulka definuje několik podmínek pro popis délky časové osy.  
  
|Termín|Popis|Vlastnosti||||  
|----------|-----------------|----------------|-|-|-|  
|Jednoduchá doba trvání|Doba, po kterou časová osa trvá provedení jediného dopředné iterace.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jedno opakování|Doba, po kterou časová osa trvá přehrání dopředu a v případě, že je vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> pravdivá, se přehraje zpět.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktivní období|Doba, kterou časová osa trvá k dokončení všech opakování určených vlastností <xref:System.Windows.Media.Animation.RepeatBehavior>.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Vlastnost Duration  
 Jak už jsme uvedli, časová osa představuje segment času. Délka tohoto segmentu je určena <xref:System.Windows.Media.Animation.Timeline.Duration%2A>časové osy. Když časová osa dosáhne konce své doby trvání, zastaví se přehrávání. Pokud časová osa obsahuje podřízené časové osy, přestanou také hrát. V případě animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> určuje, jak dlouho animace trvá přechodu od počáteční hodnoty k její konečné hodnotě. Doba trvání časové osy se někdy označuje jako *Jednoduchá doba trvání*, aby se lišila doba trvání jedné iterace a celková doba, kterou animace přehrává, včetně opakování. Můžete zadat dobu trvání s použitím omezené hodnoty času nebo zvláštních hodnot <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>. Doba trvání animace by se měla překládat na hodnotu <xref:System.Windows.Duration.TimeSpan%2A>, takže může přejít mezi hodnotami.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.Animation.Timeline.Duration%2A> po dobu pěti sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Časové osy kontejneru, například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, mají výchozí dobu trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že se automaticky ukončí, když se jejich poslední podřízená položka přestane přehrávat. Následující příklad ukazuje <xref:System.Windows.Media.Animation.Storyboard>, jehož <xref:System.Windows.Media.Animation.Timeline.Duration%2A> se přeloží na pět sekund, což je doba, po kterou všechny své podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty dokončí.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Nastavením <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy kontejneru na <xref:System.Windows.Duration.TimeSpan%2A> hodnotu můžete vynutit, aby se přehrály déle nebo méně, než se přestanou přecházet do jejich podřízených objektů <xref:System.Windows.Media.Animation.Timeline>. Pokud <xref:System.Windows.Media.Animation.Timeline.Duration%2A> nastavíte na hodnotu, která je menší než délka podřízených objektů <xref:System.Windows.Media.Animation.Timeline> časové osy kontejneru, přestanou podřízené objekty <xref:System.Windows.Media.Animation.Timeline> přecházet, když je tato časová osa kontejneru. Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.Storyboard> z předchozích příkladů na tři sekundy. V důsledku toho se první <xref:System.Windows.Media.Animation.DoubleAnimation> zastaví po třech sekundách, když má animovanou šířku cílového obdélníku na 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Vlastnost RepeatBehavior  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ovládacího prvku <xref:System.Windows.Media.Animation.Timeline> řídí, kolikrát se opakuje jeho jednoduchá doba trvání. Pomocí vlastnosti <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> můžete určit, kolikrát se má časová osa přehrávat (iterace <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>), nebo celkovou dobu, kterou by měla přehrát (opakování <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). V obou případech animace projde až do tolika začátku až do konce, aby bylo možné vyplnit požadovaný počet nebo dobu trvání. Ve výchozím nastavení mají časové osy počet iterací `1.0`, což znamená, že se jednou hrají a neopakují se vůbec.  
  
 V následujícím příkladu je použita vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> k provedení <xref:System.Windows.Media.Animation.DoubleAnimation> přehrání pro dvojnásobek své jednoduché doby trvání zadáním počtu iterací.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 V dalším příkladu se pomocí vlastnosti <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> nastaví, aby se <xref:System.Windows.Media.Animation.DoubleAnimation> hrály po polovinu jeho jednoduchého trvání.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Pokud nastavíte vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> se opakuje, dokud se nezastaví interaktivně nebo systémem časování. V následujícím příkladu se pomocí vlastnosti <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> nastaví, aby se <xref:System.Windows.Media.Animation.DoubleAnimation> hrály po neomezenou dobu.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Další příklad naleznete v tématu [opakování animace](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Vlastnost Reverse  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> určuje, zda se <xref:System.Windows.Media.Animation.Timeline> na konci každé předávací iterace přehraje zpět. Následující příklad nastaví vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na `true`; Výsledkem je, že se animuje od nuly do 100 a pak od 100 do nuly. Hraje se celkem 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Použijete-li <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> hodnotu k určení <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> a vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> tohoto <xref:System.Windows.Media.Animation.Timeline> `true`, bude jediným opakováním sestává jedna předávací iterace následovaná jedním zpětným iterací.  Následující příklad nastaví <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> z předchozího příkladu na <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> dvou. V důsledku toho se <xref:System.Windows.Media.Animation.DoubleAnimation> přehrává po dobu 20 sekund: dopředu po dobu pěti sekund, zpětně po dobu 5 sekund, předejte ji na 5 sekund znovu a pak na pět sekund zpětně.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Pokud má časová osa kontejneru podřízené <xref:System.Windows.Media.Animation.Timeline> objekty, obrátí se, až bude časová osa kontejneru. Další příklady naleznete v tématu [určení, zda se časová osa automaticky obrátí](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Vlastnost BeginTime  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> umožňuje určit, kdy se časová osa spustí.  Čas zahájení časové osy je relativní vzhledem ke své nadřazené časové ose. Čas zahájení nula sekund znamená, že se časová osa začne hned po zahájení nadřazeného objektu; jakákoli jiná hodnota vytvoří posun mezi tím, kdy se spustí nadřazená časová osa, a když hraje podřízenou časovou osu. Například čas zahájení dvou sekund znamená, že se časová osa začne přehrávat, když se její nadřazená doba dosáhla dvou sekund. Ve výchozím nastavení mají všechny časové osy čas zahájení nula sekund. Můžete také nastavit čas zahájení časové osy na `null`, což zabrání spuštění časové osy. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zadáte hodnotu null pomocí [rozšíření značek x:null](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Všimněte si, že čas zahájení není aplikován při každém opakování časové osy z důvodu jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>ho nastavení. Pokud byste chtěli vytvořit animaci s <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund a <xref:System.Windows.Media.Animation.RepeatBehavior> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, před prvním přehráním animace by došlo k prodlevě 10 sekund, ale ne pro každé opakování. Pokud se ale nadřazená časová osa animace restartovala nebo zopakuje, dojde k prodlevě o délce 10 sekund.  
  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> je užitečná pro střídavé navýšení časových os. Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard>, který má dva podřízené objekty <xref:System.Windows.Media.Animation.DoubleAnimation>. První animace je <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund a druhá má <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 sekundy. V příkladu se nastaví <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> druhé <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, aby se začátek přehrával po prvním <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>Vlastnost FillBehavior  
 Pokud <xref:System.Windows.Media.Animation.Timeline> dosáhne konce celkové aktivní doby trvání, vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> určuje, zda se zastaví nebo drží poslední hodnota. Animace s <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "drží" svou výstupní hodnotu: vlastnost, která je animována, zachová poslední hodnotu animace. Hodnota <xref:System.Windows.Media.Animation.FillBehavior.Stop> způsobí, že animace přestane mít vliv na jeho cílovou vlastnost po jeho ukončení.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard>, který má dva podřízené objekty <xref:System.Windows.Media.Animation.DoubleAnimation>. Oba <xref:System.Windows.Media.Animation.DoubleAnimation> objekty animuje <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> od 0 do 100. Prvky <xref:System.Windows.Shapes.Rectangle> mají neanimované <xref:System.Windows.FrameworkElement.Width%2A> hodnoty 500 [pixelů nezávislé na zařízení].  
  
- Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> prvního <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena na hodnotu <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, výchozí hodnota. Výsledkem je, že šířka obdélníku zůstane v 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> končí.  
  
- Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> druhého <xref:System.Windows.Media.Animation.DoubleAnimation> je nastavena na hodnotu <xref:System.Windows.Media.Animation.FillBehavior.Stop>. V důsledku toho se <xref:System.Windows.FrameworkElement.Width%2A> druhého <xref:System.Windows.Shapes.Rectangle> po <xref:System.Windows.Media.Animation.DoubleAnimation> ukončení vrátí na 500.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Vlastnosti, které řídí rychlost časové osy  
 Třída <xref:System.Windows.Media.Animation.Timeline> poskytuje tři vlastnosti pro určení rychlosti:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – určuje, že je sazba relativní vzhledem ke své nadřazené položce, v jakém čase probíhá <xref:System.Windows.Media.Animation.Timeline>. Hodnoty větší než jedna zvyšují rychlost <xref:System.Windows.Media.Animation.Timeline> a jejích podřízených <xref:System.Windows.Media.Animation.Timeline> objektů; hodnoty od nuly a jednoho zpomalení. Hodnota One znamená, že <xref:System.Windows.Media.Animation.Timeline> pokrok se stejnou sazbou jako její nadřazená položka. Nastavení <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> časové osy kontejneru ovlivní také všechny její podřízené objekty <xref:System.Windows.Media.Animation.Timeline>.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> stráveného zrychlení. Příklad naleznete v tématu [How to: zrychle and zpomalit animaci](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> – určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy strávené zpomalením. Příklad naleznete v tématu [How to: zrychle and zpomalit animaci](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled animace a systému časování](animation-and-timing-system-overview.md)
- [Přehled událostí časování](timing-events-overview.md)
- [Postupy](animation-and-timing-how-to-topics.md)
- [Ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970)
