---
title: Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 754af531a20805c53785a37695dce97bb7967a53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447128"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>, including information about events and properties. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.SelectionPattern> control pattern is used to support controls that act as containers for a collection of selectable child items. The children of this element must implement <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Selection control pattern, note the following guidelines and conventions:  
  
- Controls that implement <xref:System.Windows.Automation.Provider.ISelectionProvider> allow either single or multiple child items to be selected. For example, list box, list view, and tree view support multiple selections whereas combo box, slider, and radio button group support single selection.  
  
- Controls that have a minimum, maximum, and continuous range, such as the **Volume** slider control, should implement <xref:System.Windows.Automation.Provider.IRangeValueProvider> instead of <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
- Single-selection controls that manage child controls that implement <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, such as the **Screen Resolution** slider in the **Display Properties** dialog box or the **Color Picker** selection control from Microsoft Word (illustrated below), should implement <xref:System.Windows.Automation.Provider.ISelectionProvider>; their children should implement both <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Example of Color Swatch String Mapping  
  
- Menus do not support <xref:System.Windows.Automation.SelectionPattern>. If you are working with menu items that include both graphics and text (such as the **Preview Pane** items in the **View** menu in Microsoft Outlook) and need to convey state, you should implement <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Required Members for ISelectionProvider  
 The following properties, methods, and events are required for the <xref:System.Windows.Automation.Provider.ISelectionProvider> interface.  
  
|Required members|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Should support property changed events using <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> and <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Raised when a selection in a container has changed significantly and requires sending more addition and removal events than the <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> constant permits.|  
  
 The <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> and <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> properties can be dynamic. For example, the initial state of a control might not have any items selected by default, indicating that <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> is `false`. However, after an item is selected, the control must always have at least one item selected. Similarly, in rare cases, a control might allow multiple items to be selected on initialization, but subsequently allow only single selections to be made.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Exception Type|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|If the control is not enabled.|  
|<xref:System.InvalidOperationException>|If the control is hidden.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
