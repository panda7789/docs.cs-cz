---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: c178283b18aaf2c406292d9ab7e12a24c882c102
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447039"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string. This string can be editable, depending on the control and its settings. For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Value control pattern, note the following guidelines and conventions:  
  
- Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control. The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.  
  
 ![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Example of an Editable List Item  
  
- Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>. However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>. However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values. Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.  
  
 ![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Example of Color Swatch String Mapping  
  
- A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Required Members for IValueProvider  
 The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Required members|Member type|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Žádné|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   If a new value cannot be converted from a string to a format the control recognizes.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   When an attempt is made to manipulate a control that is not enabled.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [ValuePattern Insert Text Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
