---
title: Události automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b4ab95470a1b377d1768cf30b32f170b544d225e
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305789"
---
# <a name="ui-automation-events-for-clients"></a>Události automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události se používají klienti automatizace uživatelského rozhraní.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umožňuje klientům přihlášení k odběru událostí, které vás zajímají. Tato schopnost zvyšuje výkon tím eliminuje nutnost všechny neustále dotazovat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky v systému, abyste viděli, jestli se změnil všechny informace, struktury nebo stavu.  
  
 Efektivita je také vylepšeno o možnost naslouchat událostem pouze v rámci definovaného oboru. Například klient může naslouchat se události fokusu změny na všech [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky ve stromové struktuře, nebo na právě jeden element a jejích potomků.  
  
> [!NOTE]
>  Nepředpokládejte, že jsou všechny možné události vyvolané službou [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zprostředkovatele. Například způsobit, že ne všechny změny vlastností události navýšit tak, že standardní proxy zprostředkovatelé pro [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky.  
  
 Širší přehled [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, viz [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Klientské aplikace přihlásit k odběru událostí určitého typu, když si zaregistrujete obslužné rutiny události pomocí jedné z následujících metod.  
  
|Metoda|Typ události|Argumenty typu události|Typ delegáta|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Změnit fokus|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Změna vlastnosti|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Změna struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Všechny další události, identifikovaný <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> Nebo <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Před voláním metody, je nutné vytvořit metody delegáta pro zpracování události. Pokud dáváte přednost, můžete zpracovávat různé druhy událostí v jedné metody a předat této metodě ve více voláních metod v tabulce. Například jeden <xref:System.Windows.Automation.AutomationEventHandler> můžete nastavit pro zpracování různých události odlišně podle <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Pro zpracování událostí okno zavřeno, přetypování, která je předána obslužné rutiny události jako typ argumentu <xref:System.Windows.Automation.WindowClosedEventArgs>. Protože [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] – element pro okno už není platná, nelze použít `sender` parametr k načtení informací; použijte <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> místo toho.  
  
> [!CAUTION]
>  Pokud vaše aplikace může přijímat události z vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nepoužívejte vaší aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákno přihlásit k odběru události, nebo k odhlášení odběru. To může vést k nepředvídatelné chování. Další informace najdete v tématu [problémy dělení na vlákna uživatelského rozhraní automatizace](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Při vypnutí nebo když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události už nejsou zajímavé pro aplikace, klienti automatizace uživatelského rozhraní by měly volat jednu z následujících metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován prostřednictvím metody <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován prostřednictvím metody <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, který byl zaregistrován prostřednictvím metody <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Zruší registraci všech registrovaných obslužných rutin události.|  
  
 Příklad kódu naleznete v tématu [přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Viz také:
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
- [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Ukázka TrackFocus](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
