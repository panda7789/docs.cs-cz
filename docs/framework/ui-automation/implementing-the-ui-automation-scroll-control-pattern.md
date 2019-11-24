---
title: Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: d146ba67f4fe3f5fda6196231f96f428f702086a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447161"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementace vzoru ovládacích prvků posuv pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IScrollProvider>, including information about events and properties. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.ScrollPattern> control pattern is used to support a control that acts as a scrollable container for a collection of child objects. The control is not required to use scrollbars to support the scrolling functionality, although it commonly does.  
  
 ![Scroll control without scrollbars.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Example of a Scrolling Control that Does Not Use Scrollbars  
  
 For examples of controls that implement this control, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Scroll control pattern, note the following guidelines and conventions:  
  
- The children of this control must implement <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
- The scrollbars of a container control do not support the <xref:System.Windows.Automation.ScrollPattern> control pattern. They must support the <xref:System.Windows.Automation.RangeValuePattern> control pattern instead.  
  
- When scrolling is measured in percentages, all values or amounts related to scroll graduation must be normalized to a range of 0 to 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> and <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> are independent of the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
- If <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` then <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> should be set to 100% and <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> should be set to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Likewise, if <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` then <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> should be set to 100 percent and <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> should be set to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. This allows a UI Automation client to use these property values within the <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> method while avoiding a [race condition](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) if a direction the client is not interested in scrolling becomes activated.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> is locale-specific. Setting HorizontalScrollPercent = 100.0 must set the scrolling location of the control to the equivalent of its rightmost position for languages such as English that read left to right. Alternately, for languages such as Arabic that read right to left, setting HorizontalScrollPercent = 100.0 must set the scroll location to the leftmost position.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Required Members for IScrollProvider  
 The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
|Required member|Member type|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Metoda|Žádné|  
  
 This control pattern has no associated events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Exception Type|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> throws this exception if a control supports <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> values exclusively for horizontal or vertical scrolling, but a <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> value is passed in.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throws this exception when a value that cannot be converted to a double is passed in.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throws this exception when a value greater than 100 or less than 0 is passed in (except -1 which is equivalent to <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Both <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> and <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throw this exception when an attempt is made to scroll in an unsupported direction.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
