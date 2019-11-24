---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 2f96f3c7261882af58cd10038d729c4e723d6fa0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447952"
---
# <a name="ui-automation-properties-overview"></a>Přehled vlastností automatizace uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements. These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.  
  
 This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties. More specific information is given in the following topics:  
  
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)  
  
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a>Property Identifiers  
 Every property is identified by a number and a name. The names of properties are used only for debugging and diagnosis. Providers use the numeric IDs to identify incoming property requests. Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.  
  
 <xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes. For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.  
  
 The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.  
  
|Kinds of properties|Clients get IDs from|Providers get IDs from|  
|-------------------------|--------------------------|----------------------------|  
|Properties common to all elements (see following tables)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Position of a docking window|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|State of an element that can expand and collapse|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Properties of an item in a grid|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Properties of a grid|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Current and supported view of an element that has multiple views|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Properties of an element that moves over a range of values, such as a slider|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Properties of a scrolling window|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Status and container of an item that can be selected, as in a list|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Properties of a control that contains selection items|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Column and row headers of an item in a table|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Column and row headers, and orientation, of a table|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|State of a toggle control|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Capabilities of an element that can be moved, rotated, or resized|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Value and read/write capabilities of an element that has a value|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Capabilities and state of a window|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a>Properties by Category  
 The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>. These properties are common to all controls. All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.  
  
 The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> For specific information about each property, follow the link in the **Property Access** column.  
  
### <a name="display-characteristics"></a>Display Characteristics  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|není k dispozici|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Element Type  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identification  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interaction  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Support for Patterns  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a>Různé  
  
|Property identifier|Property access|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a>Lokalizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers should present the following properties in the language of the operating system:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a>Properties and Events  
 Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events. For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.  
  
 Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes. For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern. Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.  
  
 Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element. For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes. In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Clients listen for events by subscribing to them. Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods. For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](return-properties-from-a-ui-automation-provider.md)
- [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](raise-events-from-a-ui-automation-provider.md)
