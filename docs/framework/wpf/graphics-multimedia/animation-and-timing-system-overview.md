---
title: Animace a časování přehledu systému
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: bfb9a337a604fe8d86d208344d4371748e28f285
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557963"
---
# <a name="animation-and-timing-system-overview"></a>Animace a časování přehledu systému
Toto téma popisuje, jak používá systém časování animace, <xref:System.Windows.Media.Animation.Timeline>, a <xref:System.Windows.Media.Animation.Clock> třídy pro animaci vlastnosti.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit v tomto tématu byste měli použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací pro animaci vlastnosti, jak je popsáno v [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pomáhá také se seznamte s vlastností závislostí; Další informace najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Časové osy a hodiny  
 [Animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) popisuje jak <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a animace je typ <xref:System.Windows.Media.Animation.Timeline> výstupní hodnoty, která vyvolává. Samostatně <xref:System.Windows.Media.Animation.Timeline>, nic se neděje jiné než právě popisují segment času. Je časové ose <xref:System.Windows.Media.Animation.Clock> objekt, který provádí skutečná práce. Podobně animace není animace ve skutečnosti vlastnosti: třídu animace popisuje, jak se má vypočítat výstupní hodnoty, ale je <xref:System.Windows.Media.Animation.Clock> který byl vytvořen pro animaci, jednotky výstup animace a platí pro vlastnosti.  
  
 A <xref:System.Windows.Media.Animation.Clock> je zvláštní typ objektu, který udržuje s časováním stavu spuštění pro <xref:System.Windows.Media.Animation.Timeline>. Poskytuje tři bity informace, které jsou nezbytné pro animace a časování systému: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, a <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> určuje jeho aktuální čas, průběh a stav pomocí chování časování popsaného jeho <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>a tak dále.  
  
 Ve většině případů <xref:System.Windows.Media.Animation.Clock> se vytvoří automaticky časové osy. Když animace pomocí <xref:System.Windows.Media.Animation.Storyboard> nebo <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody hodiny se automaticky vytvoří pro časové osy a animace a použijí k jejich cílové vlastnosti. Můžete také vytvořit <xref:System.Windows.Media.Animation.Clock> explicitně pomocí <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metodu vaší <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Metoda vytvoří hodiny příslušného typu pro <xref:System.Windows.Media.Animation.Timeline> na kterém je volána. Pokud <xref:System.Windows.Media.Animation.Timeline> obsahuje podřízené časových os, vytvoří <xref:System.Windows.Media.Animation.Clock> také objekty pro ně. Výsledná <xref:System.Windows.Media.Animation.Clock> objekty jsou uspořádány do stromové struktury, které odpovídají strukturu <xref:System.Windows.Media.Animation.Timeline> objekty stromu, ze které se vytvářejí.  
  
 Existují různé druhy hodiny pro různé typy časové osy. Následující tabulce je zobrazena <xref:System.Windows.Media.Animation.Clock> typy, které odpovídají na některé rozdíly <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ časové osy|Typ hodin|Účel hodiny|  
|-------------------|----------------|-------------------|  
|Animace (dědí z <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Generuje výstupní hodnoty pro vlastnost závislosti.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Zpracuje soubor média.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Skupiny a její podřízené ovládací prvky <xref:System.Windows.Media.Animation.Clock> objekty|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Skupiny a její podřízené ovládací prvky <xref:System.Windows.Media.Animation.Clock> objekty|  
  
 Můžete použít libovolný <xref:System.Windows.Media.Animation.AnimationClock> objekty pomocí vytvoříte vlastností kompatibilní závislostí <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> metoda.  
  
 V případech náročných na výkon, například animace velkého počtu objektů podobné, Správa vlastního <xref:System.Windows.Media.Animation.Clock> použití můžou poskytovat výhody výkonu.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Hodiny a časové správce  
 Když animace objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je čas správce, který spravuje <xref:System.Windows.Media.MediaPlayer.Clock%2A> objekty vytvořené pro vaše časové osy. Správce čas je kořenem strom <xref:System.Windows.Media.MediaPlayer.Clock%2A> objekty a řídí tok čas ve stromové struktuře.  Čas manager se automaticky vytvoří pro každou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace a neviditelná pro vývojáře aplikací. Správce čas "rysky" tolikrát, kolikrát za sekundu; skutečný počet rysky, ke kterým došlo, každý druhý se liší v závislosti na dostupné prostředky systému. Při každé jeden z těchto rysky správce čas vypočítá stav všech <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> objekty ve stromové struktuře časování.  
  
 Následující obrázek znázorňuje vztah mezi správce čas a <xref:System.Windows.Media.Animation.AnimationClock>a ve vlastnosti animovaný závislostí.  
  
 ![Časování součásti systému](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animace vlastnost  
  
 Když správce čas značek, aktualizuje době každých <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> v aplikaci. Pokud <xref:System.Windows.Media.Animation.Clock> je <xref:System.Windows.Media.Animation.AnimationClock>, použije <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metodu <xref:System.Windows.Media.Animation.AnimationTimeline> ze které byla vytvořena pro výpočet jeho aktuální hodnota výstupu. <xref:System.Windows.Media.Animation.AnimationClock> Poskytuje <xref:System.Windows.Media.Animation.AnimationTimeline> s aktuálním místním časem, vstupní hodnotu, která je obvykle hodnotu vlastnosti a cílový výchozí hodnotu. Když načíst hodnotu animovaný pomocí vlastnosti <xref:System.Windows.DependencyObject.GetValue%2A> metoda nebo její přistupující objekt CLR, získat výstup jeho <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Hodiny skupiny  
 V předchozí části popisuje, jak jsou různé typy <xref:System.Windows.Media.Animation.Clock> objekty pro různé typy časové osy. Následující obrázek znázorňuje vztah mezi správce čas <xref:System.Windows.Media.Animation.ClockGroup>, <xref:System.Windows.Media.Animation.AnimationClock>a ve vlastnosti animovaný závislostí. A <xref:System.Windows.Media.Animation.ClockGroup> se vytvoří pro časové osy skupiny ostatní časové osy, jako <xref:System.Windows.Media.Animation.Storyboard> třídy, která skupiny animace a ostatní časové osy.  
  
 ![Časování součásti systému](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>Složení  
 Jeho možné přidružit víc označí s jedinou vlastností, v takovém případě každé hodiny používá hodnotu výstup předchozím taktovací jako svou základní hodnotu. Následující obrázek znázorňuje tři <xref:System.Windows.Media.Animation.AnimationClock> objekty použít pro stejnou vlastnost. Clock1 používá hodnotu animovaný vlastnosti jako vstup a používá ke generování výstupu. Clock2 trvá výstup z Clock1 jako vstup a používá ke generování výstupu. Clock3 trvá výstup z Clock2 jako vstup a používá ke generování výstupu. Více hodiny ovlivnit stejnou vlastnost současně, jsou označeny jako v řetězu složení.  
  
 ![Časování součásti systému](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Řetěz složení  
  
 Všimněte si, že i když je vytvořen vztah mezi vstup a výstup <xref:System.Windows.Media.Animation.AnimationClock> objekty v řetězu složení jejich chování časování neovlivní; <xref:System.Windows.Media.Animation.Clock> objekty (včetně <xref:System.Windows.Media.Animation.AnimationClock> objekty) jsou hierarchické závislé na jejich nadřazené <xref:System.Windows.Media.Animation.Clock> objekty.  
  
 Chcete-li použít více hodiny pro stejnou vlastnost, použijte <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> při použití <xref:System.Windows.Media.Animation.Storyboard>, animace, nebo <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Značky a konsolidaci událostí  
 Kromě výpočet hodnot výstup, čas manager funguje jiných pokaždé, když ho značek: Určuje stav každého hodin a vygeneruje události podle potřeby.  
  
 Pokud ke rysky často dochází, je možné pro mnoho kroků k mezi značky. Například <xref:System.Windows.Media.Animation.Clock> může zastavení, spuštění a zastavení znovu, v takovém případě jeho <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> hodnota bude změněna třikrát. Teoreticky <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> událost může vyvolá více než jednou. v jedné značky; však modul časování dojde ke konsolidaci událostí, tak, aby <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> události mohou být vyvolány nejvíce jednou za značek. To platí pro všechny události časování: každého typu maximálně jednu událost se vyvolá pro danou <xref:System.Windows.Media.Animation.Clock> objektu.  
  
 Při <xref:System.Windows.Media.Animation.Clock> přepíná stavy a vrátí zpět do původního stavu mezi rysky (jako je například změna z <xref:System.Windows.Media.Animation.ClockState.Active> k <xref:System.Windows.Media.Animation.ClockState.Stopped> a zpět na <xref:System.Windows.Media.Animation.ClockState.Active>), stále dochází k související události.  
  
 Další informace o časování událostí najdete v tématu [přehled časování událostí](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Aktuální hodnoty a základní hodnoty vlastností  
 Animatable vlastnost může mít dvě hodnoty: hodnotu základní a aktuální hodnotu. Když nastavíte vlastnost pomocí jeho přistupujícího objektu CLR nebo <xref:System.Windows.DependencyObject.SetValue%2A> metoda, nastavte jeho základní hodnotu. Pokud není vlastnost animovaný, jeho základní a aktuální hodnoty jsou stejné.  
  
 Když animace vlastnosti <xref:System.Windows.Media.Animation.AnimationClock> nastaví vlastnosti *aktuální* hodnota. Načítání hodnotu vlastnosti prostřednictvím její přistupující objekt CLR nebo <xref:System.Windows.DependencyObject.GetValue%2A> metoda vrátí výstup <xref:System.Windows.Media.Animation.AnimationClock> při <xref:System.Windows.Media.Animation.AnimationClock> je <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling>. Základní hodnotu vlastnosti můžete načíst pomocí <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled událostí časování](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Přehled chování časování](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
