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
ms.openlocfilehash: 5f9362814eb671a6d7a111cadb96be6d06f5cb3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441489"
---
# <a name="ui-automation-events-overview"></a>Přehled událostí automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 oznámení o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události je klíčovou funkcí pro asistenční technologie, jako jsou čtečky obrazovky a zvětšování obrazovky. Tito klienti pro automatizaci uživatelského rozhraní sledují události, které jsou vyvolány zprostředkovateli automatizace uživatelského rozhraní, když se něco stane v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a použije informace k oznamování koncovým uživatelům.  
  
 Efektivita se zlepšuje tím, že aplikacím poskytovatele umožní vyvolávat události selektivně, v závislosti na tom, jestli se k těmto událostem přihlásí, nebo ne vůbec, pokud žádní klienti neslouchají jakýmkoli událostem.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy událostí  
 události [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spadají do následujících kategorií.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Změna vlastnosti|Vyvolá se při změně vlastnosti prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nebo vzoru ovládacího prvku. Například pokud klient potřebuje monitorovat ovládací prvek zaškrtávacího políčka aplikace, může se zaregistrovat k naslouchání události změny vlastnosti u vlastnosti <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A>. Když je ovládací prvek zaškrtávací políčko zaškrtnuté nebo nezaškrtnuté, zprostředkovatel událost vyvolá a klient může v případě potřeby fungovat.|  
|Akce elementu|Vyvolá se, když dojde ke změně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] výsledků od koncového uživatele nebo programové aktivity. například když kliknete na tlačítko nebo vyvoláte prostřednictvím <xref:System.Windows.Automation.InvokePattern>.|  
|Změna struktury|Je aktivována, když dojde ke změně struktury [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Struktura se změní, když budou nové položky [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] viditelné, skryté nebo odebrané na ploše.|  
|Globální změna plochy|Je aktivována, když dojde k akcím globálního zájmu na klienta, například když se fokus přesune z jednoho prvku na jiný nebo když se zavře okno.|  
  
 Některé události nemusí nutně znamenat, že došlo ke změně stavu uživatelského rozhraní. Například pokud uživatel na kartě pro zadání textu a následně klikne na tlačítko pro aktualizaci pole, je vyvolána `TextChangedEvent`, a to i v případě, že uživatel samotný text nezměnil. Při zpracování události může být nutné, aby klientská aplikace kontrolovala, zda cokoli se před provedením akce skutečně změnila.  
  
 Následující události mohou být vyvolány i v případě, že se stav uživatelského rozhraní nezměnil.  
  
- `AutomationPropertyChangedEvent` (v závislosti na vlastnosti, která se změnila)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identifikátory událostí automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události jsou identifikovány pomocí objektů <xref:System.Windows.Automation.AutomationEvent>. Vlastnost <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> obsahuje hodnotu, která jednoznačně identifikuje druh události.  
  
 Možné hodnoty pro <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> jsou uvedeny v následující tabulce společně s typem použitým pro argumenty události. Všimněte si, že identifikátory používané klienty a zprostředkovateli jsou identicky s názvem pole z různých tříd.  
  
|Identifikátor klienta|Identifikátor poskytovatele|Typ argumentů události|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>Argumenty události pro automatizaci uživatelského rozhraní  
 Následující třídy zapouzdřují argumenty události.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Obsahuje informace o asynchronním načítání obsahu, včetně procenta dokončeného načítání.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Obsahuje informace o jednoduché události, která nevyžaduje žádná další data.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Obsahuje informace o změně fokusu vstupu z jednoho prvku na jiný. Události tohoto typu jsou vyvolány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]m systémem, nikoli poskytovateli.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Obsahuje informace o změně v hodnotě vlastnosti prvku nebo vzoru ovládacího prvku.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Obsahuje informace o změně stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Obsahuje informace o zavírání okna.|  
  
 Všechny třídy argumentů události obsahují <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> člen. Tento identifikátor je zapouzdřený v <xref:System.Windows.Automation.AutomationEvent>.  
  
 Objekty <xref:System.Windows.Automation.AutomationEvent> používané k identifikaci událostí jsou získávány poskytovateli z polí v <xref:System.Windows.Automation.AutomationElementIdentifiers> a třídách identifikátoru vzoru ovládacího prvku, jako je například <xref:System.Windows.Automation.DockPatternIdentifiers>. Ekvivalentní pole jsou získána klientskými aplikacemi z polí v <xref:System.Windows.Automation.AutomationElement> a tříd vzoru ovládacích prvků, jako je například <xref:System.Windows.Automation.DockPattern>.  
  
 Seznam identifikátorů událostí najdete v tématu [události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Viz také:

- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
