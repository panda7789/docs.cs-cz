---
title: Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 22bb78040b023a59fd46f0a2be45659d6d7220b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914514"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IScrollProvider>implementaci, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.ScrollPattern> ovládacího prvku slouží k podpoře ovládacího prvku, který funguje jako posuvný kontejner pro kolekci podřízených objektů. Ovládací prvek není vyžadován k použití posuvníků k podpoře funkcí posouvání, i když to obvykle funguje.  
  
 ![Posuňte ovládací prvek bez posuvníků.](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Příklad ovládacího prvku pro posouvání, který nepoužívá posuvníky  
  
 Příklady ovládacích prvků, které implementují tento ovládací prvek, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci řídicího vzoru posuvníku si všimněte následujících pokynů a konvencí:  
  
- Podřízené objekty tohoto ovládacího prvku musí implementovat <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
- Posuvníky ovládacího prvku kontejneru nepodporují <xref:System.Windows.Automation.ScrollPattern> vzor ovládacího prvku. Musí místo toho podporovat <xref:System.Windows.Automation.RangeValuePattern> vzor ovládacího prvku.  
  
- Když se v procentech měří posouvání, musí být všechny hodnoty nebo částky související s posouváním do rozsahu normalizovány na rozsah 0 až 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> jsou nezávislé na <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>Pokud byměl =  být nastaven na 100% a měl by být nastaven na. `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Podobně, pokud  =  <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>by měl být nastaven na 100 procent a měl by být nastaven na. `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> To umožňuje klientovi automatizace uživatelského rozhraní použít tyto hodnoty vlastností v rámci <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metody a vyhnout se [konfliktu časování](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) , pokud se neaktivuje směr, který klient nemá zájem o posouvání.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>je specifický pro národní prostředí. Nastavení HorizontalScrollPercent = 100,0 musí nastavit umístění posouvání ovládacího prvku na ekvivalent jeho pravé pozice pro jazyky, jako je angličtina, které jsou čteny zleva doprava. Alternativně pro jazyky, jako je arabština, která je zprava doleva, nastavení HorizontalScrollPercent = 100,0 musí nastavit umístění posouvání na levou pozici.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Vyžadovaná členové pro IScrollProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider>jsou vyžadovány následující vlastnosti a metody.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>vyvolá tuto výjimku, pokud ovládací prvek <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> podporuje hodnoty výhradně pro vodorovné nebo svislé posouvání, <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> ale je předána hodnota.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, pokud je předána hodnota, která nemůže být převedena na typ Double.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, pokud je předána hodnota větší než 100 nebo menší než 0 (kromě hodnoty-1, která je <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>ekvivalentní hodnotě).|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> A<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> vyvolají tuto výjimku při pokusu o přechod v nepodporovaném směru.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
