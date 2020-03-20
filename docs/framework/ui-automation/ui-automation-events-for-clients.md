---
title: Události automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: d7105e9211c35e7d6125c3017e8b4b829a25b128
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179907"
---
# <a name="ui-automation-events-for-clients"></a>Události automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] popisuje, jak jsou události používány klienty automatizace uživatelského rozhraní.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje klientům přihlásit se k odběru zajímavých událostí. Tato funkce zlepšuje výkon tím, že eliminuje potřebu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] neustále dotazovat všechny prvky v systému, aby zjistili, zda došlo ke změně informací, struktury nebo stavu.  
  
 Efektivita je také lepší schopnost naslouchat událostem pouze v rámci definovaného rozsahu. Klient může například naslouchat pro změny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zaměření události na všechny prvky ve stromu nebo pouze na jeden prvek a jeho potomci.  
  
> [!NOTE]
> Nepředpokládejte, že všechny možné [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události jsou vyvolány zprostředkovatelem. Například ne všechny změny vlastností způsobit události, které mají být vyvolány standardní zprostředkovatelé proxy pro Windows Forms a Win32 ovládací prvky.  
  
 Širší zobrazení událostí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Klientské aplikace se přihlásí k odběru událostí určitého druhu registrací obslužné rutiny události pomocí jedné z následujících metod.  
  
|Metoda|Event Type|Typ argumentů události|Typ delegáta|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Změna fokusu|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Změna vlastnosti|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Změna struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Všechny ostatní události identifikované<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> nebo <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Před voláním metody je nutné vytvořit metodu delegáta pro zpracování události. Pokud dáváte přednost, můžete zpracovat různé druhy událostí v jedné metodě a předat tuto metodu ve více voláních jedné z metod v tabulce. Například jeden <xref:System.Windows.Automation.AutomationEventHandler> lze nastavit pro zpracování různých událostí odlišně podle <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
> Chcete-li zpracovat události uzavřené okno, přetypovat typ <xref:System.Windows.Automation.WindowClosedEventArgs>argumentu, který je předán obslužné rutině události jako . Vzhledem [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k tomu, že prvek pro okno `sender` již není platný, nelze parametr použít k načtení informací; místo <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> toho použít.  
  
> [!CAUTION]
> Pokud vaše aplikace může přijímat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]události z vlastní , [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nepoužívejte vlákno aplikace k odběru událostí nebo odhlásit. To může vést k nepředvídatelnému chování. Další informace naleznete v [tématu Problémy s automatizací procesů v uživatelském rozhraní](ui-automation-threading-issues.md).  
  
 Při vypnutí nebo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] když události již nejsou zajímavé pro aplikaci, klienti automatizace uživatelského rozhraní by měl volat jednu z následujících metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Zruší registraci obslužné <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>rutiny události, která byla zaregistrována pomocí .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Zruší registraci obslužné <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>rutiny události, která byla zaregistrována pomocí .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Zruší registraci obslužné <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>rutiny události, která byla zaregistrována pomocí .|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Zruší registraci všech registrovaných obslužných rutin událostí.|  
  
 Například kód, najdete [v tématu Přihlásit se k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Viz také

- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
- [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md)
- [Ukázka trackfocusu](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
