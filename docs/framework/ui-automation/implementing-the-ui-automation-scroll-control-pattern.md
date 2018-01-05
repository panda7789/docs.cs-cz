---
title: "Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9ad069a4670cc7e4c2281109d8df6afa55ea6dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider>, včetně informací o události a vlastnosti. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.ScrollPattern> – Vzor ovládacích prvků se používá pro podporu ovládacího prvku, který funguje jako posuvný kontejner pro kolekci podřízených objektů. Ovládací prvek není nutné používat posuvníky pro podporu posouvání funkcí, i když běžně nemá.  
  
 ![Posuňte se ovládací prvek bez posuvníky. ] (../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Příklad posouvání ovládací prvek, který nepoužívá posuvníky  
  
 Příklady ovládacích prvků, které implementují tento ovládací prvek najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků posuv, poznamenejte si následující pokyny a konvence:  
  
-   Musí implementovat podřízené objekty tohoto ovládacího prvku <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Posuvníky ovládacího prvku kontejner nepodporují <xref:System.Windows.Automation.ScrollPattern> – vzor ovládacích prvků. Musí podporovat <xref:System.Windows.Automation.RangeValuePattern> řízení vzor místo.  
  
-   Při posouvání se měří v procentech, všechny hodnoty nebo objemy související s posun odstupňování musí být normalizovány na rozsahu od 0 do 100.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> jsou nezávislé <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` pak <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> musí být nastavena na 100 % a <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> musí být nastavena na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobně pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` pak <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> musí být nastavena na 100 procent a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> musí být nastavena na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. To umožňuje automatizace uživatelského rozhraní klienta pro použití v rámci hodnoty těchto vlastností <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metoda při vyloučení [soupeřit podmínku](http://support.microsoft.com/default.aspx?scid=kb;en-us;317723) Pokud směrem k klient není zájem o posouvání, dojde k aktivaci.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>je specifická pro národní prostředí. Nastavení HorizontalScrollPercent = 100.0 musí nastavit posouvání umístění ovládacího prvku na ekvivalent nejvíce vpravo pozici pro jazyky, jako je angličtina, který čtení zleva doprava. Alternativně pro jazyky, jako je například arabština, který číst přímo na levé straně nastavení HorizontalScrollPercent = 100.0 musí nastavte umístění, přejděte na levou krajní pozici.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Požadované členy pro IScrollProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>vyvolá výjimku, pokud podporuje ovládacího prvku <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> hodnoty výhradně pro vodorovné nebo svislé posouvání, ale <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> je předána hodnota.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>Pokud je předaná hodnota, která nelze převést na datový typ double, vyvolá výjimku.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>vyvolá výjimku, pokud je předaná hodnota vyšší než 100 nebo menší než 0 (s výjimkou -1, která je ekvivalentní <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Obě <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> a <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> výjimku výjimku při pokusu o přejděte v nepodporované směru.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
