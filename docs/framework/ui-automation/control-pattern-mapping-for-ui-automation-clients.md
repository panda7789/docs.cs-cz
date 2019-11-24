---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433869"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic lists control types and their associated control patterns.  
  
 The following table organizes the control patterns into the following categories:  
  
- Supported. The control must support this control pattern.  
  
- Conditional support. The control may support this control pattern depending on the state of the control.  
  
- Není podporováno. The control does not support this control pattern; custom controls may support this control pattern.  
  
> [!NOTE]
> Some controls have conditional support for several control patterns depending on the functionality of the control. For example, the menu item control has conditional support for the <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, or <xref:System.Windows.Automation.SelectionItemPattern> control pattern, depending on its function in the menu control.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|Control Type|Podporováno|Conditional Support|Nepodporováno|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádné|Invoke, Toggle, Expand Collapse|Žádné|  
|Kalendář|Grid, Table|Selection, Scroll|Hodnota|  
|Check Box|Přepnout|Žádné|Žádné|  
|Pole se seznamem|Expand Collapse|Selection, Value|Posuv|  
|Datová mřížka|Mřížka|Scroll, Selection, Table|Žádné|  
|Datová položka|Položka výběru|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|Žádné|  
|Dokument|Text|Scroll, Value|Žádné|  
|Upravit|Žádné|Text, Range Value, Value|Žádné|  
|Skupina|Žádné|Expand Collapse|Žádné|  
|Záhlaví|Žádné|Transformace|Žádné|  
|Položka hlavičky|Žádné|Transform, Invoke|Žádné|  
|Hypertextový odkaz|Vyvolat|Hodnota|Žádné|  
|Image|Žádné|Grid Item, Table Item|Invoke, Selection Item|  
|Seznam|Žádné|Grid, Multiple View, Scroll, Selection|Tabulka|  
|List Item|Položka výběru|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|Žádné|  
|Nabídka|Žádné|Žádné|Žádné|  
|Řádek nabídek|Žádné|Expand Collapse, Dock, Transform|Žádné|  
|Položka nabídky|Žádné|Expand Collapse, Invoke, Selection Item, Toggle|Žádné|  
|Podokno|Žádné|Dock. Scroll, Transform|Okno|  
|Indikátor průběhu|Žádné|Range Value, Value|Žádné|  
|Přepínač|Položka výběru|Žádné|Přepnout|  
|Posuvník|Žádné|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádné|Žádné|Žádné|  
|Posuvník|Žádné|Range Value, Selection, Value|Žádné|  
|Číselník|Žádné|Range Value, Selection, Value|Žádné|  
|Tlačítko rozdělení|Invoke, Expand Collapse|Žádné|Žádné|  
|Stavový řádek|Žádné|Mřížka|Žádné|  
|Karta|Výběr|Posuv|Žádné|  
|Položka tabulátoru|Položka výběru|Žádné|Vyvolat|  
|Tabulka|Grid, Grid Item, Table, Table Item|Žádné|Žádné|  
|Text|Žádné|Grid Item, Table Item, Text|Hodnota|  
|Jezdec|Transformace|Žádné|Žádné|  
|Záhlaví|Žádné|Žádné|Žádné|  
|Tool Bar|Žádné|Dock, Expand Collapse, Transform|Žádné|  
|Tool Tip|Žádné|Text, Window|Žádné|  
|Strom|Žádné|Scroll, Selection|Žádné|  
|Položka stromu|Expand Collapse|Invoke, Scroll Item, Selection Item, Toggle|Žádné|  
|Okno|Transform, Window|Dock|Žádné|  
  
> [!NOTE]
> If a control type has no supported control patterns listed but has one or more conditionally-supported control patterns, then one of those conditional control patterns will be supported at all times.  
  
## <a name="see-also"></a>Viz také:

- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
