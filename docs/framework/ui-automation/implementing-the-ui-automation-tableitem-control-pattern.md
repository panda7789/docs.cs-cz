---
title: Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 4374666ba5e03720413614c63b00ba987f81f58f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447078"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties. Links to additional references are listed at the end of the overview.  
  
 The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>. Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>. This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
  
- For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Required Members for ITableItemProvider  
  
|Required member|Member type|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Metoda|Žádné|  
  
 This control pattern has no associated properties or events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 This control pattern has no associated exceptions.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-table-control-pattern.md)
- [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
