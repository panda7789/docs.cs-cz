---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: c59352f908c5f4a1fd2ca6dd631d26bb5d69f09a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441220"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="3f458-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="3f458-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="3f458-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="3f458-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3f458-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3f458-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3f458-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span><span class="sxs-lookup"><span data-stu-id="3f458-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="3f458-106">Windows Presentation Foundation Controls</span><span class="sxs-lookup"><span data-stu-id="3f458-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="3f458-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f458-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3f458-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f458-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="3f458-109">Win32 Controls</span><span class="sxs-lookup"><span data-stu-id="3f458-109">Win32 Controls</span></span>  
 <span data-ttu-id="3f458-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="3f458-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3f458-111">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="3f458-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3f458-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span><span class="sxs-lookup"><span data-stu-id="3f458-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="3f458-113">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="3f458-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3f458-114">Class name</span><span class="sxs-lookup"><span data-stu-id="3f458-114">Class name</span></span>|<span data-ttu-id="3f458-115">Control Type</span><span class="sxs-lookup"><span data-stu-id="3f458-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3f458-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-116">Button</span></span>|<span data-ttu-id="3f458-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-117">Button</span></span>|  
|<span data-ttu-id="3f458-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-118">Button</span></span>|<span data-ttu-id="3f458-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3f458-119">RadioButton</span></span>|  
|<span data-ttu-id="3f458-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-120">Button</span></span>|<span data-ttu-id="3f458-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="3f458-121">Group</span></span>|  
|<span data-ttu-id="3f458-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-122">Button</span></span>|<span data-ttu-id="3f458-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3f458-123">CheckBox</span></span>|  
|<span data-ttu-id="3f458-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-124">Button</span></span>|<span data-ttu-id="3f458-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="3f458-125">Hyperlink</span></span>|  
|<span data-ttu-id="3f458-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-126">Button</span></span>|<span data-ttu-id="3f458-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="3f458-127">SplitButton</span></span>|  
|<span data-ttu-id="3f458-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-128">Button</span></span>|<span data-ttu-id="3f458-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3f458-129">CheckBox</span></span>|  
|<span data-ttu-id="3f458-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="3f458-130">ComboBoxEx32</span></span>|<span data-ttu-id="3f458-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3f458-131">ComboBox</span></span>|  
|<span data-ttu-id="3f458-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3f458-132">ComboBox</span></span>|<span data-ttu-id="3f458-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3f458-133">ComboBox</span></span>|  
|<span data-ttu-id="3f458-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="3f458-134">Edit</span></span>|<span data-ttu-id="3f458-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="3f458-135">Document</span></span>|  
|<span data-ttu-id="3f458-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="3f458-136">Edit</span></span>|<span data-ttu-id="3f458-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="3f458-137">Edit</span></span>|  
|<span data-ttu-id="3f458-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="3f458-138">SysLink</span></span>|<span data-ttu-id="3f458-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="3f458-139">Hyperlink</span></span>|  
|<span data-ttu-id="3f458-140">Static</span><span class="sxs-lookup"><span data-stu-id="3f458-140">Static</span></span>|<span data-ttu-id="3f458-141">Text</span><span class="sxs-lookup"><span data-stu-id="3f458-141">Text</span></span>|  
|<span data-ttu-id="3f458-142">Static</span><span class="sxs-lookup"><span data-stu-id="3f458-142">Static</span></span>|<span data-ttu-id="3f458-143">Image</span><span class="sxs-lookup"><span data-stu-id="3f458-143">Image</span></span>|  
|<span data-ttu-id="3f458-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="3f458-144">SysIPAddress32</span></span>|<span data-ttu-id="3f458-145">Custom</span><span class="sxs-lookup"><span data-stu-id="3f458-145">Custom</span></span>|  
|<span data-ttu-id="3f458-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="3f458-146">SysHeader32</span></span>|<span data-ttu-id="3f458-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="3f458-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="3f458-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3f458-148">SysListView32</span></span>|<span data-ttu-id="3f458-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3f458-149">DataGrid</span></span>|  
|<span data-ttu-id="3f458-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3f458-150">SysListView32</span></span>|<span data-ttu-id="3f458-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="3f458-151">List</span></span>|  
|<span data-ttu-id="3f458-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="3f458-152">ListBox</span></span>|<span data-ttu-id="3f458-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="3f458-153">List</span></span>|  
|<span data-ttu-id="3f458-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="3f458-154">ListBox</span></span>|<span data-ttu-id="3f458-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="3f458-155">ListItem</span></span>|  
|<span data-ttu-id="3f458-156">#32768</span><span class="sxs-lookup"><span data-stu-id="3f458-156">#32768</span></span>|<span data-ttu-id="3f458-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="3f458-157">Menu</span></span>|  
|<span data-ttu-id="3f458-158">#32768</span><span class="sxs-lookup"><span data-stu-id="3f458-158">#32768</span></span>|<span data-ttu-id="3f458-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3f458-159">MenuItem</span></span>|  
|<span data-ttu-id="3f458-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="3f458-160">msctls_progress32</span></span>|<span data-ttu-id="3f458-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3f458-161">ProgressBar</span></span>|  
|<span data-ttu-id="3f458-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="3f458-162">RichEdit</span></span>|<span data-ttu-id="3f458-163">Document.</span><span class="sxs-lookup"><span data-stu-id="3f458-163">Document.</span></span> <span data-ttu-id="3f458-164">See note.</span><span class="sxs-lookup"><span data-stu-id="3f458-164">See note.</span></span>|  
|<span data-ttu-id="3f458-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="3f458-165">RichEdit20A</span></span>|<span data-ttu-id="3f458-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="3f458-166">Document</span></span>|  
|<span data-ttu-id="3f458-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="3f458-167">RichEdit20W</span></span>|<span data-ttu-id="3f458-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="3f458-168">Document</span></span>|  
|<span data-ttu-id="3f458-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="3f458-169">RichEdit50W</span></span>|<span data-ttu-id="3f458-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="3f458-170">Document</span></span>|  
|<span data-ttu-id="3f458-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="3f458-171">ScrollBar</span></span>|<span data-ttu-id="3f458-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="3f458-172">Slider</span></span>|  
|<span data-ttu-id="3f458-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="3f458-173">msctls_trackbar32</span></span>|<span data-ttu-id="3f458-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="3f458-174">Slider</span></span>|  
|<span data-ttu-id="3f458-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="3f458-175">msctls_updown32</span></span>|<span data-ttu-id="3f458-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="3f458-176">Spinner</span></span>|  
|<span data-ttu-id="3f458-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="3f458-177">msctls_statusbar32</span></span>|<span data-ttu-id="3f458-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3f458-178">StatusBar</span></span>|  
|<span data-ttu-id="3f458-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3f458-179">SysTabControl32</span></span>|<span data-ttu-id="3f458-180">Karta</span><span class="sxs-lookup"><span data-stu-id="3f458-180">Tab</span></span>|  
|<span data-ttu-id="3f458-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3f458-181">SysTabControl32</span></span>|<span data-ttu-id="3f458-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="3f458-182">TabItem</span></span>|  
|<span data-ttu-id="3f458-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-183">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="3f458-184">ToolBar</span></span>|  
|<span data-ttu-id="3f458-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-185">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3f458-186">MenuItem</span></span>|  
|<span data-ttu-id="3f458-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-187">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-188">Button</span></span>|  
|<span data-ttu-id="3f458-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-189">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3f458-190">CheckBox</span></span>|  
|<span data-ttu-id="3f458-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-191">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3f458-192">RadioButton</span></span>|  
|<span data-ttu-id="3f458-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-193">ToolbarWindow32</span></span>|<span data-ttu-id="3f458-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="3f458-194">Separator</span></span>|  
|<span data-ttu-id="3f458-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="3f458-195">tooltips_class32</span></span>|<span data-ttu-id="3f458-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="3f458-196">ToolTip</span></span>|  
|<span data-ttu-id="3f458-197">#32774</span><span class="sxs-lookup"><span data-stu-id="3f458-197">#32774</span></span>|<span data-ttu-id="3f458-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="3f458-198">ToolTip</span></span>|  
|<span data-ttu-id="3f458-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="3f458-199">ReBarWindow32</span></span>|<span data-ttu-id="3f458-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="3f458-200">Toolbar</span></span>|  
|<span data-ttu-id="3f458-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3f458-201">SysTreeView32</span></span>|<span data-ttu-id="3f458-202">Strom</span><span class="sxs-lookup"><span data-stu-id="3f458-202">Tree</span></span>|  
|<span data-ttu-id="3f458-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3f458-203">SysTreeView32</span></span>|<span data-ttu-id="3f458-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="3f458-204">TreeItem</span></span>|  
  
 <span data-ttu-id="3f458-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span><span class="sxs-lookup"><span data-stu-id="3f458-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="3f458-206">The following controls are not supported.</span><span class="sxs-lookup"><span data-stu-id="3f458-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="3f458-207">Class name</span><span class="sxs-lookup"><span data-stu-id="3f458-207">Class name</span></span>|<span data-ttu-id="3f458-208">Control type</span><span class="sxs-lookup"><span data-stu-id="3f458-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3f458-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="3f458-209">SysAnimate32</span></span>|<span data-ttu-id="3f458-210">Image</span><span class="sxs-lookup"><span data-stu-id="3f458-210">Image</span></span>|  
