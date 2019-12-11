---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 314526c1164f70e6b261df1a6f11ddce2b5fa240
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960079"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="613a0-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="613a0-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="613a0-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="613a0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="613a0-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="613a0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="613a0-105">Toto téma obsahuje informace o podpoře [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro standardní ovládací prvky v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.</span><span class="sxs-lookup"><span data-stu-id="613a0-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="613a0-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="613a0-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="613a0-107">Všechny prvky ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="613a0-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="613a0-108">Jiné prvky, například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="613a0-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="613a0-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="613a0-109">Win32 Controls</span></span>  
 <span data-ttu-id="613a0-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]ch ovládacích prvků je k dispozici [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="613a0-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="613a0-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="613a0-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="613a0-112">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 souboru *Comctrl32. dll*.</span><span class="sxs-lookup"><span data-stu-id="613a0-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="613a0-113">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="613a0-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="613a0-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="613a0-114">Class name</span></span>|<span data-ttu-id="613a0-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="613a0-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="613a0-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-116">Button</span></span>|<span data-ttu-id="613a0-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-117">Button</span></span>|  
|<span data-ttu-id="613a0-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-118">Button</span></span>|<span data-ttu-id="613a0-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="613a0-119">RadioButton</span></span>|  
|<span data-ttu-id="613a0-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-120">Button</span></span>|<span data-ttu-id="613a0-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="613a0-121">Group</span></span>|  
|<span data-ttu-id="613a0-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-122">Button</span></span>|<span data-ttu-id="613a0-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="613a0-123">CheckBox</span></span>|  
|<span data-ttu-id="613a0-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-124">Button</span></span>|<span data-ttu-id="613a0-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="613a0-125">Hyperlink</span></span>|  
|<span data-ttu-id="613a0-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-126">Button</span></span>|<span data-ttu-id="613a0-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="613a0-127">SplitButton</span></span>|  
|<span data-ttu-id="613a0-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-128">Button</span></span>|<span data-ttu-id="613a0-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="613a0-129">CheckBox</span></span>|  
|<span data-ttu-id="613a0-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="613a0-130">ComboBoxEx32</span></span>|<span data-ttu-id="613a0-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="613a0-131">ComboBox</span></span>|  
|<span data-ttu-id="613a0-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="613a0-132">ComboBox</span></span>|<span data-ttu-id="613a0-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="613a0-133">ComboBox</span></span>|  
|<span data-ttu-id="613a0-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="613a0-134">Edit</span></span>|<span data-ttu-id="613a0-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="613a0-135">Document</span></span>|  
|<span data-ttu-id="613a0-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="613a0-136">Edit</span></span>|<span data-ttu-id="613a0-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="613a0-137">Edit</span></span>|  
|<span data-ttu-id="613a0-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="613a0-138">SysLink</span></span>|<span data-ttu-id="613a0-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="613a0-139">Hyperlink</span></span>|  
|<span data-ttu-id="613a0-140">Statické</span><span class="sxs-lookup"><span data-stu-id="613a0-140">Static</span></span>|<span data-ttu-id="613a0-141">Text</span><span class="sxs-lookup"><span data-stu-id="613a0-141">Text</span></span>|  
|<span data-ttu-id="613a0-142">Statické</span><span class="sxs-lookup"><span data-stu-id="613a0-142">Static</span></span>|<span data-ttu-id="613a0-143">Obrázek</span><span class="sxs-lookup"><span data-stu-id="613a0-143">Image</span></span>|  
|<span data-ttu-id="613a0-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="613a0-144">SysIPAddress32</span></span>|<span data-ttu-id="613a0-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="613a0-145">Custom</span></span>|  
|<span data-ttu-id="613a0-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="613a0-146">SysHeader32</span></span>|<span data-ttu-id="613a0-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="613a0-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="613a0-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="613a0-148">SysListView32</span></span>|<span data-ttu-id="613a0-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="613a0-149">DataGrid</span></span>|  
|<span data-ttu-id="613a0-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="613a0-150">SysListView32</span></span>|<span data-ttu-id="613a0-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="613a0-151">List</span></span>|  
|<span data-ttu-id="613a0-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="613a0-152">ListBox</span></span>|<span data-ttu-id="613a0-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="613a0-153">List</span></span>|  
|<span data-ttu-id="613a0-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="613a0-154">ListBox</span></span>|<span data-ttu-id="613a0-155">Collection</span><span class="sxs-lookup"><span data-stu-id="613a0-155">ListItem</span></span>|  
|<span data-ttu-id="613a0-156">#32768</span><span class="sxs-lookup"><span data-stu-id="613a0-156">#32768</span></span>|<span data-ttu-id="613a0-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="613a0-157">Menu</span></span>|  
|<span data-ttu-id="613a0-158">#32768</span><span class="sxs-lookup"><span data-stu-id="613a0-158">#32768</span></span>|<span data-ttu-id="613a0-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="613a0-159">MenuItem</span></span>|  
|<span data-ttu-id="613a0-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="613a0-160">msctls_progress32</span></span>|<span data-ttu-id="613a0-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="613a0-161">ProgressBar</span></span>|  
|<span data-ttu-id="613a0-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="613a0-162">RichEdit</span></span>|<span data-ttu-id="613a0-163">Dokumentů.</span><span class="sxs-lookup"><span data-stu-id="613a0-163">Document.</span></span> <span data-ttu-id="613a0-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="613a0-164">See note.</span></span>|  
|<span data-ttu-id="613a0-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="613a0-165">RichEdit20A</span></span>|<span data-ttu-id="613a0-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="613a0-166">Document</span></span>|  
|<span data-ttu-id="613a0-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="613a0-167">RichEdit20W</span></span>|<span data-ttu-id="613a0-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="613a0-168">Document</span></span>|  
|<span data-ttu-id="613a0-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="613a0-169">RichEdit50W</span></span>|<span data-ttu-id="613a0-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="613a0-170">Document</span></span>|  
|<span data-ttu-id="613a0-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="613a0-171">ScrollBar</span></span>|<span data-ttu-id="613a0-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="613a0-172">Slider</span></span>|  
|<span data-ttu-id="613a0-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="613a0-173">msctls_trackbar32</span></span>|<span data-ttu-id="613a0-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="613a0-174">Slider</span></span>|  
|<span data-ttu-id="613a0-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="613a0-175">msctls_updown32</span></span>|<span data-ttu-id="613a0-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="613a0-176">Spinner</span></span>|  
|<span data-ttu-id="613a0-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="613a0-177">msctls_statusbar32</span></span>|<span data-ttu-id="613a0-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="613a0-178">StatusBar</span></span>|  
|<span data-ttu-id="613a0-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="613a0-179">SysTabControl32</span></span>|<span data-ttu-id="613a0-180">Karta</span><span class="sxs-lookup"><span data-stu-id="613a0-180">Tab</span></span>|  
|<span data-ttu-id="613a0-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="613a0-181">SysTabControl32</span></span>|<span data-ttu-id="613a0-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="613a0-182">TabItem</span></span>|  
|<span data-ttu-id="613a0-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-183">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="613a0-184">ToolBar</span></span>|  
|<span data-ttu-id="613a0-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-185">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="613a0-186">MenuItem</span></span>|  
|<span data-ttu-id="613a0-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-187">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-188">Button</span></span>|  
|<span data-ttu-id="613a0-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-189">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="613a0-190">CheckBox</span></span>|  
|<span data-ttu-id="613a0-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-191">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="613a0-192">RadioButton</span></span>|  
|<span data-ttu-id="613a0-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-193">ToolbarWindow32</span></span>|<span data-ttu-id="613a0-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="613a0-194">Separator</span></span>|  
|<span data-ttu-id="613a0-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="613a0-195">tooltips_class32</span></span>|<span data-ttu-id="613a0-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="613a0-196">ToolTip</span></span>|  
|<span data-ttu-id="613a0-197">#32774</span><span class="sxs-lookup"><span data-stu-id="613a0-197">#32774</span></span>|<span data-ttu-id="613a0-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="613a0-198">ToolTip</span></span>|  
|<span data-ttu-id="613a0-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="613a0-199">ReBarWindow32</span></span>|<span data-ttu-id="613a0-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="613a0-200">Toolbar</span></span>|  
|<span data-ttu-id="613a0-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="613a0-201">SysTreeView32</span></span>|<span data-ttu-id="613a0-202">Strom</span><span class="sxs-lookup"><span data-stu-id="613a0-202">Tree</span></span>|  
|<span data-ttu-id="613a0-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="613a0-203">SysTreeView32</span></span>|<span data-ttu-id="613a0-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="613a0-204">TreeItem</span></span>|  
  
 <span data-ttu-id="613a0-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="613a0-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="613a0-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="613a0-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="613a0-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="613a0-207">Class name</span></span>|<span data-ttu-id="613a0-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="613a0-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="613a0-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="613a0-209">SysAnimate32</span></span>|<span data-ttu-id="613a0-210">Obrázek</span><span class="sxs-lookup"><span data-stu-id="613a0-210">Image</span></span>|  
