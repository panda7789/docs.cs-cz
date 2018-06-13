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
ms.openlocfilehash: a48d1621e5568d556a1177578cc662813d70a283
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565484"
---
# <a name="timing-events-overview"></a>Přehled událostí časování
Toto téma popisuje, jak používat k dispozici na pět časování události <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> objekty.  
  
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, musíte vědět, jak vytvořit a používat animace. Začínáme s animace, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Animace vlastnosti v několika způsoby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Použití objektů storyboard** (značek a kódu): můžete použít <xref:System.Windows.Media.Animation.Storyboard> objekty, které chcete uspořádat a distribuovat animací na jeden nebo více objektů. Příklad, naleznete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Pomocí místní animací** (pouze kód): můžete použít <xref:System.Windows.Media.Animation.AnimationTimeline> objekty přímo pro vlastnosti se animace. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Pomocí hodiny** (pouze kód): můžete explicitně správě vytváření hodiny a distribuovat hodiny animace sami.  Příklad, naleznete v části [animace vlastnost pomocí AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Vzhledem k tomu, že je lze využít v značek a kódu, příklady v tomto přehledu použít <xref:System.Windows.Media.Animation.Storyboard> objekty. Konceptů popsaných však můžete použít jiné metody animace vlastnosti.  
  
### <a name="what-is-a-clock"></a>Co je čase?  
 Časová osa, samostatně, nic se neděje ve skutečnosti jiné než popisují segment času. Je časové ose <xref:System.Windows.Media.Animation.Clock> objekt, který funguje skutečné: udržuje s časováním stavu spuštění pro časovou osu. Ve většině případů, například při použití scénářů hodiny, které vytvoří automaticky časové osy. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně pomocí <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metoda. Další informace o <xref:System.Windows.Media.Animation.Clock> objekty, najdete [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Proč používat události?  
 S výjimkou jeden (Hledat zarovnaný na poslední značek), všechny operace interaktivní časování jsou asynchronní. Neexistuje žádný způsob nevíte, přesně když se spustí. Pokud máte jiný kód, který závisí na vaší časování operaci, která může být problém. Předpokládejme, že jste chtěli zastavit osy, která animovaný obdélníku. Po časovou osu zastaví, změníte barvu rámečku.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 V předchozím příkladu druhý řádek kódu může spustit před storyboard zastaví. Je to způsobeno zastavením je asynchronní operace. Že časová osa nebo hodiny zastavit vytvoří "žádost o zastavení" typů které nejsou předmětem zpracování, dokud modul časování další značky.  
  
 Chcete-li po dokončení časový horizont spuštěním příkazů, použijte časování události. V následujícím příkladu obslužné rutiny události umožňuje změnit barvu obdélníku po scénáři zastaví přehrávání.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Více kompletní příklad najdete v tématu [změny stavu přijímat oznámení při hodiny na](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Veřejné události  
 <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> třídy obou poskytují pět časování události. Následující tabulka uvádí tyto události a podmínky, které je.  
  
|Událost|Spouštěcí interaktivní operace|Další aktivační události|  
|-----------|--------------------------------------|--------------------|  
|**byla dokončena**|Přeskočit k vyplnění|Hodiny dokončí.|  
|**CurrentGlobalSpeedInvalidated**|Pozastavit, pokračovat, Hledat, nastavit rychlost poměr, přejděte k vyplnění, zastavte|Hodiny obrátí, zrychluje, spuštění nebo zastavení.|  
|**CurrentStateInvalidated**|Začít, přejděte k vyplnění, zastavte|Hodiny spustí, zastaví, nebo doplní.|  
|**CurrentTimeInvalidated**|Začít, Hledat, přejděte k vyplnění, zastavte|Postupuje hodiny.|  
|**RemoveRequested**|Odebrat||  
  
## <a name="ticking-and-event-consolidation"></a>A obaly a konsolidaci událostí  
 Když animace objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], časování stroj, který spravuje vaše animace. Modul časování sleduje průběh čas a vypočítá stav každého animace. Umožňuje mnoho takové předává vyhodnocení za sekundu. Tyto zkušební předává se označují jako "rysky."  
  
 Pokud ke rysky často dochází, je možné pro mnoho kroků k mezi značky. Například časové osy může být zastavena, spustit a zastavit znovu, v takovém případě jejím aktuálním stavu se změnily třikrát. Teoreticky události je možné zvýšit více než jednou. v jedné značky; modul časování však konsoliduje události, tak, aby všechny události mohou být vyvolány nejvíce jednou za značek.  
  
## <a name="registering-for-events"></a>Registrace pro události  
 Existují dva způsoby registrace pro časování události: můžete zaregistrovat s časovou osu nebo hodiny vytvořené z časovou osu. Registrace pro událost přímo s hodinami je poměrně jasné, i když lze provést pouze z kódu. Můžete zaregistrovat pro události se časové osy z kód. Další část popisuje postup registrace pro události hodiny s časovou osu.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrace pro události hodiny se časové osy  
 I když časové osy <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, a <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> události se zobrazí přidruženi k registraci pro tyto události ve skutečnosti přidruží obslužné rutiny události s časovou osu <xref:System.Windows.Media.Animation.Clock> vytvoří pro časovou osu.  
  
 Když si zaregistrujete <xref:System.Windows.Media.Animation.Timeline.Completed> událostí na časové ose, například můžete jste ve skutečnosti informuje systém k registraci pro <xref:System.Windows.Media.Animation.Clock.Completed> událostí každé hodiny, který se vytvoří pro časovou osu. V kódu, je třeba zaregistrovat pro tuto událost před <xref:System.Windows.Media.Animation.Clock> se vytvoří pro tuto časovou osu; jinak nebude přijímat oznámení. K tomu dojde automaticky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; analyzátor automaticky zaregistruje událost před <xref:System.Windows.Media.Animation.Clock> je vytvořena.  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace a systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled chování časování](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
