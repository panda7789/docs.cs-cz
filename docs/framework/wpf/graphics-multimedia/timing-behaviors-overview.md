---
title: "Přehled chování časování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9305b69927a1ed0ad4f154ab972316f3dee951e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="timing-behaviors-overview"></a>Přehled chování časování
Toto téma popisuje chování časování animace a jiných <xref:System.Windows.Media.Animation.Timeline> objekty.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit v tomto tématu byste měli seznámit s funkcemi základní animace. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Časová osa typy  
 A <xref:System.Windows.Media.Animation.Timeline> představuje segment času. Poskytuje vlastnosti, které vám umožní zadat délku segmentu, pokud by se měl spustit, kolikrát se bude opakovat, jak rychle čas hodnoty v tomto segmentu a další.  
  
 Třídy, které dědí z třídy časová osa poskytují další funkce, například přehrávání animace a média. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ časové osy|Popis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstraktní základní třída pro <xref:System.Windows.Media.Animation.Timeline> objekty, které generovat výstup hodnoty pro vlastnosti animace.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje výstup ze souboru média.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Typ <xref:System.Windows.Media.Animation.TimelineGroup> podřazených skupin a ovládací prvky <xref:System.Windows.Media.Animation.Timeline> objekty.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Typ <xref:System.Windows.Media.Animation.ParallelTimeline> poskytující zaměřená na informace o časová osa objekty, které obsahuje.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstraktní základní třída, která definuje chování časování.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstraktní třída pro <xref:System.Windows.Media.Animation.Timeline> objekty, které může obsahovat jiné <xref:System.Windows.Media.Animation.Timeline> objekty.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Vlastnosti, které řídí délku časové osy  
 A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a délka časové osy lze popsat různými způsoby. Následující tabulka definuje několik podmínek pro popisující délka časové osy.  
  
