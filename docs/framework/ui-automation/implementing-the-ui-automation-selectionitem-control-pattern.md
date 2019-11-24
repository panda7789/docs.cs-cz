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
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, including information about properties, methods, and events. Links to additional references are listed at the end of the overview.  
  
 The <xref:System.Windows.Automation.SelectionItemPattern> control pattern is used to support controls that act as individual, selectable child items of container controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider>. For examples of controls that implement the SelectionItem control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Selection Item control pattern, note the following guidelines and conventions:  
  
- Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box, should implement <xref:System.Windows.Automation.Provider.ISelectionProvider> and their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Required Members for ISelectionItemProvider  
 The following properties, methods, and events are required for implementing <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Required members|Member type|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Raised when a selection in a container has changed significantly and requires sending more <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> and <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.|  
  
- If the result of a <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, an <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, or a <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> is a single selected item, an <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> should be raised; otherwise send <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> as appropriate.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|When any of the following are attempted:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and an element is already selected.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> is called on a multiple-selection container where <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` and only one element is selected.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> is called on a single-selection container where <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` and another element is already selected.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selection-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Fragment Provider Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