|<span data-ttu-id="613a0-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="613a0-211">SysPager</span></span>|<span data-ttu-id="613a0-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="613a0-212">Spinner</span></span>|  
|<span data-ttu-id="613a0-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="613a0-213">SysDateTimePick32</span></span>|<span data-ttu-id="613a0-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="613a0-214">Custom</span></span>|  
|<span data-ttu-id="613a0-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="613a0-215">SysMonthCal32</span></span>|<span data-ttu-id="613a0-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="613a0-216">Calendar</span></span>|  
|<span data-ttu-id="613a0-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="613a0-217">MS_WINNOTE</span></span>|<span data-ttu-id="613a0-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="613a0-218">Tooltip</span></span>|  
|<span data-ttu-id="613a0-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="613a0-219">VBBubble</span></span>|<span data-ttu-id="613a0-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="613a0-220">Tooltip</span></span>|  
|<span data-ttu-id="613a0-221">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="613a0-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="613a0-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="613a0-222">Slider</span></span>|  
|<span data-ttu-id="613a0-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="613a0-223">SuperGrid</span></span>|<span data-ttu-id="613a0-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="613a0-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="613a0-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="613a0-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="613a0-226">Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="613a0-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="613a0-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="613a0-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="613a0-228">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporuje obvykle model Windows Forms ovládací prvky, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="613a0-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="613a0-229">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="613a0-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="613a0-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="613a0-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="613a0-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="613a0-231">Button</span></span>|  
|<span data-ttu-id="613a0-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="613a0-232">CheckBox</span></span>|  
|<span data-ttu-id="613a0-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="613a0-233">CheckedListBox</span></span>|  
|<span data-ttu-id="613a0-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-234">ColorDialog</span></span>|  
|<span data-ttu-id="613a0-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="613a0-235">ComboBox</span></span>|  
|<span data-ttu-id="613a0-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="613a0-236">FolderBrowser</span></span>|  
|<span data-ttu-id="613a0-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-237">FontDialog</span></span>|  
|<span data-ttu-id="613a0-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="613a0-238">GroupBox</span></span>|  
|<span data-ttu-id="613a0-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="613a0-239">HscrollBar</span></span>|  
|<span data-ttu-id="613a0-240">Obrázků</span><span class="sxs-lookup"><span data-stu-id="613a0-240">ImageList</span></span>|  
|<span data-ttu-id="613a0-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="613a0-241">Label</span></span>|  
|<span data-ttu-id="613a0-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="613a0-242">ListBox</span></span>|  
|<span data-ttu-id="613a0-243">ListView</span><span class="sxs-lookup"><span data-stu-id="613a0-243">ListView</span></span>|  
|<span data-ttu-id="613a0-244">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="613a0-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="613a0-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="613a0-245">MonthCalendar</span></span>|  
|<span data-ttu-id="613a0-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="613a0-246">NotifyIcon</span></span>|  
|<span data-ttu-id="613a0-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="613a0-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="613a0-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-249">PrintDialog</span></span>|  
|<span data-ttu-id="613a0-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="613a0-250">ProgressBar</span></span>|  
|<span data-ttu-id="613a0-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="613a0-251">RadioButton</span></span>|  
|<span data-ttu-id="613a0-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="613a0-252">RichTextBox</span></span>|  
|<span data-ttu-id="613a0-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="613a0-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="613a0-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="613a0-254">ScrollableControl</span></span>|  
|<span data-ttu-id="613a0-255">Komponentu</span><span class="sxs-lookup"><span data-stu-id="613a0-255">SoundPlayer</span></span>|  
|<span data-ttu-id="613a0-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="613a0-256">StatusBar</span></span>|  
|<span data-ttu-id="613a0-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="613a0-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="613a0-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="613a0-258">TextBox</span></span>|  
|<span data-ttu-id="613a0-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="613a0-259">Timer</span></span>|  
|<span data-ttu-id="613a0-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="613a0-260">Toolbar</span></span>|  
|<span data-ttu-id="613a0-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="613a0-261">ToolTip</span></span>|  
|<span data-ttu-id="613a0-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="613a0-262">TrackBar</span></span>|  
|<span data-ttu-id="613a0-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="613a0-263">TreeView</span></span>|  
|<span data-ttu-id="613a0-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="613a0-264">VscrollBar</span></span>|  
|<span data-ttu-id="613a0-265">Navig</span><span class="sxs-lookup"><span data-stu-id="613a0-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="613a0-266">Následující ovládací prvky jsou k dispozici pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jenom prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="613a0-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="613a0-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="613a0-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="613a0-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="613a0-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="613a0-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="613a0-269">BindingSource</span></span>|  
|<span data-ttu-id="613a0-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="613a0-270">DataGrid</span></span>|  
|<span data-ttu-id="613a0-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="613a0-271">DataGridView</span></span>|  
|<span data-ttu-id="613a0-272">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="613a0-272">DataNavigator</span></span>|  
|<span data-ttu-id="613a0-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="613a0-273">DomainUpDown</span></span>|  
|<span data-ttu-id="613a0-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="613a0-274">ErrorProvider</span></span>|  
|<span data-ttu-id="613a0-275">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="613a0-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="613a0-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="613a0-276">Form</span></span>|  
|<span data-ttu-id="613a0-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="613a0-277">LinkLabel</span></span>|  
|<span data-ttu-id="613a0-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="613a0-278">HelpProvider</span></span>|  
|<span data-ttu-id="613a0-279">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="613a0-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="613a0-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="613a0-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="613a0-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="613a0-281">NumericUpDown</span></span>|  
|<span data-ttu-id="613a0-282">Panel</span><span class="sxs-lookup"><span data-stu-id="613a0-282">Panel</span></span>|  
|<span data-ttu-id="613a0-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="613a0-283">PictureBox</span></span>|  
|<span data-ttu-id="613a0-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="613a0-284">PrintDocument</span></span>|  
|<span data-ttu-id="613a0-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="613a0-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="613a0-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="613a0-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="613a0-287">Mřížky</span><span class="sxs-lookup"><span data-stu-id="613a0-287">PropertyGrid</span></span>|  
|<span data-ttu-id="613a0-288">Type</span><span class="sxs-lookup"><span data-stu-id="613a0-288">UserControl</span></span>|  
|<span data-ttu-id="613a0-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="613a0-289">ToolStrip</span></span>|  
|<span data-ttu-id="613a0-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="613a0-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="613a0-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="613a0-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="613a0-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="613a0-292">Splitter</span></span>|  
|<span data-ttu-id="613a0-293">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="613a0-293">RaftingContainer</span></span>|  
|<span data-ttu-id="613a0-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="613a0-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="613a0-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="613a0-295">See also</span></span>

- [<span data-ttu-id="613a0-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="613a0-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
