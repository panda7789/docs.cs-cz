---
title: Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 643c89e8f6c5e34aa1fb3c5c7c6c750c72046277
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179938"
---
# <a name="ui-automation-control-types-overview"></a>Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy ovládacích prvků jsou dobře známé identifikátory, které lze použít k označení, jaký druh ovládacího prvku představuje určitý prvek, například pole se seznamem nebo tlačítko.  
  
 S dobře známý identifikátor usnadňuje asistenční technologie zařízení k určení, jaké typy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ovládacích prvků jsou k dispozici v a jak pracovat s ovládacími prvky.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a>Požadavky typu automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy ovládacích prvku poskytují sadu podmínek, které musí poskytovatelé splňovat. Pokud jsou splněny tyto podmínky, ovládací prvek můžete použít konkrétní název typu ovládacího prvku. Každý typ ovládacího prvku má podmínky pro následující:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ovládací vzorky – které řídicí vzorky musí být podporovány, které řídicí vzorky jsou volitelné a které řídicí vzorky nesmí být ovládacím prvkem podporovány.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hodnoty vlastností – které hodnoty vlastností jsou podporovány.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]stromová struktura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – požadovaná stromová struktura pro ovládací prvek.  
  
 Pokud ovládací prvek splňuje podmínky pro určitý <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> typ ovládacího prvku, hodnota vlastnosti bude označovat tento typ ovládacího prvku.  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a>Aktuální typy ovládacích prvku automatizace uživatelského rozhraní  
 Následující seznam obsahuje aktuální [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sadu typů ovládacích prvku:  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko](ui-automation-support-for-the-button-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument](ui-automation-support-for-the-document-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav](ui-automation-support-for-the-edit-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku skupina](ui-automation-support-for-the-group-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku záhlaví](ui-automation-support-for-the-header-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku hypertextový odkaz](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek](ui-automation-support-for-the-image-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam](ui-automation-support-for-the-list-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku nabídka](ui-automation-support-for-the-menu-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno](ui-automation-support-for-the-pane-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku oddělovač](ui-automation-support-for-the-separator-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník](ui-automation-support-for-the-slider-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta](ui-automation-support-for-the-tab-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tabulka](ui-automation-support-for-the-table-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku text](ui-automation-support-for-the-text-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku jezdec](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku strom](ui-automation-support-for-the-tree-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku okno](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType>