|<span data-ttu-id="3f458-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="3f458-211">SysPager</span></span>|<span data-ttu-id="3f458-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="3f458-212">Spinner</span></span>|  
|<span data-ttu-id="3f458-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="3f458-213">SysDateTimePick32</span></span>|<span data-ttu-id="3f458-214">Custom</span><span class="sxs-lookup"><span data-stu-id="3f458-214">Custom</span></span>|  
|<span data-ttu-id="3f458-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="3f458-215">SysMonthCal32</span></span>|<span data-ttu-id="3f458-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="3f458-216">Calendar</span></span>|  
|<span data-ttu-id="3f458-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="3f458-217">MS_WINNOTE</span></span>|<span data-ttu-id="3f458-218">Tooltip</span><span class="sxs-lookup"><span data-stu-id="3f458-218">Tooltip</span></span>|  
|<span data-ttu-id="3f458-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="3f458-219">VBBubble</span></span>|<span data-ttu-id="3f458-220">Tooltip</span><span class="sxs-lookup"><span data-stu-id="3f458-220">Tooltip</span></span>|  
|<span data-ttu-id="3f458-221">ScrollBar (when used as a standalone control)</span><span class="sxs-lookup"><span data-stu-id="3f458-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="3f458-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="3f458-222">Slider</span></span>|  
|<span data-ttu-id="3f458-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="3f458-223">SuperGrid</span></span>|<span data-ttu-id="3f458-224">Custom</span><span class="sxs-lookup"><span data-stu-id="3f458-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="3f458-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f458-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="3f458-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="3f458-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3f458-227">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="3f458-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3f458-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f458-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3f458-229">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="3f458-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3f458-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="3f458-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="3f458-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f458-231">Button</span></span>|  
|<span data-ttu-id="3f458-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3f458-232">CheckBox</span></span>|  
|<span data-ttu-id="3f458-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="3f458-233">CheckedListBox</span></span>|  
|<span data-ttu-id="3f458-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-234">ColorDialog</span></span>|  
|<span data-ttu-id="3f458-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3f458-235">ComboBox</span></span>|  
|<span data-ttu-id="3f458-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="3f458-236">FolderBrowser</span></span>|  
|<span data-ttu-id="3f458-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-237">FontDialog</span></span>|  
|<span data-ttu-id="3f458-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="3f458-238">GroupBox</span></span>|  
|<span data-ttu-id="3f458-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="3f458-239">HscrollBar</span></span>|  
|<span data-ttu-id="3f458-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="3f458-240">ImageList</span></span>|  
|<span data-ttu-id="3f458-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="3f458-241">Label</span></span>|  
|<span data-ttu-id="3f458-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="3f458-242">ListBox</span></span>|  
|<span data-ttu-id="3f458-243">ListView</span><span class="sxs-lookup"><span data-stu-id="3f458-243">ListView</span></span>|  
|<span data-ttu-id="3f458-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3f458-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="3f458-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="3f458-245">MonthCalendar</span></span>|  
|<span data-ttu-id="3f458-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="3f458-246">NotifyIcon</span></span>|  
|<span data-ttu-id="3f458-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="3f458-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="3f458-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-249">PrintDialog</span></span>|  
|<span data-ttu-id="3f458-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3f458-250">ProgressBar</span></span>|  
|<span data-ttu-id="3f458-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3f458-251">RadioButton</span></span>|  
|<span data-ttu-id="3f458-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="3f458-252">RichTextBox</span></span>|  
|<span data-ttu-id="3f458-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="3f458-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="3f458-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="3f458-254">ScrollableControl</span></span>|  
|<span data-ttu-id="3f458-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="3f458-255">SoundPlayer</span></span>|  
|<span data-ttu-id="3f458-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3f458-256">StatusBar</span></span>|  
|<span data-ttu-id="3f458-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="3f458-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="3f458-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="3f458-258">TextBox</span></span>|  
|<span data-ttu-id="3f458-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="3f458-259">Timer</span></span>|  
|<span data-ttu-id="3f458-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="3f458-260">Toolbar</span></span>|  
|<span data-ttu-id="3f458-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="3f458-261">ToolTip</span></span>|  
|<span data-ttu-id="3f458-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="3f458-262">TrackBar</span></span>|  
|<span data-ttu-id="3f458-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="3f458-263">TreeView</span></span>|  
|<span data-ttu-id="3f458-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="3f458-264">VscrollBar</span></span>|  
|<span data-ttu-id="3f458-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="3f458-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="3f458-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="3f458-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="3f458-267">Some functionality may not be available.</span><span class="sxs-lookup"><span data-stu-id="3f458-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="3f458-268">Control Name</span><span class="sxs-lookup"><span data-stu-id="3f458-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="3f458-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="3f458-269">BindingSource</span></span>|  
|<span data-ttu-id="3f458-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3f458-270">DataGrid</span></span>|  
|<span data-ttu-id="3f458-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="3f458-271">DataGridView</span></span>|  
|<span data-ttu-id="3f458-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="3f458-272">DataNavigator</span></span>|  
|<span data-ttu-id="3f458-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="3f458-273">DomainUpDown</span></span>|  
|<span data-ttu-id="3f458-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="3f458-274">ErrorProvider</span></span>|  
|<span data-ttu-id="3f458-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3f458-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="3f458-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="3f458-276">Form</span></span>|  
|<span data-ttu-id="3f458-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="3f458-277">LinkLabel</span></span>|  
|<span data-ttu-id="3f458-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="3f458-278">HelpProvider</span></span>|  
|<span data-ttu-id="3f458-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="3f458-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="3f458-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3f458-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="3f458-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="3f458-281">NumericUpDown</span></span>|  
|<span data-ttu-id="3f458-282">Panel</span><span class="sxs-lookup"><span data-stu-id="3f458-282">Panel</span></span>|  
|<span data-ttu-id="3f458-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="3f458-283">PictureBox</span></span>|  
|<span data-ttu-id="3f458-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="3f458-284">PrintDocument</span></span>|  
|<span data-ttu-id="3f458-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="3f458-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="3f458-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="3f458-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="3f458-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="3f458-287">PropertyGrid</span></span>|  
|<span data-ttu-id="3f458-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="3f458-288">UserControl</span></span>|  
|<span data-ttu-id="3f458-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3f458-289">ToolStrip</span></span>|  
|<span data-ttu-id="3f458-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3f458-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="3f458-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="3f458-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="3f458-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="3f458-292">Splitter</span></span>|  
|<span data-ttu-id="3f458-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="3f458-293">RaftingContainer</span></span>|  
|<span data-ttu-id="3f458-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="3f458-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f458-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f458-295">See also</span></span>

- [<span data-ttu-id="3f458-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f458-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
