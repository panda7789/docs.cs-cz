---
title: Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c8ca0934e724c4035fb24b9cb246b0b2f41eea3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399727"
---
# <a name="ui-automation-control-types-overview"></a>Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy ovládacích prvků jsou známé identifikátory, které slouží k označení, jaký druh řízení představuje určitý element, jako je například pole se seznamem nebo tlačítko.  
  
 S známý identifikátor usnadňuje pomocných zařízení k určení, které typy ovládacích prvků, které jsou k dispozici v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a návod, jak pracovat s ovládacími prvky.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Požadavky typ ovládacího prvku automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy ovládacích prvků poskytují sadu podmínek, které musí splňovat zprostředkovatele. Pokud tyto podmínky jsou splněny, můžete použít ovládací prvek název konkrétní ovládací prvek typu. Každý typ ovládacího prvku má podmínek pro následující:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory – musí být podporována které vzory ovládacích prvků, které řízení vzory jsou volitelné a které vzory ovládacích prvků nesmí být podporována ovládacího prvku.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností – hodnot vlastností, které jsou podporovány.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury – požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury pro ovládací prvek.  
  
 Pokud ovládací prvek splňuje podmínky pro konkrétní ovládací prvek typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> hodnota vlastnosti označí tuto kontrolu typu.  
  
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
