---
title: Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: aef1d31499f65834fa1268147e45f82294fe560a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935691"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.ISelectionItemProvider>implementaci, včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor ovládacího prvku se používá pro podporu ovládacích prvků, které fungují jako jednotliví, volitelných podřízených položek kontejnerových ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider>. <xref:System.Windows.Automation.SelectionItemPattern> Příklady ovládacích prvků, které implementují vzor ovládacího prvku ovládacích SelectionItem, najdete v tématu [mapování vzoru řízení pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md) .  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku Výběr položky si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky pro jedno výběr, které spravují podřízené ovládací <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>prvky, které implementují, jako je posuvník **rozlišení obrazovky** v dialogovém okně **zobrazení vlastností** , by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider> a jejich podřízené objekty by měly implementovat obojí <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a .<xref:System.Windows.Automation.Provider.ISelectionItemProvider>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Vyžadovaná členové pro ISelectionItemProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>jsou vyžadovány následující vlastnosti, metody a události.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá se v případě, že se výběr v kontejneru významně změnil a vyžaduje <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> odeslání <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> více událostí a <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> , než povoluje konstanta.|  
  
- <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>Pokud je výsledkem <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, nebo a <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jedinou vybranou položkou, <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> měla by být vyvolána. jinak odešlete <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> podle potřeby.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Při pokusu o provedení některé z následujících akcí:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>se volá v kontejneru s jedním výběrem, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a je už vybraný element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána v kontejneru vícenásobného výběru, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` je vybrán pouze jeden prvek.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>se volá v kontejneru s jedním výběrem, kde <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` a je už vybraný jiný element.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Ukázka zprostředkovatele fragmentů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