|Termín|Popis|Vlastnosti||||  
|----------|-----------------|----------------|-|-|-|  
|Jednoduché doba trvání|Délka doby trvání časové osy, aby jeden dopředného iterace.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jeden opakování|Doba, která je potřebná pro časové osy přehrávání dál po a pokud <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost na hodnotu true, přehrání zpětné jednou.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktivní období|Doba, která je potřebná pro časové osy pro dokončení všech opakování určeného jeho <xref:System.Windows.Media.Animation.RepeatBehavior> vlastnost.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Vlastnost doba trvání  
 Jak jsme uvedli časové osy představuje segment času. Délka tohoto segmentu je dáno časové ose <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Pokud termín dosáhne konce jeho trvání, zastaví se přehrávání. Pokud časovou osu podřízené časových os, jejich zastavit také přehrávání. V případě animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu. Doba trvání časové osy se někdy označuje jako jeho *jednoduché trvání*, k rozlišení mezi trvání jeden iterace a celková délka času animace se přehraje, včetně opakování. Můžete zadat dobu trvání pomocí hodnotu konečný čas nebo speciální hodnoty <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>. Doba trvání animace společnosti musí se překládat na <xref:System.Windows.Duration.TimeSpan%2A> hodnotu, může přecházet mezi hodnotami.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kontejner časových os, jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí při jejich posledního podřízeného zastavení přehrávání. Následující příklad ukazuje <xref:System.Windows.Media.Animation.Storyboard> jejichž <xref:System.Windows.Media.Animation.Timeline.Duration%2A> přeloží na pět sekund, dobu trvá všechny jeho podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty, které chcete dokončit.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Nastavením <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kontejneru osy a <xref:System.Windows.Duration.TimeSpan%2A> hodnotu, můžete vynutit přehrávání delší nebo kratší než jeho podřízené <xref:System.Windows.Media.Animation.Timeline> by přehrání objekty. Pokud nastavíte <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na hodnotu, která je menší než délka časová osa kontejneru podřízené <xref:System.Windows.Media.Animation.Timeline> objekty, podřízená <xref:System.Windows.Media.Animation.Timeline> objekty zastavit přehrávání při nemá časovou osu kontejneru. Následující příklad nastavuje <xref:System.Windows.Media.Animation.Timeline.Duration%2A> z <xref:System.Windows.Media.Animation.Storyboard> z předchozích ukázkách do 3 sekund. V důsledku toho první <xref:System.Windows.Media.Animation.DoubleAnimation> zastaví pokročíte po tři sekundy, když ho má animovaný šířku obdélníku cíl na 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Vlastnost RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, kolikrát bude správce opakovat jeho trvání jednoduché. Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, můžete určit, jak často plní časová osa (iterace <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) nebo celková délka čas by měl přehrání (o opakování <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). V obou případech animace projde mnoho začátku do konce běží podle potřeby zadejte požadovaný počet nebo doba trvání. Ve výchozím nastavení, časové osy mít iterace `1.0`, což znamená jejich přehrání jednou a neopakuje vůbec.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> přehrání dvakrát jeho jednoduché doby trvání zadáním počet iterací.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Další příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> přehrání poloviční jednoduché dobu.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Pokud nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> k <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> opakuje, dokud nebude zastaven interaktivně nebo systémem časování. Následující příklad používá <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost, aby <xref:System.Windows.Media.Animation.DoubleAnimation> přehrání po neomezenou dobu.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Další příklad najdete v tématu [opakování animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Vlastnost AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Vlastnost určuje, zda <xref:System.Windows.Media.Animation.Timeline> zpětné přehraje na konci každé iteraci předat dál. V následujícím příkladu se nastaví na <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation> k `true`; v důsledku toho se animuje od nuly do 100 a od 100 na hodnotu nula. Přehrání celkem 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Při použití <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> hodnotu k určení <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost této <xref:System.Windows.Media.Animation.Timeline> je `true`, jeden opakování se skládá z jednoho dopředného iterace následuje jeden zpětné iterací.  Následující příklad nastavuje <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation> z předchozího příkladu k <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> dva. V důsledku toho <xref:System.Windows.Media.Animation.DoubleAnimation> hraje 20 sekund: předávání pro předávání pět sekund, zpětné pro pět sekund, po dobu 5 sekund znovu a pak zpětně pro pět sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Pokud má časová osa kontejneru podřízené <xref:System.Windows.Media.Animation.Timeline> objekty, budou obrátit při nemá časovou osu kontejneru. Další příklady najdete v tématu [určit, zda časová osa automaticky obrátí](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Vlastnost BeginTime  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Vlastnost umožňuje určit při spuštění časové osy.  Čas zahájení časové osy je relativní vzhledem ke své nadřazené časové ose. Počáteční čas nula sekund znamená, které časovou osu spustí ihned po jeho nadřazený spustí; žádné jiné hodnoty vytvoří posun při časovou osu podřízené hraje až při spuštění nadřazené časovou osu přehrávání. Například počáteční čas dvou sekund znamená, spustí časovou osu přehrávání jeho nadřazený objekt se dosáhne doba dvou sekund. Ve výchozím nastavení mají všechny časové osy počáteční čas nula sekund. Můžete také nastavit časové osy začít dobu `null`, který brání spouštění časovou osu. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zadejte hodnotu null. pomocí [x: Null – rozšíření značek](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Všimněte si, že počáteční čas není použita pokaždé, když se opakuje časové osy z důvodu jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> nastavení. Pokud byste chtěli vytvořit animace s <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund a <xref:System.Windows.Media.Animation.RepeatBehavior> z <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, by prodlevu 10 sekund před animace se přehrávají poprvé, ale ne pro každý následných opakování. Kdyby došlo k restartování nebo opakujte má animace nadřazené časové osy by tomu prodlevu 10 sekund.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Vlastnost je užitečná pro rozptylu časové osy. Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard> má dva podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty. Má první animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund, a druhý <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 sekund. V příkladu je nastavena <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> druhého <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, takže to začne přehrávání po první <xref:System.Windows.Media.Animation.DoubleAnimation> ukončí.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>Vlastnost FillBehavior  
 Když <xref:System.Windows.Media.Animation.Timeline> dosáhne konce jeho celkový active trvání <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost určuje, zda se zastaví, nebo obsahuje jeho poslední hodnotu. Animace s <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "obsahuje" jeho hodnota výstupu: vlastnost se animovaný uchovává poslední hodnotu animace. Hodnota <xref:System.Windows.Media.Animation.FillBehavior.Stop> způsobí, který ovlivňuje jeho vlastnost target po jeho skončení zastavení animace.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.Animation.Storyboard> má dva podřízené <xref:System.Windows.Media.Animation.DoubleAnimation> objekty. Obě <xref:System.Windows.Media.Animation.DoubleAnimation> animace objektů <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> od 0 do 100. <xref:System.Windows.Shapes.Rectangle> Prvky mít bez animací <xref:System.Windows.FrameworkElement.Width%2A> hodnoty 500 [nezávislé pixelů zařízení].  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost první <xref:System.Windows.Media.Animation.DoubleAnimation> je nastaven na <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, výchozí hodnota. V důsledku toho šířku rámeček zůstává na 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> ukončí.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost druhý <xref:System.Windows.Media.Animation.DoubleAnimation> je nastaven na <xref:System.Windows.Media.Animation.FillBehavior.Stop>. V důsledku toho <xref:System.Windows.FrameworkElement.Width%2A> druhého <xref:System.Windows.Shapes.Rectangle> se vrátí do 500 po <xref:System.Windows.Media.Animation.DoubleAnimation> ukončí.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Vlastnosti, které řídí rychlosti časové osy  
 <xref:System.Windows.Media.Animation.Timeline> Třída poskytuje tři vlastnosti pro zadání jeho rychlost:  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Určuje, že rychlost relativně k jeho nadřazeným prvkem, ve kterém čas hodnoty pro <xref:System.Windows.Media.Animation.Timeline>. Hodnoty větší než jedna zvýšení rychlosti <xref:System.Windows.Media.Animation.Timeline> a jeho podřízené <xref:System.Windows.Media.Animation.Timeline> objekty; hodnoty mezi 0 a 1 zpomalovat práci. Hodnota jednoho Určuje, že <xref:System.Windows.Media.Animation.Timeline> postupuje stejnou rychlostí jako svůj nadřazený uzel. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Nastavení časová osa kontejneru ovlivňuje všechny jeho podřízené <xref:System.Windows.Media.Animation.Timeline> také objekty.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy stráví urychlení. Příklad, naleznete v části [postupy: zvýšení nebo snížení hardwarové akcelerace animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-Určuje procento <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy stráví zpomaluje. Příklad, naleznete v části [postupy: zvýšení nebo snížení hardwarové akcelerace animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animace a systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Přehled událostí časování](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970)
