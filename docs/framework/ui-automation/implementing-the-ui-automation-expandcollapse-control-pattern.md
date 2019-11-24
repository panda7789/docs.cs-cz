---
title: Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 073ff0727fc6aab1189f73a254aa95da60820cc3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447150"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní

> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).

This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, including information about properties, methods, and events. Links to additional references are listed at the end of the overview.

The <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern is used to support controls that visually expand to display more content and collapse to hide content. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions

When implementing the ExpandCollapse control pattern, note the following guidelines and conventions:

- Aggregate controls—built with child objects that provide the UI with expand/collapse functionality—must support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern whereas their child elements do not. For example, a combo box control is built with a combination of list box, button, and edit controls, but it is only the parent combo box that must support the <xref:System.Windows.Automation.ExpandCollapsePattern>.

  > [!NOTE]
  > An exception is the menu control, which is an aggregate of individual MenuItem objects. The MenuItem objects can support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern, but the parent Menu control cannot. A similar exception applies to the Tree and Tree Item controls.

- When the <xref:System.Windows.Automation.ExpandCollapseState> of a control is set to <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, any <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is currently inactive for the control and the only information that can be obtained using this control pattern is the <xref:System.Windows.Automation.ExpandCollapseState>. If any child objects are subsequently added, the <xref:System.Windows.Automation.ExpandCollapseState> changes and <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is activated.

- <xref:System.Windows.Automation.ExpandCollapseState> refers to the visibility of immediate child objects only; it does not refer to the visibility of all descendant objects.

- Expand and Collapse functionality is control-specific. The following are examples of this behavior.

  - The Office Personal Menu can be a tri-state MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> and <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) where the control specifies the state to adopt when an <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called.

  - Calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> on a TreeItem may display all descendants or only immediate children.

  - If calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> on a control maintains the state of its descendants, a visibility change event should be sent, not a state change event If the parent control does not maintain the state of its descendants when collapsed, the control may destroy all the descendants that are no longer visible and raise a destroyed event; or it may change the <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> for each descendant and raise a visibility change event.

- To guarantee navigation, it is desirable for an object to be in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree (with appropriate visibility state) regardless of its parents <xref:System.Windows.Automation.ExpandCollapseState>. If descendants are generated on demand, they may only appear in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree after being displayed for the first time or only while they are visible.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Required Members for IExpandCollapseProvider

The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.

|Required members|Member type|Poznámky|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Vlastnost|Žádné|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Žádné|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Žádné|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Událost|This control has no associated events; use this generic delegate.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Výjimky

Providers must throw the following exceptions.

|Typ výjimky|Podmínka|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|Either <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called when the <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|

## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
