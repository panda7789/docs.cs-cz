---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 1e33a64e66bc084e8cc5f75ece2ac2a4d7ea85aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447135"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>. This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Scroll Item control pattern, note the following guidelines and conventions:  
  
- Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface. As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Required Members for IScrollItemProvider  
 The following method is required for implementing the IScrollProvider interface.  
  
|Required members|Member type|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-   Method|Žádné|  
  
 This control pattern has no associated properties or events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Providers must throw the following exceptions.  
  
|Exception Type|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|If an item cannot be scrolled into view:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
