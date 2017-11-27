---
title: "Události automatizace uživatelského rozhraní pro klienty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
caps.latest.revision: "32"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1dfb4c1acd12b58d5c4f032ebe0ad8c56fc0db87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-events-for-clients"></a>Události automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události se používají klienti automatizace uživatelského rozhraní.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Umožňuje klientům přihlásit k odběru událostí, které vás zajímají. Tato funkce zlepšuje odstraněním potřeby průběžně všechny dotazování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy v systému a zjistěte, jestli se změnil jakékoli informace, struktura nebo stavu.  
  
 Efektivita je taky vylepšené podle možnost tak, aby naslouchala událostem pouze v rámci definován obor. Například můžete klienta naslouchat události změny fokus na všech [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky ve stromu nebo na pouze jeden prvek a jeho následníky.  
  
> [!NOTE]
>  Nepředpokládejte, že jsou všechny možné události aktivováno [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zprostředkovatele. Ne všechny změny vlastností způsobí například události, které má být aktivována poskytovateli standardní proxy pro [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky.  
  
 Pro větší přehled o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, viz [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Klientské aplikace přihlásit k odběru událostí konkrétní typ tak, že zaregistrujete obslužnou rutinu události pomocí jedné z následujících metod.  
  
|Metoda|Typ události|Argumenty typu události|Typ delegáta|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Změnu fokusu|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Změna vlastnosti|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Změnu struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Všechny ostatní události, identifikovaný<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs>nebo<xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Před voláním metody, je nutné vytvořit metody delegáta pro zpracování události. Pokud dáváte přednost, můžete zpracovat různé druhy události v jedné metody a předat této metodě v několika volání do jedné z metod v tabulce. Například jeden <xref:System.Windows.Automation.AutomationEventHandler> se dá nastavit pro zpracování různých událostí jinak souladu se <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Při zpracování události okno zavřít, přetypovat typ argumentu, který je předán do obslužné rutiny události jako <xref:System.Windows.Automation.WindowClosedEventArgs>. Protože [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] element intervalu pro správu a již není platná, nelze použít `sender` parametr načíst informace o; použít <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> místo.  
  
> [!CAUTION]
>  Pokud vaše aplikace může přijímat události z vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nepoužívejte vaší aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákno přihlásit k odběru událostí nebo zrušit. Díky tomu může způsobit nepředvídatelné chování. Další informace najdete v tématu [problémy dělení na vlákna automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Při vypnutí nebo když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události jsou již v zájmu aplikace, klienti automatizace uživatelského rozhraní by měly volat jednu z následujících metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován pomocí <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován pomocí <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Zruší registraci všech registrovaných obslužných rutin události.|  
  
 Příklad kódu, najdete v části [přihlásit k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Viz také  
 [Přihlásit k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)  
 [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Ukázka TrackFocus](http://msdn.microsoft.com/en-us/4a91c0af-6bb5-4d38-a743-cf136f268fc9)
