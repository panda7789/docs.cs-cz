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
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145407"
---
# <a name="timing-events-overview"></a>Přehled událostí časování
Toto téma popisuje, jak používat pět <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> časování události, které jsou k dispozici na a objekty.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste pochopit, jak vytvářet a používat animace. Chcete-li začít s animací, podívejte se na [přehled animací](animation-overview.md).  
  
 Existuje několik způsobů, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animovat vlastnosti v aplikaci :  
  
- **Použití objektů scénáře** (značky a kód): Objekty můžete použít <xref:System.Windows.Media.Animation.Storyboard> k uspořádání a distribuci animací do jednoho nebo více objektů. Příklad například viz [Animate vlastnost pomocí storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Použití místních animací** (pouze <xref:System.Windows.Media.Animation.AnimationTimeline> kód): Objekty můžete aplikovat přímo na vlastnosti, které animují. Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Použití hodin** (pouze kód): Můžete explicitně spravovat tvorbu hodin a distribuovat hodiny animace sami.  Příklad naleznete v [tématu Animate vlastnost pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Vzhledem k tomu, že je můžete použít ve <xref:System.Windows.Media.Animation.Storyboard> značkách a kódu, příklady v tomto přehledu používají objekty. Popsané koncepty však lze použít na jiné metody animace vlastností.  
  
### <a name="what-is-a-clock"></a>Co jsou hodiny?  
 Časová osa sama o sobě ve skutečnosti nedělá nic jiného než popisuje segment času. Je to objekt časové <xref:System.Windows.Media.Animation.Clock> osy, který provádí skutečnou práci: udržuje časování související s časovým časem stavu časové osy. Ve většině případů, například při použití scénářů, hodiny se vytvoří automaticky pro vaši časovou osu. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> pomocí metody. Další informace <xref:System.Windows.Media.Animation.Clock> o objektech naleznete v tématu [Přehled systému animace a časování](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Proč používat události?  
 S výjimkou jednoho (hledání zarovnány s poslední klíště), všechny interaktivní operace časování jsou asynchronní. Neexistuje žádný způsob, jak přesně vědět, kdy budou provedeny. To může být problém, pokud máte jiný kód, který je závislý na operaci časování. Předpokládejme, že chcete zastavit časovou osu, která animovala obdélník. Po zastavení časové osy změníte barvu obdélníku.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 V předchozím příkladu druhý řádek kódu může spustit před zastavením scénáře. To proto, že zastavení je asynchronní operace. Sdělit časovou osu nebo hodiny zastavit vytvoří "stop požadavek" druhů, které nejsou zpracovány, dokud časování motoru další klíště.  
  
 Chcete-li po dokončení časové osy spustit příkazy, použijte události časování. V následujícím příkladu obslužná rutina události se používá ke změně barvy obdélníku po přehrání storyboard zastaví přehrávání.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Podrobnější příklad najdete v tématu [Příjem oznámení při změny stavu hodiny](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Veřejné události  
 A <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> třídy poskytují pět časování události. V následující tabulce jsou uvedeny tyto události a podmínky, které je aktivují.  
  
|Událost|Spuštění interaktivní operace|Další aktivační události|  
|-----------|--------------------------------------|--------------------|  
|**Dokončeno**|Přeskočit k vyplnění|Hodiny se dokončují.|  
|**Currentglobalspeedinvalidated**|Pauza, pokračovat, hledat, nastavit poměr rychlosti, přeskočit k vyplnění, zastavit|Hodiny se obrátí, zrychlují, spouští nebo zastavují.|  
|**Currentstateinvalidated**|Začněte, přeskočte na vyplnění, zastavte|Hodiny se spustí, zastaví nebo vyplní.|  
|**CurrentTimeInvalidated**|Začněte, hledejte, přeskočte vyplnit, zastavit|Hodiny postupují.|  
|**OdebratRequested**|Odebrat||  
  
## <a name="ticking-and-event-consolidation"></a>Zaškrtnutí a konsolidace událostí  
 Při animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objektů v aplikaci je modul časování, který spravuje animace. Modul časování sleduje průběh času a vypočítá stav každé animace. To dělá mnoho takových hodnocení projde v druhém. Tyto průchody hodnocení jsou označovány jako "klíšťata".  
  
 Zatímco klíšťata se vyskytují často, je možné, že se mezi klíšťaty stane spousta věcí. Například časová osa může být zastavena, spuštěna a zastavena znovu, v takovém případě se její aktuální stav třikrát změní. Teoreticky by událost mohla být vyvolána vícekrát v jednom tiku; však modul časování konsoliduje události, tak, aby každá událost může být vyvolána maximálně jednou za značku.  
  
## <a name="registering-for-events"></a>Registrace na události  
 Existují dva způsoby, jak se zaregistrovat pro události časování: můžete se zaregistrovat na časové ose nebo s hodinami vytvořenými z časové osy. Registrace pro událost přímo s hodinami je poměrně jednoduché, i když to lze provést pouze z kódu. Můžete se zaregistrovat pro události s časovou osou z kódu nebo kódu. V další části je popsáno, jak se zaregistrovat pro události hodiny s časovou osou.  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrace pro události hodin s časovou osou  
 Přestože se <xref:System.Windows.Media.Animation.Timeline.Completed>zdá, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>že <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> časová osa , <xref:System.Windows.Media.Animation.Clock> <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated> <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, a události časové osy jsou přidruženy k časové ose, registrace těchto událostí ve skutečnosti přidruží obslužnou rutinu události k vytvořené pro časovou osu.  
  
 Když se například zaregistrujete pro <xref:System.Windows.Media.Animation.Timeline.Completed> událost na časové ose, ve <xref:System.Windows.Media.Animation.Clock.Completed> skutečnosti říkáte systému, aby se zaregistroval pro událost každé hodiny, která je vytvořena pro časovou osu. V kódu se musíte zaregistrovat <xref:System.Windows.Media.Animation.Clock> pro tuto událost před vytvořením pro tuto časovou osu; v opačném případě nebudete dostávat oznámení. K tomu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dochází automaticky v ; analyzátor se automaticky zaregistruje pro <xref:System.Windows.Media.Animation.Clock> událost před vytvořením.  
  
## <a name="see-also"></a>Viz také

- [Animace a časování přehledu systému](animation-and-timing-system-overview.md)
- [Přehled animace](animation-overview.md)
- [Přehled chování časování](timing-behaviors-overview.md)
