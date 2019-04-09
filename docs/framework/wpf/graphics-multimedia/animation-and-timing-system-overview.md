---
title: Animace a časování přehledu systému
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: f64431e7804ba6e068a3d05f512c6ead089d7712
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079315"
---
# <a name="animation-and-timing-system-overview"></a>Animace a časování přehledu systému
Toto téma popisuje, jak používá systém časování animace, <xref:System.Windows.Media.Animation.Timeline>, a <xref:System.Windows.Media.Animation.Clock> třídy pro animaci vlastnosti.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, byste měli používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace pro animaci vlastnosti, jak je popsáno v [přehled animace](animation-overview.md). Pomáhá také se seznámit s vlastností závislosti; Další informace najdete v tématu [přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Časové osy a hodiny  
 [Přehled animace](animation-overview.md) jak je popsáno <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment, data a animaci je typ <xref:System.Windows.Media.Animation.Timeline> , která vytváří výstupní hodnoty. Sama o sobě <xref:System.Windows.Media.Animation.Timeline>, nebude dělat nic jiného než jenom popisují segment čas. Je na časové ose <xref:System.Windows.Media.Animation.Clock> objekt, který odvádí skutečnou práci. Obdobně animace není animace ve skutečnosti vlastností: třídu animace popisuje způsob výpočtu výstupní hodnoty, ale je <xref:System.Windows.Media.Animation.Clock> , který byl vytvořen pro animaci, která řídí výstup animace a platí pro vlastnosti.  
  
 A <xref:System.Windows.Media.Animation.Clock> je speciální typ objektu, který udržuje s časováním běhový stav pro <xref:System.Windows.Media.Animation.Timeline>. Poskytuje tři bits informace, které jsou nezbytné pro animace a časování systému: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, a <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> určuje jeho aktuální čas, průběhu a stavu pomocí chování časování popsal jeho <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, a tak dále.  
  
 Ve většině případů <xref:System.Windows.Media.Animation.Clock> se automaticky vytvoří pro vaši časovou osu. Když animace s použitím <xref:System.Windows.Media.Animation.Storyboard> nebo <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody hodiny automaticky vytvořené pro časové osy a animace a použít pro jejich cílové vlastnosti. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně pomocí <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metodu vaše <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Metoda vytvoří hodiny odpovídající typu <xref:System.Windows.Media.Animation.Timeline> na kterém je volána. Pokud <xref:System.Windows.Media.Animation.Timeline> obsahuje podřízených časových os, vytvoří <xref:System.Windows.Media.Animation.Clock> objekty pro ně i. Výsledná <xref:System.Windows.Media.Animation.Clock> objekty jsou uspořádány do stromové struktury, které odpovídají struktury <xref:System.Windows.Media.Animation.Timeline> objekty stromové struktury, ze které je vytvořen.  
  
 Existují různé druhy hodiny pro různé typy časové osy. Následující tabulka ukazuje <xref:System.Windows.Media.Animation.Clock> typy, které odpovídají na některé z různých <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ osy|Typ hodin|Účel hodiny|  
|-------------------|----------------|-------------------|  
|Animace (dědí z <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Vygeneruje výstupní hodnoty pro vlastnost závislosti.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Zpracuje mediální soubor.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Skupiny a jeho podřízených ovládacích prvků <xref:System.Windows.Media.Animation.Clock> objekty|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Skupiny a jeho podřízených ovládacích prvků <xref:System.Windows.Media.Animation.Clock> objekty|  
  
 Můžete použít libovolný <xref:System.Windows.Media.Animation.AnimationClock> objektů, vytvoříte pro vlastnosti závislosti kompatibilní s použitím <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> metody.  
  
 Ve scénářích náročné na výkon, jako je například velký počet podobné objekty animace Správa vlastních <xref:System.Windows.Media.Animation.Clock> použití může poskytnout přinese zlepšení výkonu.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Hodiny a správce čas  
 Když animace objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je čas správce, který spravuje <xref:System.Windows.Media.MediaPlayer.Clock%2A> objekty vytvořené pro vaše časové osy. Správce čas je kořen stromu <xref:System.Windows.Media.MediaPlayer.Clock%2A> objektů a řídí tok čas ve stromové struktuře.  Správce čas se automaticky vytvoří pro každou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace a je viditelný pro vývojáře aplikací. Správce čas "značky" tolikrát, kolikrát za sekundu; skutečný počet taktů, ke kterým dochází každou sekundu se liší v závislosti na dostupných systémových prostředků. Během jedna z těchto značek, vypočítá čas správce stavu všech <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> objekty ve stromové struktuře časování.  
  
 Následující ilustrace znázorňuje vztah mezi správce čas a <xref:System.Windows.Media.Animation.AnimationClock>a vlastnost animovaný závislostí.  
  
 ![Součásti systému časování](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animace vlastností  
  
 Správce čas značek, aktualizuje čas každý <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> v aplikaci. Pokud <xref:System.Windows.Media.Animation.Clock> je <xref:System.Windows.Media.Animation.AnimationClock>, použije <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metodu <xref:System.Windows.Media.Animation.AnimationTimeline> ze které byla vytvořena pro výpočet aktuálním výstupní hodnota. <xref:System.Windows.Media.Animation.AnimationClock> Poskytuje <xref:System.Windows.Media.Animation.AnimationTimeline> s aktuálním místním časem, vstupní hodnota, která je obvykle základní hodnoty vlastnosti a určení výchozí hodnotu. Při načtení hodnoty animovaného pomocí vlastnosti <xref:System.Windows.DependencyObject.GetValue%2A> metody nebo její přistupující objekt CLR, získáte výstup jeho <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Hodiny skupiny  
 Předchozí část popisuje, jak jsou různé druhy <xref:System.Windows.Media.Animation.Clock> objekty pro různé druhy časové osy. Následující ilustrace znázorňuje vztah mezi správce čas <xref:System.Windows.Media.Animation.ClockGroup>, <xref:System.Windows.Media.Animation.AnimationClock>a vlastnost animovaný závislostí. A <xref:System.Windows.Media.Animation.ClockGroup> pro časové osy, které skupiny jiné časové osy, jako je vytvořen <xref:System.Windows.Media.Animation.Storyboard> třídu, která seskupuje animace a jiné časové osy.  
  
 ![Součásti systému časování](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>Složení  
 Je možné přidružit více hodiny s jedinou vlastností, v takovém případě každý používá hodiny hodnota výstupního předchozím hodiny jako jeho základní hodnoty. Následující obrázek znázorňuje tři <xref:System.Windows.Media.Animation.AnimationClock> objekty použité na stejnou vlastnost. Clock1 používá základní hodnotou animované vlastnosti jako vstup a používá ji generovat výstup. Clock2 převezme výstup z Clock1 jako vstup a používá ke generování výstupu. Clock3 převezme výstup z Clock2 jako vstup a používá ke generování výstupu. Několik hodin. ovlivňují stejnou vlastnost současně, jsou označeny v řetězu složení.  
  
 ![Součásti systému časování](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Řetězec sestavení  
  
 Všimněte si, že i když je vytvořen vztah mezi vstup a výstup <xref:System.Windows.Media.Animation.AnimationClock> objekty v řetězci složení jejich chování časování neovlivní; <xref:System.Windows.Media.Animation.Clock> objekty (včetně <xref:System.Windows.Media.Animation.AnimationClock> objekty) jsou hierarchické závislá na jejich nadřazené <xref:System.Windows.Media.Animation.Clock> objekty.  
  
 Použít stejnou vlastnost několik hodin, použijte <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> při použití <xref:System.Windows.Media.Animation.Storyboard>, animace, nebo <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Značky a konsolidaci událostí  
 Kromě výpočet výstupní hodnoty času manager provede další práci pokaždé, když ho značek: Určuje stav každé hodiny a vyvolává události podle potřeby.  
  
 Zatímco značky docházet často, je možné pro mnoho věcí, které se provedou mezi značkami. Například <xref:System.Windows.Media.Animation.Clock> může zastavit, spustit a zastavit znovu, v takovém případě jeho <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> hodnota se změnily třikrát. Teoreticky vzato <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> události může být vyvolána více než jednou v jedné značky, ale modul časování konsoliduje události, tak, aby <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> událost může být vyvolána nejvýše jednou za značek. To platí pro všechny události časování: každého typu maximálně jednu událost je aktivována pro danou <xref:System.Windows.Media.Animation.Clock> objektu.  
  
 Při <xref:System.Windows.Media.Animation.Clock> přepíná stavy a vrátí zpět do původního stavu mezi značkami (jako je například změna z <xref:System.Windows.Media.Animation.ClockState.Active> k <xref:System.Windows.Media.Animation.ClockState.Stopped> a zpět <xref:System.Windows.Media.Animation.ClockState.Active>), i přesto dochází ke související události.  
  
 Další informace o události časování, najdete v článku [Přehled událostí časování](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Aktuální hodnoty a základní hodnoty vlastností  
 Animovatelné vlastnosti může mít dvě hodnoty: základní hodnoty a aktuální hodnotu. Při nastavení vlastnosti pomocí její přistupující objekt CLR nebo <xref:System.Windows.DependencyObject.SetValue%2A> metody, nastavte jeho základní hodnoty. Pokud není vlastnost animovat, jsou základní a aktuální hodnoty stejné.  
  
 Při animovat vlastnost, <xref:System.Windows.Media.Animation.AnimationClock> nastaví vlastnosti *aktuální* hodnotu. Načítání hodnoty vlastnosti prostřednictvím její přistupující objekt CLR nebo <xref:System.Windows.DependencyObject.GetValue%2A> metoda vrátí výstup <xref:System.Windows.Media.Animation.AnimationClock> při <xref:System.Windows.Media.Animation.AnimationClock> je <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling>. Základní hodnota vlastnosti můžete načíst pomocí <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> metody.  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled událostí časování](timing-events-overview.md)
- [Přehled chování časování](timing-behaviors-overview.md)
