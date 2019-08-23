---
title: Události automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: 3bb41fa476f15c5fc16a942cc0c82fd8e0aba7bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911670"
---
# <a name="ui-automation-events-for-clients"></a>Události automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma popisuje, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jak jsou události používány klienty automatizace uživatelského rozhraní.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje klientům přihlásit se k odběru událostí zájmu. Tato funkce zvyšuje výkon tím, že eliminuje nutnost nepřetržitého dotazování všech [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků v systému, aby bylo možné zjistit, zda se změnily informace, struktury nebo stav.  
  
 Efektivita je také vylepšená díky schopnosti naslouchat pouze událostem v rámci definovaného oboru. Například klient může naslouchat událostem změny fokusu u všech [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvků stromu nebo pouze jednoho prvku a jeho následníků.  
  
> [!NOTE]
> Nepředpokládá se, že [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zprostředkovatel vyvolal všechny možné události. Například ne všechny změny vlastností způsobují, že události budou vyvolány standardními poskytovateli proxy [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky a.  
  
 Širší zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Klientské aplikace se přihlásí k odběru událostí určitého druhu registrací obslužné rutiny události pomocí jedné z následujících metod.  
  
|Metoda|Typ události|Typ argumentů události|Typ delegáta|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Změna fokusu|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Změna vlastnosti|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Změna struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Všechny ostatní události, které jsou označeny<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> Nebo <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Před voláním metody je nutné vytvořit metodu delegáta pro zpracování události. Pokud chcete, můžete zpracovávat různé druhy událostí v rámci jediné metody a předat tuto metodu ve více voláních jedné z metod v tabulce. Například jedna <xref:System.Windows.Automation.AutomationEventHandler> může být nastavena tak, aby zpracovávala různé události odlišně v <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>závislosti na.  
  
> [!NOTE]
> Chcete-li zpracovat události uzavřené v okně, přetypujte typ argumentu, který je předán obslužné rutině události jako <xref:System.Windows.Automation.WindowClosedEventArgs>. Vzhledem k tomu, že `sender` <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> elementprooknojižneníplatný,nemůžetepoužítparametrpronačteníinformací;[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] použijte místo toho.  
  
> [!CAUTION]
>  Pokud vaše aplikace může přijímat události sami [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nepoužívejte [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákno vaší aplikace k přihlášení k odběru událostí nebo k odhlášení odběru. To může vést k nepředvídatelnému chování. Další informace najdete v tématu [problémy s vlákny pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Při vypnutí nebo pokud [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události již nejsou důležité pro aplikaci, klienti automatizace uživatelského rozhraní by měli volat jednu z následujících metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Zruší registraci obslužné rutiny události, která byla zaregistrována pomocí <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, která byla zaregistrována pomocí <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Zruší registraci obslužné rutiny události, která byla zaregistrována pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Zruší registraci všech zaregistrovaných obslužných rutin událostí.|  
  
 Příklad kódu naleznete v tématu [přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Viz také:

- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
- [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Ukázka TrackFocus](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
