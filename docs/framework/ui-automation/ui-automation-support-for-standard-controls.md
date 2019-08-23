---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914235"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="e61db-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="e61db-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="e61db-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e61db-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e61db-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e61db-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e61db-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře standardních ovládacích prvků v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]rozhraní [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e61db-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="e61db-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="e61db-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="e61db-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky ovládacích prvků, které poskytují informace nebo podporu pro interakci s uživatelem, mají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]úplnou nativní podporu pro.</span><span class="sxs-lookup"><span data-stu-id="e61db-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="e61db-108">Jiné prvky, například panely, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e61db-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="e61db-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="e61db-109">Win32 Controls</span></span>  
 <span data-ttu-id="e61db-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků je vystavena prostřednictvím poskytovatelů na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="e61db-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="e61db-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e61db-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="e61db-112">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 Comctrl32. dll ( [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] k dispozici v a novějších verzích).</span><span class="sxs-lookup"><span data-stu-id="e61db-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="e61db-113">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e61db-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="e61db-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="e61db-114">Class name</span></span>|<span data-ttu-id="e61db-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e61db-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="e61db-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-116">Button</span></span>|<span data-ttu-id="e61db-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-117">Button</span></span>|  
|<span data-ttu-id="e61db-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-118">Button</span></span>|<span data-ttu-id="e61db-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e61db-119">RadioButton</span></span>|  
|<span data-ttu-id="e61db-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-120">Button</span></span>|<span data-ttu-id="e61db-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="e61db-121">Group</span></span>|  
|<span data-ttu-id="e61db-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-122">Button</span></span>|<span data-ttu-id="e61db-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="e61db-123">CheckBox</span></span>|  
|<span data-ttu-id="e61db-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-124">Button</span></span>|<span data-ttu-id="e61db-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="e61db-125">Hyperlink</span></span>|  
|<span data-ttu-id="e61db-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-126">Button</span></span>|<span data-ttu-id="e61db-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="e61db-127">SplitButton</span></span>|  
|<span data-ttu-id="e61db-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-128">Button</span></span>|<span data-ttu-id="e61db-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="e61db-129">CheckBox</span></span>|  
|<span data-ttu-id="e61db-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="e61db-130">ComboBoxEx32</span></span>|<span data-ttu-id="e61db-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="e61db-131">ComboBox</span></span>|  
|<span data-ttu-id="e61db-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="e61db-132">ComboBox</span></span>|<span data-ttu-id="e61db-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="e61db-133">ComboBox</span></span>|  
|<span data-ttu-id="e61db-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="e61db-134">Edit</span></span>|<span data-ttu-id="e61db-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="e61db-135">Document</span></span>|  
|<span data-ttu-id="e61db-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="e61db-136">Edit</span></span>|<span data-ttu-id="e61db-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="e61db-137">Edit</span></span>|  
|<span data-ttu-id="e61db-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="e61db-138">SysLink</span></span>|<span data-ttu-id="e61db-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="e61db-139">Hyperlink</span></span>|  
|<span data-ttu-id="e61db-140">Static</span><span class="sxs-lookup"><span data-stu-id="e61db-140">Static</span></span>|<span data-ttu-id="e61db-141">Text</span><span class="sxs-lookup"><span data-stu-id="e61db-141">Text</span></span>|  
|<span data-ttu-id="e61db-142">Static</span><span class="sxs-lookup"><span data-stu-id="e61db-142">Static</span></span>|<span data-ttu-id="e61db-143">Image</span><span class="sxs-lookup"><span data-stu-id="e61db-143">Image</span></span>|  
|<span data-ttu-id="e61db-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="e61db-144">SysIPAddress32</span></span>|<span data-ttu-id="e61db-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="e61db-145">Custom</span></span>|  
|<span data-ttu-id="e61db-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="e61db-146">SysHeader32</span></span>|<span data-ttu-id="e61db-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="e61db-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="e61db-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="e61db-148">SysListView32</span></span>|<span data-ttu-id="e61db-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="e61db-149">DataGrid</span></span>|  
|<span data-ttu-id="e61db-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="e61db-150">SysListView32</span></span>|<span data-ttu-id="e61db-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="e61db-151">List</span></span>|  
|<span data-ttu-id="e61db-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="e61db-152">ListBox</span></span>|<span data-ttu-id="e61db-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="e61db-153">List</span></span>|  
|<span data-ttu-id="e61db-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="e61db-154">ListBox</span></span>|<span data-ttu-id="e61db-155">Collection</span><span class="sxs-lookup"><span data-stu-id="e61db-155">ListItem</span></span>|  
|<span data-ttu-id="e61db-156">#32768</span><span class="sxs-lookup"><span data-stu-id="e61db-156">#32768</span></span>|<span data-ttu-id="e61db-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="e61db-157">Menu</span></span>|  
|<span data-ttu-id="e61db-158">#32768</span><span class="sxs-lookup"><span data-stu-id="e61db-158">#32768</span></span>|<span data-ttu-id="e61db-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="e61db-159">MenuItem</span></span>|  
|<span data-ttu-id="e61db-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="e61db-160">msctls_progress32</span></span>|<span data-ttu-id="e61db-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="e61db-161">ProgressBar</span></span>|  
|<span data-ttu-id="e61db-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="e61db-162">RichEdit</span></span>|<span data-ttu-id="e61db-163">Dokumentů.</span><span class="sxs-lookup"><span data-stu-id="e61db-163">Document.</span></span> <span data-ttu-id="e61db-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="e61db-164">See note.</span></span>|  
|<span data-ttu-id="e61db-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="e61db-165">RichEdit20A</span></span>|<span data-ttu-id="e61db-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="e61db-166">Document</span></span>|  
|<span data-ttu-id="e61db-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="e61db-167">RichEdit20W</span></span>|<span data-ttu-id="e61db-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="e61db-168">Document</span></span>|  
|<span data-ttu-id="e61db-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="e61db-169">RichEdit50W</span></span>|<span data-ttu-id="e61db-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="e61db-170">Document</span></span>|  
|<span data-ttu-id="e61db-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e61db-171">ScrollBar</span></span>|<span data-ttu-id="e61db-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="e61db-172">Slider</span></span>|  
|<span data-ttu-id="e61db-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="e61db-173">msctls_trackbar32</span></span>|<span data-ttu-id="e61db-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="e61db-174">Slider</span></span>|  
|<span data-ttu-id="e61db-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="e61db-175">msctls_updown32</span></span>|<span data-ttu-id="e61db-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="e61db-176">Spinner</span></span>|  
|<span data-ttu-id="e61db-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="e61db-177">msctls_statusbar32</span></span>|<span data-ttu-id="e61db-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="e61db-178">StatusBar</span></span>|  
|<span data-ttu-id="e61db-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="e61db-179">SysTabControl32</span></span>|<span data-ttu-id="e61db-180">Karta</span><span class="sxs-lookup"><span data-stu-id="e61db-180">Tab</span></span>|  
|<span data-ttu-id="e61db-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="e61db-181">SysTabControl32</span></span>|<span data-ttu-id="e61db-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="e61db-182">TabItem</span></span>|  
|<span data-ttu-id="e61db-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-183">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="e61db-184">ToolBar</span></span>|  
|<span data-ttu-id="e61db-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-185">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="e61db-186">MenuItem</span></span>|  
|<span data-ttu-id="e61db-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-187">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-188">Button</span></span>|  
|<span data-ttu-id="e61db-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-189">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="e61db-190">CheckBox</span></span>|  
|<span data-ttu-id="e61db-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-191">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e61db-192">RadioButton</span></span>|  
|<span data-ttu-id="e61db-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-193">ToolbarWindow32</span></span>|<span data-ttu-id="e61db-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="e61db-194">Separator</span></span>|  
|<span data-ttu-id="e61db-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="e61db-195">tooltips_class32</span></span>|<span data-ttu-id="e61db-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="e61db-196">ToolTip</span></span>|  
|<span data-ttu-id="e61db-197">#32774</span><span class="sxs-lookup"><span data-stu-id="e61db-197">#32774</span></span>|<span data-ttu-id="e61db-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="e61db-198">ToolTip</span></span>|  
|<span data-ttu-id="e61db-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="e61db-199">ReBarWindow32</span></span>|<span data-ttu-id="e61db-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="e61db-200">Toolbar</span></span>|  
|<span data-ttu-id="e61db-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="e61db-201">SysTreeView32</span></span>|<span data-ttu-id="e61db-202">Strom</span><span class="sxs-lookup"><span data-stu-id="e61db-202">Tree</span></span>|  
|<span data-ttu-id="e61db-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="e61db-203">SysTreeView32</span></span>|<span data-ttu-id="e61db-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="e61db-204">TreeItem</span></span>|  
  
 <span data-ttu-id="e61db-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] systémem (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="e61db-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="e61db-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="e61db-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="e61db-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="e61db-207">Class name</span></span>|<span data-ttu-id="e61db-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e61db-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="e61db-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="e61db-209">SysAnimate32</span></span>|<span data-ttu-id="e61db-210">Image</span><span class="sxs-lookup"><span data-stu-id="e61db-210">Image</span></span>|  
|<span data-ttu-id="e61db-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="e61db-211">SysPager</span></span>|<span data-ttu-id="e61db-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="e61db-212">Spinner</span></span>|  
|<span data-ttu-id="e61db-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="e61db-213">SysDateTimePick32</span></span>|<span data-ttu-id="e61db-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="e61db-214">Custom</span></span>|  
|<span data-ttu-id="e61db-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="e61db-215">SysMonthCal32</span></span>|<span data-ttu-id="e61db-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="e61db-216">Calendar</span></span>|  
|<span data-ttu-id="e61db-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="e61db-217">MS_WINNOTE</span></span>|<span data-ttu-id="e61db-218">Okna</span><span class="sxs-lookup"><span data-stu-id="e61db-218">Tooltip</span></span>|  
|<span data-ttu-id="e61db-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="e61db-219">VBBubble</span></span>|<span data-ttu-id="e61db-220">Okna</span><span class="sxs-lookup"><span data-stu-id="e61db-220">Tooltip</span></span>|  
|<span data-ttu-id="e61db-221">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="e61db-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="e61db-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="e61db-222">Slider</span></span>|  
|<span data-ttu-id="e61db-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="e61db-223">SuperGrid</span></span>|<span data-ttu-id="e61db-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="e61db-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="e61db-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e61db-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="e61db-226">Ovládací prvky model Windows Forms jsou zpřístupněny prostřednictvím poskytovatelů na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="e61db-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="e61db-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e61db-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="e61db-228">Obvykle jsou model Windows Forms ovládací prvky, které jsou spravované obálky [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] pro běžné ovládací prvky, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporovány nástrojem.</span><span class="sxs-lookup"><span data-stu-id="e61db-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="e61db-229">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e61db-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="e61db-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="e61db-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="e61db-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="e61db-231">Button</span></span>|  
|<span data-ttu-id="e61db-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="e61db-232">CheckBox</span></span>|  
|<span data-ttu-id="e61db-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="e61db-233">CheckedListBox</span></span>|  
|<span data-ttu-id="e61db-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-234">ColorDialog</span></span>|  
|<span data-ttu-id="e61db-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="e61db-235">ComboBox</span></span>|  
|<span data-ttu-id="e61db-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="e61db-236">FolderBrowser</span></span>|  
|<span data-ttu-id="e61db-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-237">FontDialog</span></span>|  
|<span data-ttu-id="e61db-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="e61db-238">GroupBox</span></span>|  
|<span data-ttu-id="e61db-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="e61db-239">HscrollBar</span></span>|  
|<span data-ttu-id="e61db-240">Obrázků</span><span class="sxs-lookup"><span data-stu-id="e61db-240">ImageList</span></span>|  
|<span data-ttu-id="e61db-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="e61db-241">Label</span></span>|  
|<span data-ttu-id="e61db-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="e61db-242">ListBox</span></span>|  
|<span data-ttu-id="e61db-243">ListView</span><span class="sxs-lookup"><span data-stu-id="e61db-243">ListView</span></span>|  
|<span data-ttu-id="e61db-244">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="e61db-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="e61db-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="e61db-245">MonthCalendar</span></span>|  
|<span data-ttu-id="e61db-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="e61db-246">NotifyIcon</span></span>|  
|<span data-ttu-id="e61db-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="e61db-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="e61db-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-249">PrintDialog</span></span>|  
|<span data-ttu-id="e61db-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="e61db-250">ProgressBar</span></span>|  
|<span data-ttu-id="e61db-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e61db-251">RadioButton</span></span>|  
|<span data-ttu-id="e61db-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="e61db-252">RichTextBox</span></span>|  
|<span data-ttu-id="e61db-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e61db-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="e61db-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="e61db-254">ScrollableControl</span></span>|  
|<span data-ttu-id="e61db-255">Komponentu</span><span class="sxs-lookup"><span data-stu-id="e61db-255">SoundPlayer</span></span>|  
|<span data-ttu-id="e61db-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="e61db-256">StatusBar</span></span>|  
|<span data-ttu-id="e61db-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="e61db-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="e61db-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="e61db-258">TextBox</span></span>|  
|<span data-ttu-id="e61db-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="e61db-259">Timer</span></span>|  
|<span data-ttu-id="e61db-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="e61db-260">Toolbar</span></span>|  
|<span data-ttu-id="e61db-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="e61db-261">ToolTip</span></span>|  
|<span data-ttu-id="e61db-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="e61db-262">TrackBar</span></span>|  
|<span data-ttu-id="e61db-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="e61db-263">TreeView</span></span>|  
|<span data-ttu-id="e61db-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="e61db-264">VscrollBar</span></span>|  
|<span data-ttu-id="e61db-265">Navig</span><span class="sxs-lookup"><span data-stu-id="e61db-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="e61db-266">Následující ovládací prvky jsou k [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dispozici pouze prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="e61db-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="e61db-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e61db-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="e61db-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e61db-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="e61db-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="e61db-269">BindingSource</span></span>|  
|<span data-ttu-id="e61db-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="e61db-270">DataGrid</span></span>|  
|<span data-ttu-id="e61db-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="e61db-271">DataGridView</span></span>|  
|<span data-ttu-id="e61db-272">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="e61db-272">DataNavigator</span></span>|  
|<span data-ttu-id="e61db-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="e61db-273">DomainUpDown</span></span>|  
|<span data-ttu-id="e61db-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="e61db-274">ErrorProvider</span></span>|  
|<span data-ttu-id="e61db-275">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="e61db-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="e61db-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="e61db-276">Form</span></span>|  
|<span data-ttu-id="e61db-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="e61db-277">LinkLabel</span></span>|  
|<span data-ttu-id="e61db-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="e61db-278">HelpProvider</span></span>|  
|<span data-ttu-id="e61db-279">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="e61db-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="e61db-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e61db-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="e61db-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="e61db-281">NumericUpDown</span></span>|  
|<span data-ttu-id="e61db-282">Panel</span><span class="sxs-lookup"><span data-stu-id="e61db-282">Panel</span></span>|  
|<span data-ttu-id="e61db-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="e61db-283">PictureBox</span></span>|  
|<span data-ttu-id="e61db-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="e61db-284">PrintDocument</span></span>|  
|<span data-ttu-id="e61db-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="e61db-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="e61db-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="e61db-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="e61db-287">Mřížky</span><span class="sxs-lookup"><span data-stu-id="e61db-287">PropertyGrid</span></span>|  
|<span data-ttu-id="e61db-288">Type</span><span class="sxs-lookup"><span data-stu-id="e61db-288">UserControl</span></span>|  
|<span data-ttu-id="e61db-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e61db-289">ToolStrip</span></span>|  
|<span data-ttu-id="e61db-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e61db-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="e61db-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="e61db-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="e61db-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="e61db-292">Splitter</span></span>|  
|<span data-ttu-id="e61db-293">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="e61db-293">RaftingContainer</span></span>|  
|<span data-ttu-id="e61db-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="e61db-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e61db-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e61db-295">See also</span></span>

- [<span data-ttu-id="e61db-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e61db-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
