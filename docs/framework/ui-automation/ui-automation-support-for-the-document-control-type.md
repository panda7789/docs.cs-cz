---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Document
- Document control type
- UI Automation, Document control type
ms.assetid: a79d594b-1ca0-4543-8dac-afd2c645201d
ms.openlocfilehash: 18c7e59ec4e4c8cdcb668bef239abc6c0004379d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449472"
---
# <a name="ui-automation-support-for-the-document-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic provides information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support for the Document control type. In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], a control type is a set of conditions that a control must meet in order to use the <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> property. The conditions include specific guidelines for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values, and control patterns.  
  
 Document controls let a user view and manipulate multiple pages of text. Unlike edit controls which only support a simple line of unformatted text, document controls can host text that is richly styled and formatted.  
  
 The following sections define the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, properties, control patterns, and events for the Document control type. The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requirements apply to all document controls, whether [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], or [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="required-ui-automation-tree-structure"></a>Required UI Automation Tree Structure  
 The following table depicts the control view and the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree that pertains to document controls and describes what can be contained in each view. For more information about the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Control View|Content View|  
|------------------|------------------|  
|Dokument<br /><br /> -   Varies|Dokument<br /><br /> -   Varies|  
  
## <a name="required-ui-automation-properties"></a>Required UI Automation Properties  
 The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties whose value or definition is especially relevant to document controls. For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Property|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|See notes.|The value of this property needs to be unique across all controls in an application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|See notes.|The outermost rectangle that contains the whole control.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|See notes.|The document has a clickable point that will cause the document of one of its elements in the document container to have focus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Dokument|This value is the same for all UI frameworks.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|The document control is always included in the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|The document control is always included in the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|See notes.|If the control can receive keyboard focus, it must support this property.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|See notes.|The value of this property should be the label of the document control. Typically, the title of the document is used.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"document"|Localized string corresponding to the Document control type.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|See notes.|The document control typically gets its names from the file name it is loaded from. This is often displayed in a containing window or frame title.|  
  
## <a name="required-ui-automation-control-patterns"></a>Required UI Automation Control Patterns  
 The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns required to be supported by document controls. For more information about control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Control Pattern|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depends|The document control can span larger than that span of the viewport. The control should support the Scroll control pattern if the content is scrollable.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Požadováno|The document control can span larger than that span of the viewport. The control should support the Scroll control pattern if the content is scrollable.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Never|The document control does not support this control pattern because the contents of the control often span more than one page. UI Automation clients should use <xref:System.Windows.Automation.TextPattern> to obtain text information about a document.|  
  
## <a name="required-ui-automation-events"></a>Required UI Automation Events  
 The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events required to be supported by all document controls. For more information about events, see [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Event|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> property-changed event.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Depends|If the control supports the Selection control pattern, it must support this event.|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> property-changed event.|Never|Žádné|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.Document>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
