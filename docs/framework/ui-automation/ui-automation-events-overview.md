---
title: Přehled událostí automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
ms.openlocfilehash: 495e7d29c814164f4235d18569477b856cb09045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179899"
---
# <a name="ui-automation-events-overview"></a>Přehled událostí automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]oznámení o událostech je klíčovou funkcí pro asistenční technologie, jako jsou programy pro čtení z obrazovky a programy lupy obrazovky. Tito klienti automatizace uživatelského rozhraní sledovat události, které jsou [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vyvolány zprostředkovateli automatizace uživatelského rozhraní, když se něco stane v a použít informace k upozornění koncových uživatelů.  
  
 Efektivita je lepší tím, že umožňuje zprostředkovatele aplikací min. události selektivně, v závislosti na tom, zda jsou klienti přihlášeni k odběru těchto událostí, nebo vůbec, pokud žádní klienti jsou naslouchání pro všechny události.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Typy událostí  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]události spadají do následujících kategorií.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Změna vlastnosti|Je aktivována při [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] změně vlastnosti prvku nebo vzoru ovládacího prvku. Například pokud klient potřebuje sledovat ovládací prvek zaškrtávacího políčka aplikace, může <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> se zaregistrovat a poslouchat událost změny vlastnosti ve vlastnosti. Pokud je ovládací prvek zaškrtávacího políčka zaškrtnuto nebo nezaškrtnuto, zprostředkovatel vyvolá událost a klient může fungovat podle potřeby.|  
|Akce prvku|Vyvolána při změně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] výsledků z koncového uživatele nebo programové aktivity; například při klepnutí na tlačítko nebo <xref:System.Windows.Automation.InvokePattern>vyvolání prostřednictvím .|  
|Změna struktury|Je aktivována při [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] změně struktury stromu. Struktura se změní, když se nové [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky stanou viditelnými, skrytými nebo odebranými na ploše.|  
|Globální změna plochy|Je vyvolána, když dojde k akce globálního zájmu klienta, například když fokus přesune z jednoho prvku do druhého, nebo když se zavře okno.|  
  
 Některé události nemusí nutně znamenat, že stav ui se změnil. Pokud například uživatel zavede karty k textovému poli a potom klepne `TextChangedEvent` na tlačítko pro aktualizaci pole, a je aktivována i v případě, že uživatel ve skutečnosti text nezměnil. Při zpracování události může být nutné pro klientskou aplikaci zkontrolovat, zda se něco skutečně změnilo před provedením akce.  
  
 Následující události mohou být vyvolány i v případě, že se nezměnil stav ui.  
  
- `AutomationPropertyChangedEvent`(v závislosti na vlastnosti, která se změnila)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>Identifikátory událostí automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]události jsou <xref:System.Windows.Automation.AutomationEvent> identifikovány objekty. Vlastnost <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> obsahuje hodnotu, která jednoznačně identifikuje druh události.  
  
 Možné hodnoty <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> pro jsou uvedeny v následující tabulce, spolu s typem používaným pro argumenty události. Všimněte si, že identifikátory používané klienty a poskytovateli jsou identicky pojmenované pole z různých tříd.  
  
|Identifikátor klienta|Identifikátor zprostředkovatele|Typ argumentů události|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>
## <a name="ui-automation-event-arguments"></a>Argumenty událostí automatizace uživatelského rozhraní  
 Následující třídy zapouzdřují argumenty události.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Obsahuje informace o asynchronní načítání obsahu, včetně procento načítání dokončena.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Obsahuje informace o jednoduché události, která nevyžaduje žádná další data.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Obsahuje informace o změně vstupnífokus z jednoho prvku do druhého. Události tohoto typu jsou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vyvolány systémem, nikoli zprostředkovateli.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Obsahuje informace o změně hodnoty vlastnosti prvku nebo vzoru ovládacího prvku.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Obsahuje informace o změně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve stromu.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Obsahuje informace o zavření okna.|  
  
 Všechny třídy argumentů <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> události obsahují člena. Tento identifikátor je zapouzdřen v . <xref:System.Windows.Automation.AutomationEvent>  
  
 Objekty <xref:System.Windows.Automation.AutomationEvent> používané k identifikaci událostí jsou <xref:System.Windows.Automation.AutomationElementIdentifiers> získány zprostředkovateli <xref:System.Windows.Automation.DockPatternIdentifiers>z polí v a řízení tříd identifikátoru vzoru, jako jsou například . Ekvivalentní pole jsou získávána klientskými <xref:System.Windows.Automation.AutomationElement> aplikacemi z <xref:System.Windows.Automation.DockPattern>polí v polích a řídí třídy vzorů, jako je například .  
  
 Seznam identifikátorů událostí naleznete v [tématu Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Viz také

- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
