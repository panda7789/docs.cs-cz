---
title: Přehled událostí časování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: 91e335f4d5adaa5279fb16805604f2e2848eeb8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002388"
---
# <a name="timing-events-overview"></a>Přehled událostí časování
Toto téma popisuje, jak používat k dispozici na pěti události časování <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> objekty.  
  
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, by měl pochopit, jak vytvořit a používat animace. Abyste mohli začít s animací, najdete v článku [přehled animace](animation-overview.md).  
  
 Existuje několik způsobů animace vlastností v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Použití objektů scénáře** (značek a kódu): Můžete použít <xref:System.Windows.Media.Animation.Storyboard> objektů můžete uspořádat a distribuovat animací na jeden nebo více objektů. Příklad najdete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Pomocí místní animace** (jenom kód): Můžete použít <xref:System.Windows.Media.Animation.AnimationTimeline> objekty přímo k vlastnostem, animace. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Pomocí hodiny** (jenom kód): Můžete explicitně spravovat vytváření hodiny a distribuovat hodiny animace sami.  Příklad najdete v tématu [animace vlastnosti pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Vzhledem k tomu, že lze využít v značek a kódu, příklady v tomto přehledu používají <xref:System.Windows.Media.Animation.Storyboard> objekty. Koncepty popsané však můžete použít pro jiné metody animace vlastností.  
  
### <a name="what-is-a-clock"></a>Co je ve formátu?  
 Časová osa, samostatně, nic nedělá skutečně jiné než popisují část času. Je na časové ose <xref:System.Windows.Media.Animation.Clock> objekt, který odvádí skutečnou práci: udržuje pro časovou osu s časováním běhový stav. Ve většině případů, jako je například pomocí scénářů při se automaticky vytvoří hodin pro vaši časovou osu. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně pomocí <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metody. Další informace o <xref:System.Windows.Media.Animation.Clock> objekty, najdete [animace a časování přehledu systému](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Proč používat události?  
 S výjimkou jednoho (hledání zarovnané posledního impulzu), všechny operace interaktivní časování jsou asynchronní. Neexistuje žádný způsob, jak budete vědět, přesně tak když se spustí. Pokud máte jiný kód, který je závislý na vaše operace časování, který může být problém. Předpokládejme, že byste chtěli zastavit časovou osu, která animace obdélníku. Po ukončení na časové ose, změnit barvu obdélníku.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 V předchozím příkladu druhý řádek kódu může spustit před zastaví scénáře. Důvodem je skutečnost zastavení je asynchronní operace. "Požadavek na zastavení" typů, která není zpracována až do další značky modul časování oznamovat časové osy nebo hodiny zastavit vytvoří.  
  
 Provádět příkazy po dokončení časové osy, použijte události časování. V následujícím příkladu se používá obslužnou rutinu události a změňte barvu obdélník po scénář se zastaví přehrávání.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Podrobnější příklad naleznete v tématu [změny stavu dostávat oznámení při hodin](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Veřejné události  
 <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> obě třídy poskytují pět události časování. V následující tabulce jsou uvedeny tyto události a podmínky, které je.  
  
|Událost|Aktivace interaktivní operace|Jiné triggery|  
|-----------|--------------------------------------|--------------------|  
|**Dokončeno**|Přejít k vyplnění|Hodiny se dokončí.|  
|**CurrentGlobalSpeedInvalidated**|Pozastavit, obnovit, hledání, nastavit poměr rychlost, přejděte k vyplnění, zastavit|Hodiny obrátí, zrychluje doručování, spuštění nebo zastavení.|  
|**CurrentStateInvalidated**|Začněte tím, že přeskočit na to, zastavit|Hodiny spustí, zastaví, nebo vyplní.|  
|**CurrentTimeInvalidated**|Začít, hledání, přejděte k vyplnění, zastavit|Postupuje hodiny.|  
|**RemoveRequested**|odebrat||  
  
## <a name="ticking-and-event-consolidation"></a>Tikání a konsolidaci událostí  
 Když animace objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je modul časování, který spravuje animace. Časování stroj sleduje průběh čas a vypočítá stavu každou animaci. Nezáleží na počtu průchodů takové vyhodnocení za sekundu. Tyto zkušební předá jsou označovány jako "taktů."  
  
 Zatímco značky docházet často, je možné pro mnoho věcí, které se provedou mezi značkami. Například časovou osu může být zastavit, spustit a zastavit znovu, v takovém případě jejím aktuálním stavu se změnili třikrát. Teoreticky vzato události může být vyvolána více než jednou v jedné značky; modul časování však konsoliduje události, tak, aby každé události může být vyvolána oznámením nejvýše jednou za značek.  
  
## <a name="registering-for-events"></a>Registrace k událostem  
 Existují dva způsoby, jak zaregistrovat pro události časování: můžete zaregistrovat pomocí časové osy nebo s hodinami vytvořené z časové osy. Registrace pro události přímo s hodinami je celkem jasné, i když lze provést pouze z kódu. Můžete se zaregistrovat pro události se časovou osu z značek nebo kódu. Další část popisuje postup registrace pro události hodiny se časové osy.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrace k událostem hodiny s časovou osu  
 I když časové osy <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, a <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> události se zobrazí k časové ose, registrace pro tyto události ve skutečnosti přidruží obslužné rutiny události s <xref:System.Windows.Media.Animation.Clock> vytvoří pro časovou osu.  
  
 Když si zaregistrujete <xref:System.Windows.Media.Animation.Timeline.Completed> událostí na časové ose, například je skutečně tím rozdílem, systém a zaregistrujte se <xref:System.Windows.Media.Animation.Clock.Completed> události každé hodiny, který je vytvořen pro časovou osu. V kódu, musíte zaregistrovat pro tuto událost před <xref:System.Windows.Media.Animation.Clock> se vytvoří pro tento osu; v opačném případě nebude přijímat oznámení. K tomu dojde automaticky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; analyzátor automaticky zaregistruje událost před <xref:System.Windows.Media.Animation.Clock> se vytvoří.  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace a systému časování](animation-and-timing-system-overview.md)
- [Přehled animace](animation-overview.md)
- [Přehled chování časování](timing-behaviors-overview.md)
