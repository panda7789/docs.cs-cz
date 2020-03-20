---
title: Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 0420adaefb91f0c9f0d34d5bdf5863373a0b652b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180154"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IScrollProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.ScrollPattern> ovládacího prvku se používá pro podporu ovládacího prvku, který funguje jako posuvný kontejner pro kolekci podřízených objektů. Ovládací prvek není nutné používat posuvníky pro podporu funkce posouvání, i když to obvykle dělá.  
  
 ![Posuňte ovládací prvek bez posuvníků.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Příklad posouvání ovládacího prvku, který nepoužívá posuvníky  
  
 Příklady ovládacích prvků, které implementují tento ovládací prvek, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci scroll ovládacího vzoru, poznamenejte si následující pokyny a konvence:  
  
- Podřízené položky tohoto <xref:System.Windows.Automation.Provider.IScrollItemProvider>ovládacího prvku musí implementovat .  
  
- Posuvníky ovládacího prvku kontejneru nepodporují vzor ovládacího <xref:System.Windows.Automation.ScrollPattern> prvku. Musí podporovat <xref:System.Windows.Automation.RangeValuePattern> vzor ovládacího prvku místo.  
  
- Při posouvání se měří v procentech, všechny hodnoty nebo částky související s posunutí odstupňování musí být normalizovány do rozsahu 0 až 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> jsou nezávislé <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>na .  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  Pokud `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> pak by měla být nastavena na 100% a <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> měla by být nastavena na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobně, pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> pak by měla být nastavena na 100 procent a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> měla by být nastavena na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. To umožňuje klientovi automatizace uživatelského rozhraní <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> používat tyto hodnoty vlastností v rámci metody a zároveň se vyhnout [spor,](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) pokud se aktivuje směr klienta, který nemá zájem o posouvání.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>je specifické pro národní prostředí. Nastavení HorizontalScrollPercent = 100.0 musí nastavit umístění posouvání ovládacího prvku na ekvivalent jeho vpravo pozici pro jazyky, jako je angličtina, která čte zleva doprava. Alternativně pro jazyky, jako je arabština, které čtou zprava doleva, nastavení HorizontalScrollPercent = 100.0 musí nastavit umístění posouvání na pozici nejvíce vlevo.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>Požadované členy pro IScrollProvider  
 Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IScrollProvider>vyžadovány pro implementaci .  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Metoda|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>vyvolá tuto výjimku, <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> pokud ovládací prvek podporuje hodnoty výhradně <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> pro vodorovné nebo svislé posouvání, ale hodnota je předána.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, když je předána hodnota, kterou nelze převést na double.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá tuto výjimku, pokud je předána hodnota větší než 100 nebo <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>menší než 0 (s výjimkou -1, která je ekvivalentní ).|  
|<xref:System.InvalidOperationException>|Oba <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> a vyvolat tuto výjimku při pokusu o posouvání v nepodporovaném směru.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
