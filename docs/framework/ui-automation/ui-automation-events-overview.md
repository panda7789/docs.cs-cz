---
title: Přehled událostí automatizace uživatelského rozhraní
description: Podívejte se na Přehled oznámení události automatizace uživatelského rozhraní Microsoftu. Zkontrolujte typy událostí, identifikátory událostí automatizace uživatelského rozhraní a argumenty události automatizace uživatelského rozhraní.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
ms.openlocfilehash: 4f51a31a433986822a9dba22bf8f17ade00bbb76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168094"
---
# <a name="ui-automation-events-overview"></a>Přehled událostí automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]oznámení o události je klíčovou funkcí pro asistenční technologie, jako jsou čtečky obrazovky a zvětšování obrazovky. Tito klienti automatizace uživatelského rozhraní sledují události, které jsou vyvolány zprostředkovateli automatizace uživatelského rozhraní, když se něco stane v nástroji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , a použije informace k upozorňování koncových uživatelů.  
  
 Efektivita se zlepšuje tím, že aplikacím poskytovatele umožní vyvolávat události selektivně, v závislosti na tom, jestli se k těmto událostem přihlásí, nebo ne vůbec, pokud žádní klienti neslouchají jakýmkoli událostem.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Typy událostí  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]události spadají do následujících kategorií.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Změna vlastnosti|Vyvolá se při [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] změně vlastnosti prvku nebo vzoru ovládacího prvku. Například pokud klient potřebuje monitorovat ovládací prvek zaškrtávacího políčka aplikace, může se zaregistrovat a naslouchat události změny vlastnosti u <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> Vlastnosti. Když je ovládací prvek zaškrtávací políčko zaškrtnuté nebo nezaškrtnuté, zprostředkovatel událost vyvolá a klient může v případě potřeby fungovat.|  
|Akce elementu|Vyvolá se, když dojde ke změně ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] výsledcích z koncového uživatele nebo programové aktivity, například při kliknutí nebo volání prostřednictvím tlačítka <xref:System.Windows.Automation.InvokePattern> .|  
|Změna struktury|Je aktivována, když dojde ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] změně struktury stromu. Struktura se změní, když [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se nové položky zobrazí, skryjí nebo odeberou na ploše.|  
|Globální změna plochy|Je aktivována, když dojde k akcím globálního zájmu na klienta, například když se fokus přesune z jednoho prvku na jiný nebo když se zavře okno.|  
  
 Některé události nemusí nutně znamenat, že došlo ke změně stavu uživatelského rozhraní. Například pokud uživatel zaškrtne pole pro zadání textu a potom klikne na tlačítko pro aktualizaci pole, `TextChangedEvent` je vyvolána i v případě, že uživatel samotný text nezměnil. Při zpracování události může být nutné, aby klientská aplikace kontrolovala, zda cokoli se před provedením akce skutečně změnila.  
  
 Následující události mohou být vyvolány i v případě, že se stav uživatelského rozhraní nezměnil.  
  
- `AutomationPropertyChangedEvent`(v závislosti na vlastnosti, která se změnila)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>Identifikátory událostí automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]události jsou identifikovány <xref:System.Windows.Automation.AutomationEvent> objekty. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>Vlastnost obsahuje hodnotu, která jednoznačně identifikuje druh události.  
  
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
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Obsahuje informace o změně fokusu vstupu z jednoho prvku na jiný. Události tohoto typu jsou vyvolány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systémem, nikoli poskytovateli.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Obsahuje informace o změně v hodnotě vlastnosti prvku nebo vzoru ovládacího prvku.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Obsahuje informace o změně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Obsahuje informace o zavírání okna.|  
  
 Všechny třídy argumentů události obsahují <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> člena. Tento identifikátor je zapouzdřený v <xref:System.Windows.Automation.AutomationEvent> .  
  
 <xref:System.Windows.Automation.AutomationEvent>Objekty, které slouží k identifikaci událostí, jsou získávány poskytovateli z polí v <xref:System.Windows.Automation.AutomationElementIdentifiers> a třídy identifikátoru vzoru ovládacího prvku, jako je například <xref:System.Windows.Automation.DockPatternIdentifiers> . Ekvivalentní pole jsou získána klientskými aplikacemi z polí v <xref:System.Windows.Automation.AutomationElement> a třídy vzoru ovládacích prvků, jako je například <xref:System.Windows.Automation.DockPattern> .  
  
 Seznam identifikátorů událostí najdete v tématu [události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Viz také

- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
