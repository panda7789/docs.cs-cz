---
title: Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 60b2b8b8e07cfec9000ddd974891070b625fde01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194110"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider>, včetně informací o události a vlastnosti. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.ScrollPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvek, který funguje jako kontejner posuvný kolekce podřízených objektů. Ovládací prvek se nevyžaduje použití posuvníků pro podporu posouvání funkcí, i když obvykle dělá.  
  
 ![Posune ovládací prvek bez posuvníků. ](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Příklad posouvání ovládacího prvku, který nepoužívá posuvníky  
  
 Příklady ovládacích prvků, které implementují tohoto ovládacího prvku, naleznete v tématu [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků posuv, mějte na paměti následující pokyny a konvence:  
  
-   Podřízené položky tohoto ovládacího prvku musí implementovat <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Posuvníky ovládací prvek kontejneru nepodporují <xref:System.Windows.Automation.ScrollPattern> – vzor ovládacích prvků. Musí podporovat <xref:System.Windows.Automation.RangeValuePattern> místo toho řídí model.  
  
-   Při posouvání se měří v procentech, všechny hodnoty nebo objemy související, přejděte k ukončení musí být normalizovaná do rozsahu od 0 do 100.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> platí bez ohledu <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` pak <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> musí být nastavená na 100 % a <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> by mělo být nastavené <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobně pokud <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` pak <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> musí být nastavená na 100 procent a <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> by mělo být nastavené <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. To umožňuje klientům automatizace uživatelského rozhraní použijte tyto hodnoty vlastností v rámci <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metoda současně vám [časování](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) Pokud směru klient není zájem posouvání, dojde k aktivaci.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> je specifických pro národní prostředí. Nastavení HorizontalScrollPercent = 100.0 musí posouvání umístění ovládacího prvku nastavte na ekvivalentní pozici úplně vpravo jazyků, jako jsou angličtinu, která čteny zleva doprava. Můžete také pro jazyků, jako je arabština, který číst přímo na levé straně, nastavení HorizontalScrollPercent = 100.0. musíte nastavit umístění přejděte úplně vlevo pozici.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Požadované členy pro IScrollProvider  
 Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Tento model ovládací prvek nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> vyvolá tuto výjimku, pokud ovládací prvek podporuje <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> hodnoty výhradně pro vodorovné nebo svislé posouvání, ale <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> je předána hodnota.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> vyvolá tuto výjimku při předaný hodnotu, která se nedá převést na typ double.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> vyvolá tuto výjimku, pokud je předána hodnota větší než 100 nebo menší než 0. (-1, což je ekvivalentní s výjimkou <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Obě <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> a <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> vyvolávají tuto výjimku při pokusu o posouvejte nepodporovaný směr.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
