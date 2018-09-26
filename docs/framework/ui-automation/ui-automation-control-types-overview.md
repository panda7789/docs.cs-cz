---
title: Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: f59549d83e5662f236a44f112b473b2d233f4669
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073696"
---
# <a name="ui-automation-control-types-overview"></a>Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy ovládacích prvků jsou dobře známé identifikátory, které slouží k označení, jaký druh ovládacího prvku představuje určitý element, jako je například pole se seznamem nebo tlačítko.  
  
 S dobře známý identifikátor usnadňuje technologie pro usnadnění zařízení k určení, jaké typy ovládacích prvků jsou k dispozici v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a způsob práce s ovládacími prvky.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Požadavky typ ovládacího prvku automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy ovládacích prvků obsahují sadu podmínek, které musí splnit poskytovatelů. Při splnění těchto podmínek, můžete ovládací prvek používat název konkrétní ovládací prvek typu. Každý typ ovládacího prvku má následující podmínky:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládací prvek vzorů, které vzorů ovládacích prvků musí podporovat, který ovládací prvek vzorce jsou volitelné a které vzorů ovládacích prvků nesmí být podporována ovládacím prvku.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností – hodnot vlastností, které jsou podporovány.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura – požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura pro ovládací prvek.  
  
 Pokud ovládací prvek splňuje podmínky pro konkrétní ovládací prvek typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> hodnota vlastnosti označí tento ovládací prvek typu.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Aktuální typy ovládacích prvků automatizace uživatelského rozhraní  
 Následující seznam obsahuje aktuální sadu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řídit typy:  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku skupina](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku záhlaví](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku hypertextový odkaz](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku nabídka](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku oddělovač](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tabulka](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku text](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku jezdec](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku strom](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku okno](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType>
