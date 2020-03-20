---
title: Animace a časování přehledu systému
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187709"
---
# <a name="animation-and-timing-system-overview"></a>Animace a časování přehledu systému
Toto téma popisuje, jak systém <xref:System.Windows.Media.Animation.Timeline>časování <xref:System.Windows.Media.Animation.Clock> používá animace , a třídy animovat vlastnosti.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste být schopni animovat vlastnosti pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací, jak je popsáno v [přehledu animací](animation-overview.md). Pomáhá také seznámit se s vlastnostmi závislostí; Další informace naleznete v tématu [Přehled vlastností závislostí](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>Časové osy a hodiny  
 [Přehled animace](animation-overview.md) popsal, <xref:System.Windows.Media.Animation.Timeline> jak představuje segment času a animace je <xref:System.Windows.Media.Animation.Timeline> typ, který vytváří výstupní hodnoty. Samo o <xref:System.Windows.Media.Animation.Timeline>sobě, , nedělá nic jiného, než jen popsat segment času. Je to objekt časové <xref:System.Windows.Media.Animation.Clock> osy, který dělá skutečnou práci. Podobně animace není ve skutečnosti animovat vlastnosti: třída animace popisuje, jak by <xref:System.Windows.Media.Animation.Clock> měly být vypočteny výstupní hodnoty, ale je to, který byl vytvořen pro animaci, která řídí výstup animace a použije ji na vlastnosti.  
  
 A <xref:System.Windows.Media.Animation.Clock> je zvláštní typ objektu, který udržuje časování <xref:System.Windows.Media.Animation.Timeline>související s časem stavu pro . Poskytuje tři bity informací, které jsou nezbytné pro <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A> <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>animaci a časování systému: , , a <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> určuje jeho aktuální čas, průběh a stav pomocí chování <xref:System.Windows.Media.Animation.Timeline>časování popsané jeho : <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, a tak dále.  
  
 Ve většině případů <xref:System.Windows.Media.Animation.Clock> se pro vaši časovou osu vytvoří automaticky. Při animaci pomocí <xref:System.Windows.Media.Animation.Storyboard> metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> nebo metody se hodiny automaticky vytvoří pro vaše časové osy a animace a použijí se na jejich cílové vlastnosti. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> pomocí metody <xref:System.Windows.Media.Animation.Timeline>. Metoda <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> vytvoří hodiny příslušného typu <xref:System.Windows.Media.Animation.Timeline> pro, na kterém je volána. Pokud <xref:System.Windows.Media.Animation.Timeline> obsahuje podřízené časové <xref:System.Windows.Media.Animation.Clock> osy, vytvoří objekty pro ně také. Výsledné <xref:System.Windows.Media.Animation.Clock> objekty jsou uspořádány ve stromech, které odpovídají struktuře stromu <xref:System.Windows.Media.Animation.Timeline> objektů, ze kterého jsou vytvořeny.  
  
 Existují různé typy hodin pro různé typy časových os. V následující tabulce <xref:System.Windows.Media.Animation.Clock> jsou uvedeny typy, <xref:System.Windows.Media.Animation.Timeline> které odpovídají některé z různých typů.  
  
|Typ časové osy|Typ hodin|Účel hodin|  
|-------------------|----------------|-------------------|  
|Animace (dědí <xref:System.Windows.Media.Animation.AnimationTimeline>z)|<xref:System.Windows.Media.Animation.AnimationClock>|Generuje výstupní hodnoty pro vlastnost závislosti.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Zpracuje mediální soubor.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Seskupí <xref:System.Windows.Media.Animation.Clock> a řídí podřízené objekty.|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Seskupí <xref:System.Windows.Media.Animation.Clock> a řídí podřízené objekty.|  
  
 Pomocí metody <xref:System.Windows.Media.Animation.AnimationClock> můžete použít všechny objekty, které <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> vytvoříte, na kompatibilní vlastnosti závislostí.  
  
 Ve scénářích náročných na výkon, jako je například animace <xref:System.Windows.Media.Animation.Clock> velkého počtu podobných objektů, správa vlastní použití může poskytnout výhody výkonu.  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>Hodiny a správce času  
 Když animujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objekty v aplikaci , <xref:System.Windows.Media.MediaPlayer.Clock%2A> je to správce času, který spravuje objekty vytvořené pro vaše časové osy. Správce času je kořen stromu <xref:System.Windows.Media.MediaPlayer.Clock%2A> objektů a řídí tok času v tomto stromu.  Správce času je automaticky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořen pro každou aplikaci a je pro vývojáře aplikace neviditelný. Správce času "zaškrtne" mnohokrát za sekundu; skutečný počet značek, ke kterým dochází každou sekundu, se liší v závislosti na dostupných systémových prostředcích. Během každého z těchto značek správce času vypočítá stav <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> všech objektů ve stromu časování.  
  
 Následující obrázek znázorňuje vztah mezi <xref:System.Windows.Media.Animation.AnimationClock>správcem času a aplikacea a vlastností animované závislosti.  
  
 ![Součásti časovacího systému](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animace vlastnosti  
  
 Když správce času zaškrtne, aktualizuje <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> čas každého v aplikaci. Pokud <xref:System.Windows.Media.Animation.Clock> je <xref:System.Windows.Media.Animation.AnimationClock>, používá <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metodu, <xref:System.Windows.Media.Animation.AnimationTimeline> ze které byl vytvořen pro výpočet jeho aktuální výstupní hodnoty. Dodává <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.AnimationTimeline> s aktuální místní čas, vstupní hodnota, která je obvykle základní hodnota vlastnosti a výchozí cílovou hodnotu. Při načtení hodnoty animované vlastnosti <xref:System.Windows.DependencyObject.GetValue%2A> pomocí metody nebo jeho clr přistupujícího objektu, získáte výstup jeho <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Skupiny hodin  
 Předchozí část popisuje, jak existují různé <xref:System.Windows.Media.Animation.Clock> typy objektů pro různé typy časových os. Následující obrázek znázorňuje vztah mezi <xref:System.Windows.Media.Animation.ClockGroup>správcem času, vlastností , a <xref:System.Windows.Media.Animation.AnimationClock>animovaná závislost. A <xref:System.Windows.Media.Animation.ClockGroup> se vytvoří pro časové osy, <xref:System.Windows.Media.Animation.Storyboard> které seskupují jiné časové osy, jako je například třída, která seskupuje animace a další časové osy.  
  
 ![Součásti časovacího systému](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Hodinová skupina  
  
#### <a name="composition"></a>Složení  
 Je možné přidružit více hodin s jednou vlastností, v takovém případě každý hodiny používá výstupní hodnotu předchozí hodiny jako jeho základní hodnotu. Následující obrázek <xref:System.Windows.Media.Animation.AnimationClock> znázorňuje tři objekty aplikované na stejnou vlastnost. Clock1 používá základní hodnotu animované vlastnosti jako jeho vstup a používá jej ke generování výstupu. Clock2 bere výstup z Clock1 jako jeho vstup a používá jej ke generování výstupu. Clock3 trvá výstup z Clock2 jako jeho vstup a používá jej ke generování výstupu. Pokud více hodin ovlivnit stejnou vlastnost současně, jsou řekl, aby byl v řetězci složení.  
  
 ![Součásti časovacího systému](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Kompoziční řetězec  
  
 Všimněte si, že i když je <xref:System.Windows.Media.Animation.AnimationClock> vytvořen vztah mezi vstup a výstup objektů v řetězci složení, jejich chování časování nejsou ovlivněny; <xref:System.Windows.Media.Animation.Clock> objekty <xref:System.Windows.Media.Animation.AnimationClock> (včetně objektů) mají hierarchickou <xref:System.Windows.Media.Animation.Clock> závislost na svých nadřazených objektech.  
  
 Chcete-li použít více hodin na <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> stejnou vlastnost, použijte při použití <xref:System.Windows.Media.Animation.Storyboard>, animace nebo <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Značky a konsolidace událostí  
 Kromě výpočtu výstupních hodnot provádí správce času další práci pokaždé, když zaškrtne: určuje stav jednotlivých hodin a podle potřeby vyvolá události.  
  
 Zatímco klíšťata se vyskytují často, je možné, že se mezi klíšťaty stane spousta věcí. Může být <xref:System.Windows.Media.Animation.Clock> například zastavena, spuštěna a zastavena <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> znovu, v takovém případě se jeho hodnota třikrát změní. Teoreticky <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> by událost mohla být vyvolána vícekrát v jednom tiku; však modul časování konsoliduje události, tak, aby <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> událost může být vyvolána maximálně jednou za značku. To platí pro všechny události časování: maximálně jedna událost <xref:System.Windows.Media.Animation.Clock> každého typu je aktivována pro daný objekt.  
  
 Když <xref:System.Windows.Media.Animation.Clock> přepne stavy a vrátí se zpět do <xref:System.Windows.Media.Animation.ClockState.Active> původního stavu mezi značkami (například přechod z <xref:System.Windows.Media.Animation.ClockState.Stopped> a zpět na <xref:System.Windows.Media.Animation.ClockState.Active>), stále dochází k přidružené události.  
  
 Další informace o událostech časování naleznete v tématu [Přehled událostí časování](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>Aktuální hodnoty a základní hodnoty vlastností  
 Animovatelná vlastnost může mít dvě hodnoty: základní hodnotu a aktuální hodnotu. Když nastavíte vlastnost pomocí jeho <xref:System.Windows.DependencyObject.SetValue%2A> přístupového objektu CLR nebo metody, nastavíte její základní hodnotu. Pokud vlastnost není animována, její základní a aktuální hodnoty jsou stejné.  
  
 Když animujete vlastnost, nastaví <xref:System.Windows.Media.Animation.AnimationClock> *aktuální* hodnotu vlastnosti. Načítání hodnoty vlastnosti prostřednictvím jeho přístupový <xref:System.Windows.DependencyObject.GetValue%2A> objekt CLR nebo <xref:System.Windows.Media.Animation.AnimationClock> metoda <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.ClockState.Active> vrátí <xref:System.Windows.Media.Animation.ClockState.Filling>výstup when is nebo . Základní hodnotu vlastnosti můžete načíst <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> pomocí metody.  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled událostí časování](timing-events-overview.md)
- [Přehled chování časování](timing-behaviors-overview.md)
