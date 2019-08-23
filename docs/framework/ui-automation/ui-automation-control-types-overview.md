---
title: Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911562"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="7e6c8-102">Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e6c8-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="7e6c8-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7e6c8-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="7e6c8-105">typy ovládacích prvků jsou známé identifikátory, které lze použít k určení toho, jaký typ ovládacího prvku konkrétní element představuje, například pole se seznamem nebo tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="7e6c8-106">Má-li dobře známý identifikátor, je snazší pro zařízení s podporou technologie, aby určila, jaké typy ovládacích prvků jsou [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] k dispozici v nástroji a jak pracovat s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="7e6c8-107">Požadavky typu ovládacího prvku automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e6c8-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="7e6c8-108">typy ovládacích prvků poskytují sadu podmínek, které musí poskytovatelé splňovat.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="7e6c8-109">Pokud jsou splněny tyto podmínky, může ovládací prvek použít název konkrétního typu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="7e6c8-110">Každý typ ovládacího prvku má podmínky pro následující:</span><span class="sxs-lookup"><span data-stu-id="7e6c8-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="7e6c8-111">vzory ovládacích prvků – které řídicí vzory musí být podporovány, které vzory ovládacích prvků jsou volitelné a které řídicí vzory nesmí být podporovány ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="7e6c8-112">hodnoty vlastností – které hodnoty vlastností jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="7e6c8-113">Stromová struktura – požadovaná [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="7e6c8-114">Když ovládací prvek splňuje podmínky pro určitý typ ovládacího prvku, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> hodnota vlastnosti bude označovat, že typ ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e6c8-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="7e6c8-115">Aktuální typy ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e6c8-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="7e6c8-116">Následující seznam obsahuje aktuální sadu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typů ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="7e6c8-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="7e6c8-117">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko</span><span class="sxs-lookup"><span data-stu-id="7e6c8-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="7e6c8-118">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář</span><span class="sxs-lookup"><span data-stu-id="7e6c8-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-119">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="7e6c8-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="7e6c8-120">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="7e6c8-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="7e6c8-121">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="7e6c8-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="7e6c8-122">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-123">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument</span><span class="sxs-lookup"><span data-stu-id="7e6c8-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="7e6c8-124">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav</span><span class="sxs-lookup"><span data-stu-id="7e6c8-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="7e6c8-125">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku skupina</span><span class="sxs-lookup"><span data-stu-id="7e6c8-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="7e6c8-126">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku záhlaví</span><span class="sxs-lookup"><span data-stu-id="7e6c8-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="7e6c8-127">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-128">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="7e6c8-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="7e6c8-129">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek</span><span class="sxs-lookup"><span data-stu-id="7e6c8-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="7e6c8-130">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam</span><span class="sxs-lookup"><span data-stu-id="7e6c8-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="7e6c8-131">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-132">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku nabídka</span><span class="sxs-lookup"><span data-stu-id="7e6c8-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="7e6c8-133">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-134">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-135">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno</span><span class="sxs-lookup"><span data-stu-id="7e6c8-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="7e6c8-136">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ProgressBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-137">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="7e6c8-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="7e6c8-138">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-139">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku oddělovač</span><span class="sxs-lookup"><span data-stu-id="7e6c8-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="7e6c8-140">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník</span><span class="sxs-lookup"><span data-stu-id="7e6c8-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="7e6c8-141">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník</span><span class="sxs-lookup"><span data-stu-id="7e6c8-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="7e6c8-142">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton</span><span class="sxs-lookup"><span data-stu-id="7e6c8-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="7e6c8-143">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-144">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta</span><span class="sxs-lookup"><span data-stu-id="7e6c8-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="7e6c8-145">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TabItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-146">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tabulka</span><span class="sxs-lookup"><span data-stu-id="7e6c8-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="7e6c8-147">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku text</span><span class="sxs-lookup"><span data-stu-id="7e6c8-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="7e6c8-148">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku jezdec</span><span class="sxs-lookup"><span data-stu-id="7e6c8-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="7e6c8-149">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-150">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="7e6c8-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="7e6c8-151">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip</span><span class="sxs-lookup"><span data-stu-id="7e6c8-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="7e6c8-152">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku strom</span><span class="sxs-lookup"><span data-stu-id="7e6c8-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="7e6c8-153">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem</span><span class="sxs-lookup"><span data-stu-id="7e6c8-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="7e6c8-154">Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku okno</span><span class="sxs-lookup"><span data-stu-id="7e6c8-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e6c8-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e6c8-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
