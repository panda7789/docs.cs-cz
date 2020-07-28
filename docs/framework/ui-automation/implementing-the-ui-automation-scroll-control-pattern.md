---
title: Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzorového ovládacího prvku pro nastavení posuvníku v automatizace uživatelského rozhraní. Viz povinné členy pro rozhraní IScrollProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 830d65286f27302dcad109384b8df187ed4af1a5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166993"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider> , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 <xref:System.Windows.Automation.ScrollPattern>Vzor ovládacího prvku slouží k podpoře ovládacího prvku, který funguje jako posuvný kontejner pro kolekci podřízených objektů. Ovládací prvek není vyžadován k použití posuvníků k podpoře funkcí posouvání, i když to obvykle funguje.  
  
 ![Posuňte ovládací prvek bez posuvníků.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Příklad ovládacího prvku pro posouvání, který nepoužívá posuvníky  
  
 Příklady ovládacích prvků, které implementují tento ovládací prvek, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci řídicího vzoru posuvníku si všimněte následujících pokynů a konvencí:  
  
- Podřízené objekty tohoto ovládacího prvku musí implementovat <xref:System.Windows.Automation.Provider.IScrollItemProvider> .  
  
- Posuvníky ovládacího prvku kontejneru nepodporují <xref:System.Windows.Automation.ScrollPattern> vzor ovládacího prvku. Musí <xref:System.Windows.Automation.RangeValuePattern> místo toho podporovat vzor ovládacího prvku.  
  
- Když se v procentech měří posouvání, musí být všechny hodnoty nebo částky související s posouváním do rozsahu normalizovány na rozsah 0 až 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> jsou nezávislé na <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> .  
  
- Pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> by měl být nastaven na 100% a <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> měl by být nastaven na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> . Podobně, pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> by měl být nastaven na 100 procent a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> měl by být nastaven na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> . To umožňuje klientovi automatizace uživatelského rozhraní použít tyto hodnoty vlastností v rámci <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metody a vyhnout se [konfliktu časování](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) , pokud se neaktivuje směr, který klient nemá zájem o posouvání.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>je specifický pro národní prostředí. Nastavení HorizontalScrollPercent = 100,0 musí nastavit umístění posouvání ovládacího prvku na ekvivalent jeho pravé pozice pro jazyky, jako je angličtina, které jsou čteny zleva doprava. Alternativně pro jazyky, jako je arabština, která je zprava doleva, nastavení HorizontalScrollPercent = 100,0 musí nastavit umístění posouvání na levou pozici.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>Vyžadovaná členové pro IScrollProvider  
 Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.IScrollProvider> .  
  
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
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>vyvolá tuto výjimku, pokud ovládací prvek podporuje <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> hodnoty výhradně pro vodorovné nebo svislé posouvání, ale <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> je předána hodnota.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, pokud je předána hodnota, která nemůže být převedena na typ Double.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, pokud je předána hodnota větší než 100 nebo menší než 0 (kromě hodnoty-1, která je ekvivalentní hodnotě <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> ).|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>A <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> vyvolají tuto výjimku při pokusu o přechod v nepodporovaném směru.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
