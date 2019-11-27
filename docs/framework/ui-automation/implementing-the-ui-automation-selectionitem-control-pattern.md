---
title: Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 53a5a739918e61d53b3102c2c85d4ef2b8425173
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447106"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor ovládacího prvku <xref:System.Windows.Automation.SelectionItemPattern> slouží k podpoře ovládacích prvků, které fungují jako jednotliví, volitelných podřízených položek kontejnerových ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider>. Příklady ovládacích prvků, které implementují vzor ovládacího prvku ovládacích SelectionItem, najdete v tématu [mapování vzoru řízení pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md) .  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku Výběr položky si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky pro jedno výběr, které spravují podřízené ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, jako je například posuvník **rozlišení obrazovky** v dialogovém okně **zobrazení vlastností** , by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider> a jejich podřízené položky by měly implementovat <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Vyžadovaná členové pro ISelectionItemProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>jsou vyžadovány následující vlastnosti, metody a události.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá se v případě, že se výběr v kontejneru významně změnil a vyžaduje odeslání více <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> a <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> události, než povoluje konstanta <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit>.|  
  
- Pokud je výsledkem <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>nebo <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jediná vybraná položka, je třeba vyvolat <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>. v opačném případě odešlete <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> podle potřeby.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Při pokusu o provedení některé z následujících akcí:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> se volá v kontejneru s jedním výběrem, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` a element je už vybraný.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> je volána v kontejneru s více výběry, kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` a je vybrán pouze jeden prvek.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> je volána v kontejneru s jedním výběrem, kde je již vybrán <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` a jiný prvek.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selection-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Ukázka zprostředkovatele fragmentů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
