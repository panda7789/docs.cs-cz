---
title: "Přehled událostí automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9634c686d23503dcb4deae171f0023055c41ce2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-events-overview"></a>Přehled událostí automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]oznámení o události je klíčovou funkcí pro usnadnění technologie, jako je například čtečky obrazovky a zvětšování zobrazení. Tyto události sledování klientů automatizace uživatelského rozhraní, které jsou aktivovány zprostředkovatelé automatizace uživatelského rozhraní když v se stane něco [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a využít tyto informace mají obdržet oznámení koncovým uživatelům.  
  
 Zlepšení efektivity tím, že poskytovatel aplikace umožňuje aktivovat události selektivně, v závislosti na tom, jestli všechny klienty přihlášeni k události, nebo vůbec, pokud jsou pro všechny události, naslouchá žádní klienti.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy událostí  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]události spadají do následujících kategorií.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Změna vlastnosti|Vyvolá, když vlastnost [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element nebo ovládací prvek vzor změny. Například pokud klient potřebuje ke sledování aplikace ovládací prvek zaškrtávací políčko, se můžete zaregistrovat pro naslouchání pro událost změny vlastnosti <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> vlastnost. Pokud ovládací prvek zaškrtávací políčko je zaškrtnuté nebo nezaškrtnuté, zprostředkovatele vyvolá událost, a klient může fungovat podle potřeby.|  
|Element akce|Vyvolá, když změnu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] výsledky z koncového uživatele nebo programové aktivity, například pokud kliknutí na tlačítko nebo vyvolat prostřednictvím <xref:System.Windows.Automation.InvokePattern>.|  
|Změnu struktury|Vyvolá, když strukturu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu změny. Struktura změny při vydání nových [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky stane viditelné, skrytá nebo odebraných na ploše.|  
|Globální plochy změn|Vyvolá, když dojde k akcí globální zájmu klientovi, například když dojde k deaktivaci od jednoho prvku na jiný, nebo při zavření okna.|  
  
 Některé události neznamenají, že došlo ke změně stavu rozhraní. Například pokud uživatel karty na textového pole a poté kliknutím na tlačítko Aktualizovat pole `TextChangedEvent` se vyvolá, i když uživatel ve skutečnosti nezměnila text. Při zpracování události, může být nezbytné pro klientskou aplikaci, zkontrolujte, zda nic ve skutečnosti se změnila před provedením akce.  
  
 Tyto události může dosáhnout i v případě, že stav rozhraní nebylo změněno.  
  
-   `AutomationPropertyChangedEvent`(v závislosti na vlastnost, která se změnila)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identifikátory událostí automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]události jsou identifikovány <xref:System.Windows.Automation.AutomationEvent> objekty. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Vlastnost obsahuje hodnotu, která jednoznačně identifikuje typ události.  
  
 Možné hodnoty <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> jsou uvedeny v následující tabulce, společně s typu použitého pro argumenty událostí. Všimněte si, že identifikátory používané klienty a poskytovatelé stejně jako s názvem pole z různých tříd.  
  
|Identifikátor klienta|Identifikátor zprostředkovatele|Argumenty typu události|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>Argumenty událostí automatizace uživatelského rozhraní  
 Následující třídy zapouzdřovat argumenty událostí.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Obsahuje informace o asynchronní načítání obsah, včetně Procento načítání byla dokončena.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Obsahuje informace o jednoduchá událost, která vyžaduje žádná další data.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Obsahuje informace o změně v zaměření pro vstup od jednoho prvku na jiný. Události tohoto typu jsou vydané [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému není poskytovateli.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Obsahuje informace o změnu v hodnotě vlastnosti vzorku element nebo ovládací prvek.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Obsahuje informace o změnu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Obsahuje informace o zavření okna.|  
  
 Všechny třídy událostí argument obsahovat <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> člen. Tento identifikátor je zapouzdřené v <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Objekty použité k identifikaci událostí jsou získány zprostředkovatelé z pole v <xref:System.Windows.Automation.AutomationElementIdentifiers> a řídit vzor identifikátor třídy, jako <xref:System.Windows.Automation.DockPatternIdentifiers>. Ekvivalentní pole jsou získány pomocí klientských aplikací z pole v <xref:System.Windows.Automation.AutomationElement> a řídit vzor třídy, jako <xref:System.Windows.Automation.DockPattern>.  
  
 Seznam identifikátorů událostí najdete v tématu [událostí automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Viz také  
 [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Přihlásit k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
