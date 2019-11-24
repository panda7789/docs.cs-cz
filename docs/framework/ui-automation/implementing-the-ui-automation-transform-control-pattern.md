---
title: Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: c0a46580ad2673b56fefe7228f2549a2e19d2c14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447055"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Transform control pattern, note the following guidelines and conventions:  
  
- Support for this control pattern is not limited to objects on the desktop. This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.  
  
- An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport). In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.  
  
- For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.  
  
- All parameters and property values are absolute and independent of locale.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Required Members for ITransformProvider  
 The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Required members|Member type|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Žádné|  
  
 This control pattern has no associated events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Exception Type|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
