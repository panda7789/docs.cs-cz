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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: f6c4fd2e3d89645a7fff8c70f373e7ad7d70ad39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543731"
---
# <a name="ui-automation-events-overview"></a>Přehled událostí automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] oznamování událostí je klíčovou funkcí technologií pro usnadnění, například čtečky obrazovky a zvětšování. Tyto události sledování klientů automatizace uživatelského rozhraní, které jsou generovány při určité události ve zprostředkovateli automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a informace použijte k upozornění koncových uživatelů.  
  
 Zlepšení efektivity tím, že poskytovatel aplikace pro vyvolání události selektivně, v závislosti na tom, jestli všichni klienti přihlášeni těchto událostí nebo vůbec ne, pokud žádní klienti naslouchají a čekají nějaké události.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy událostí  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události spadají do následujících kategorií.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Změna vlastnosti|Vyvolá, když vlastnost [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element nebo ovládací prvek změny modelu. Například pokud klient potřebuje k monitorování aplikace ovládací prvek zaškrtávací políčko, se můžete zaregistrovat k naslouchání pro událost změny vlastnosti <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> vlastnost. Když je ovládací prvek zaškrtávací políčko zaškrtnuté nebo nezaškrtnuté, zprostředkovatel vyvolá událost a klient může fungovat podle potřeby.|  
|Akce – element|Aktivovaná při změně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] výsledky z koncový uživatel nebo programové aktivity, například při kliknutí nebo vyvolané prostřednictvím tlačítka <xref:System.Windows.Automation.InvokePattern>.|  
|Změna struktury|Vyvolá se, když struktury [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu změny. Struktura se změní při nové [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky budou viditelné, skrytá nebo odebrané v klientských počítačích.|  
|Globální změnu klasické pracovní plochy|Vyvoláno, když dojde k akcím globální zajímavé pro klienta, třeba když dojde k deaktivaci od jednoho prvku na jiný, nebo když se zavře okno.|  
  
 Některé události nemusí znamenat, že se změnil stav uživatelského rozhraní. Pokud uživatel karty polem pro zadání textu a pak klikne na tlačítko Aktualizovat pole, například `TextChangedEvent` dojde i v případě, že uživatel nezměnil skutečně text. Při zpracování události, může být nezbytné pro klientskou aplikaci ke kontrole, jestli nic ve skutečnosti se změnila před provedením akce.  
  
 Tyto události mohou být vyvolány, i když nedošlo ke změně stavu uživatelského rozhraní.  
  
-   `AutomationPropertyChangedEvent` (v závislosti na vlastnosti, které se změnily)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identifikátory událostí automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události jsou označeny <xref:System.Windows.Automation.AutomationEvent> objekty. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Vlastnost obsahuje hodnotu, která jednoznačně identifikuje typ události.  
  
 Možné hodnoty parametru <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> jsou uvedeny v následující tabulce, spolu s typ použitý pro argumenty události. Všimněte si, že identifikátory používané klienty a poskytovatelé jsou stejně jako s názvem pole z různých tříd.  
  
|Identifikátor klienta|Identifikátor zprostředkovatele|Argumenty typu události|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>Argumenty události automatizace uživatelského rozhraní  
 Následující třídy zapouzdření argumenty události.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Obsahuje informace o asynchronní načítání obsahu, včetně procento dokončení načítání.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Obsahuje informace o jednoduché události, která vyžaduje žádná další data.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Obsahuje informace o změně ve vstupní fokus z jednoho elementu do jiného. Události tohoto typu jsou vyvolány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému, nikoli podle poskytovatelů.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Obsahuje informace o změnu v hodnotě vlastnosti elementu nebo ovládací prvek modelu.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Obsahuje informace o změně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Obsahuje informace o znak pravé okno.|  
  
 Všechny události argument třídy, které obsahují <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> člena. Tento identifikátor je zapouzdřena v <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Objekty používané k identifikaci událostí jsou získány z polí v poskytovateli <xref:System.Windows.Automation.AutomationElementIdentifiers> a řízení, jako vzor identifikátoru třídy <xref:System.Windows.Automation.DockPatternIdentifiers>. Odpovídající pole se získávají pomocí klientské aplikace z polí v <xref:System.Windows.Automation.AutomationElement> a řízení, jako vzor třídy <xref:System.Windows.Automation.DockPattern>.  
  
 Seznam identifikátorů událostí najdete v tématu [událostí automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Viz také:
- [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
