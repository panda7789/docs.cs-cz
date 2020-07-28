---
title: Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
description: Viz pokyny a konvence pro implementaci vzoru ovládacího prvku ovládacích SelectionItem v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní ISelectionItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 441417aa370563a9ce8b513be6ca4507b21e1e4a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163549"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider> , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.SelectionItemPattern>Vzor ovládacího prvku se používá pro podporu ovládacích prvků, které fungují jako jednotliví, volitelných podřízených položek kontejnerových ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> . Příklady ovládacích prvků, které implementují vzor ovládacího prvku ovládacích SelectionItem, najdete v tématu [mapování vzoru řízení pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md) .  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku Výběr položky si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky pro jedno výběr, které spravují podřízené ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> , například posuvník **rozlišení obrazovky** v dialogovém okně **zobrazení vlastností** , by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider> a jejich podřízené položky by měly implementovat i <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>Vyžadovaná členové pro ISelectionItemProvider  
 Pro implementaci jsou vyžadovány následující vlastnosti, metody a události <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá se v případě, že se výběr v kontejneru významně změnil a vyžaduje odeslání více <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> událostí a, <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> povoluje konstanta.|  
  
- Pokud <xref:System.Windows.Automation.SelectionItemPattern.Select%2A> je výsledkem, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A> nebo a <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jedinou vybranou položkou, <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> měla by být vyvolána. jinak odešlete <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> podle potřeby.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Při pokusu o provedení některé z následujících akcí:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>se volá v kontejneru s jedním výběrem, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a je už vybraný element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána v kontejneru vícenásobného výběru, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` je vybrán pouze jeden prvek.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>se volá v kontejneru s jedním výběrem, kde <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` a je už vybraný jiný element.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selection-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Ukázka zprostředkovatele fragmentů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
