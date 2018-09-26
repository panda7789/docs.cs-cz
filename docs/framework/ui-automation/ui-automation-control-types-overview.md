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
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="a8c79-102">Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8c79-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="a8c79-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a8c79-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a8c79-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a8c79-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="a8c79-105"> typy ovládacích prvků jsou dobře známé identifikátory, které slouží k označení, jaký druh ovládacího prvku představuje určitý element, jako je například pole se seznamem nebo tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a8c79-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="a8c79-106">S dobře známý identifikátor usnadňuje technologie pro usnadnění zařízení k určení, jaké typy ovládacích prvků jsou k dispozici v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a způsob práce s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="a8c79-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="a8c79-107">Požadavky typ ovládacího prvku automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8c79-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="a8c79-108"> typy ovládacích prvků obsahují sadu podmínek, které musí splnit poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="a8c79-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="a8c79-109">Při splnění těchto podmínek, můžete ovládací prvek používat název konkrétní ovládací prvek typu.</span><span class="sxs-lookup"><span data-stu-id="a8c79-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="a8c79-110">Každý typ ovládacího prvku má následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="a8c79-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a8c79-111"> ovládací prvek vzorů, které vzorů ovládacích prvků musí podporovat, který ovládací prvek vzorce jsou volitelné a které vzorů ovládacích prvků nesmí být podporována ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a8c79-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a8c79-112"> hodnoty vlastností – hodnot vlastností, které jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a8c79-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a8c79-113"> stromová struktura – požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a8c79-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="a8c79-114">Pokud ovládací prvek splňuje podmínky pro konkrétní ovládací prvek typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> hodnota vlastnosti označí tento ovládací prvek typu.</span><span class="sxs-lookup"><span data-stu-id="a8c79-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="a8c79-115">Aktuální typy ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8c79-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="a8c79-116">Následující seznam obsahuje aktuální sadu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řídit typy:</span><span class="sxs-lookup"><span data-stu-id="a8c79-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="a8c79-117">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko</span><span class="sxs-lookup"><span data-stu-id="a8c79-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="a8c79-118">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář</span><span class="sxs-lookup"><span data-stu-id="a8c79-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-119">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="a8c79-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="a8c79-120">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="a8c79-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="a8c79-121">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="a8c79-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="a8c79-122">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-123">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument</span><span class="sxs-lookup"><span data-stu-id="a8c79-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="a8c79-124">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav</span><span class="sxs-lookup"><span data-stu-id="a8c79-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="a8c79-125">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku skupina</span><span class="sxs-lookup"><span data-stu-id="a8c79-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="a8c79-126">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku záhlaví</span><span class="sxs-lookup"><span data-stu-id="a8c79-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="a8c79-127">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-128">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="a8c79-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="a8c79-129">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek</span><span class="sxs-lookup"><span data-stu-id="a8c79-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="a8c79-130">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam</span><span class="sxs-lookup"><span data-stu-id="a8c79-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="a8c79-131">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-132">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku nabídka</span><span class="sxs-lookup"><span data-stu-id="a8c79-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="a8c79-133">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-134">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-135">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno</span><span class="sxs-lookup"><span data-stu-id="a8c79-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="a8c79-136">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-137">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="a8c79-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="a8c79-138">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-139">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku oddělovač</span><span class="sxs-lookup"><span data-stu-id="a8c79-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="a8c79-140">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník</span><span class="sxs-lookup"><span data-stu-id="a8c79-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="a8c79-141">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník</span><span class="sxs-lookup"><span data-stu-id="a8c79-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="a8c79-142">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton</span><span class="sxs-lookup"><span data-stu-id="a8c79-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="a8c79-143">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-144">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta</span><span class="sxs-lookup"><span data-stu-id="a8c79-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="a8c79-145">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TabItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-146">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tabulka</span><span class="sxs-lookup"><span data-stu-id="a8c79-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="a8c79-147">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku text</span><span class="sxs-lookup"><span data-stu-id="a8c79-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="a8c79-148">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku jezdec</span><span class="sxs-lookup"><span data-stu-id="a8c79-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="a8c79-149">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-150">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="a8c79-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="a8c79-151">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip</span><span class="sxs-lookup"><span data-stu-id="a8c79-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="a8c79-152">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku strom</span><span class="sxs-lookup"><span data-stu-id="a8c79-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="a8c79-153">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem</span><span class="sxs-lookup"><span data-stu-id="a8c79-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="a8c79-154">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku okno</span><span class="sxs-lookup"><span data-stu-id="a8c79-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8c79-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8c79-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
