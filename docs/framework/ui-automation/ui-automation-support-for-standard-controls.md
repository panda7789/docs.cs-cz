---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789604"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="52883-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="52883-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="52883-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="52883-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="52883-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="52883-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="52883-105">Toto téma obsahuje informace o podpoře [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro standardní ovládací prvky v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 a model Windows Forms architektury.</span><span class="sxs-lookup"><span data-stu-id="52883-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="52883-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="52883-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="52883-107">Všechny prvky ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52883-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="52883-108">Jiné prvky, například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52883-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="52883-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="52883-109">Win32 Controls</span></span>  
 <span data-ttu-id="52883-110">Většina ovládacích prvků Win32 je vystavena [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="52883-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="52883-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52883-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="52883-112">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 souboru *Comctrl32. dll*.</span><span class="sxs-lookup"><span data-stu-id="52883-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="52883-113">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="52883-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="52883-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="52883-114">Class name</span></span>|<span data-ttu-id="52883-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="52883-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="52883-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-116">Button</span></span>|<span data-ttu-id="52883-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-117">Button</span></span>|  
|<span data-ttu-id="52883-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-118">Button</span></span>|<span data-ttu-id="52883-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="52883-119">RadioButton</span></span>|  
|<span data-ttu-id="52883-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-120">Button</span></span>|<span data-ttu-id="52883-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="52883-121">Group</span></span>|  
|<span data-ttu-id="52883-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-122">Button</span></span>|<span data-ttu-id="52883-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="52883-123">CheckBox</span></span>|  
|<span data-ttu-id="52883-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-124">Button</span></span>|<span data-ttu-id="52883-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="52883-125">Hyperlink</span></span>|  
|<span data-ttu-id="52883-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-126">Button</span></span>|<span data-ttu-id="52883-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="52883-127">SplitButton</span></span>|  
|<span data-ttu-id="52883-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-128">Button</span></span>|<span data-ttu-id="52883-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="52883-129">CheckBox</span></span>|  
|<span data-ttu-id="52883-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="52883-130">ComboBoxEx32</span></span>|<span data-ttu-id="52883-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="52883-131">ComboBox</span></span>|  
|<span data-ttu-id="52883-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="52883-132">ComboBox</span></span>|<span data-ttu-id="52883-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="52883-133">ComboBox</span></span>|  
|<span data-ttu-id="52883-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="52883-134">Edit</span></span>|<span data-ttu-id="52883-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="52883-135">Document</span></span>|  
|<span data-ttu-id="52883-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="52883-136">Edit</span></span>|<span data-ttu-id="52883-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="52883-137">Edit</span></span>|  
|<span data-ttu-id="52883-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="52883-138">SysLink</span></span>|<span data-ttu-id="52883-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="52883-139">Hyperlink</span></span>|  
|<span data-ttu-id="52883-140">Statické</span><span class="sxs-lookup"><span data-stu-id="52883-140">Static</span></span>|<span data-ttu-id="52883-141">Text</span><span class="sxs-lookup"><span data-stu-id="52883-141">Text</span></span>|  
|<span data-ttu-id="52883-142">Statické</span><span class="sxs-lookup"><span data-stu-id="52883-142">Static</span></span>|<span data-ttu-id="52883-143">Obrázek</span><span class="sxs-lookup"><span data-stu-id="52883-143">Image</span></span>|  
|<span data-ttu-id="52883-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="52883-144">SysIPAddress32</span></span>|<span data-ttu-id="52883-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="52883-145">Custom</span></span>|  
|<span data-ttu-id="52883-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="52883-146">SysHeader32</span></span>|<span data-ttu-id="52883-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="52883-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="52883-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="52883-148">SysListView32</span></span>|<span data-ttu-id="52883-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="52883-149">DataGrid</span></span>|  
|<span data-ttu-id="52883-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="52883-150">SysListView32</span></span>|<span data-ttu-id="52883-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="52883-151">List</span></span>|  
|<span data-ttu-id="52883-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="52883-152">ListBox</span></span>|<span data-ttu-id="52883-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="52883-153">List</span></span>|  
|<span data-ttu-id="52883-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="52883-154">ListBox</span></span>|<span data-ttu-id="52883-155">Collection</span><span class="sxs-lookup"><span data-stu-id="52883-155">ListItem</span></span>|  
|<span data-ttu-id="52883-156">#32768</span><span class="sxs-lookup"><span data-stu-id="52883-156">#32768</span></span>|<span data-ttu-id="52883-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="52883-157">Menu</span></span>|  
|<span data-ttu-id="52883-158">#32768</span><span class="sxs-lookup"><span data-stu-id="52883-158">#32768</span></span>|<span data-ttu-id="52883-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="52883-159">MenuItem</span></span>|  
|<span data-ttu-id="52883-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="52883-160">msctls_progress32</span></span>|<span data-ttu-id="52883-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="52883-161">ProgressBar</span></span>|  
|<span data-ttu-id="52883-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="52883-162">RichEdit</span></span>|<span data-ttu-id="52883-163">Dokumentů.</span><span class="sxs-lookup"><span data-stu-id="52883-163">Document.</span></span> <span data-ttu-id="52883-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="52883-164">See note.</span></span>|  
|<span data-ttu-id="52883-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="52883-165">RichEdit20A</span></span>|<span data-ttu-id="52883-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="52883-166">Document</span></span>|  
|<span data-ttu-id="52883-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="52883-167">RichEdit20W</span></span>|<span data-ttu-id="52883-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="52883-168">Document</span></span>|  
|<span data-ttu-id="52883-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="52883-169">RichEdit50W</span></span>|<span data-ttu-id="52883-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="52883-170">Document</span></span>|  
|<span data-ttu-id="52883-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="52883-171">ScrollBar</span></span>|<span data-ttu-id="52883-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="52883-172">Slider</span></span>|  
|<span data-ttu-id="52883-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="52883-173">msctls_trackbar32</span></span>|<span data-ttu-id="52883-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="52883-174">Slider</span></span>|  
|<span data-ttu-id="52883-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="52883-175">msctls_updown32</span></span>|<span data-ttu-id="52883-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="52883-176">Spinner</span></span>|  
|<span data-ttu-id="52883-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="52883-177">msctls_statusbar32</span></span>|<span data-ttu-id="52883-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="52883-178">StatusBar</span></span>|  
|<span data-ttu-id="52883-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="52883-179">SysTabControl32</span></span>|<span data-ttu-id="52883-180">Karta</span><span class="sxs-lookup"><span data-stu-id="52883-180">Tab</span></span>|  
|<span data-ttu-id="52883-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="52883-181">SysTabControl32</span></span>|<span data-ttu-id="52883-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="52883-182">TabItem</span></span>|  
|<span data-ttu-id="52883-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-183">ToolbarWindow32</span></span>|<span data-ttu-id="52883-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="52883-184">ToolBar</span></span>|  
|<span data-ttu-id="52883-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-185">ToolbarWindow32</span></span>|<span data-ttu-id="52883-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="52883-186">MenuItem</span></span>|  
|<span data-ttu-id="52883-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-187">ToolbarWindow32</span></span>|<span data-ttu-id="52883-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-188">Button</span></span>|  
|<span data-ttu-id="52883-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-189">ToolbarWindow32</span></span>|<span data-ttu-id="52883-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="52883-190">CheckBox</span></span>|  
|<span data-ttu-id="52883-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-191">ToolbarWindow32</span></span>|<span data-ttu-id="52883-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="52883-192">RadioButton</span></span>|  
|<span data-ttu-id="52883-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-193">ToolbarWindow32</span></span>|<span data-ttu-id="52883-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="52883-194">Separator</span></span>|  
|<span data-ttu-id="52883-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="52883-195">tooltips_class32</span></span>|<span data-ttu-id="52883-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="52883-196">ToolTip</span></span>|  
|<span data-ttu-id="52883-197">#32774</span><span class="sxs-lookup"><span data-stu-id="52883-197">#32774</span></span>|<span data-ttu-id="52883-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="52883-198">ToolTip</span></span>|  
|<span data-ttu-id="52883-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="52883-199">ReBarWindow32</span></span>|<span data-ttu-id="52883-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="52883-200">Toolbar</span></span>|  
|<span data-ttu-id="52883-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="52883-201">SysTreeView32</span></span>|<span data-ttu-id="52883-202">Strom</span><span class="sxs-lookup"><span data-stu-id="52883-202">Tree</span></span>|  
|<span data-ttu-id="52883-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="52883-203">SysTreeView32</span></span>|<span data-ttu-id="52883-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="52883-204">TreeItem</span></span>|  
  
 <span data-ttu-id="52883-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="52883-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="52883-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="52883-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="52883-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="52883-207">Class name</span></span>|<span data-ttu-id="52883-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="52883-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="52883-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="52883-209">SysAnimate32</span></span>|<span data-ttu-id="52883-210">Obrázek</span><span class="sxs-lookup"><span data-stu-id="52883-210">Image</span></span>|  
|<span data-ttu-id="52883-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="52883-211">SysPager</span></span>|<span data-ttu-id="52883-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="52883-212">Spinner</span></span>|  
|<span data-ttu-id="52883-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="52883-213">SysDateTimePick32</span></span>|<span data-ttu-id="52883-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="52883-214">Custom</span></span>|  
|<span data-ttu-id="52883-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="52883-215">SysMonthCal32</span></span>|<span data-ttu-id="52883-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="52883-216">Calendar</span></span>|  
|<span data-ttu-id="52883-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="52883-217">MS_WINNOTE</span></span>|<span data-ttu-id="52883-218">okna</span><span class="sxs-lookup"><span data-stu-id="52883-218">Tooltip</span></span>|  
|<span data-ttu-id="52883-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="52883-219">VBBubble</span></span>|<span data-ttu-id="52883-220">okna</span><span class="sxs-lookup"><span data-stu-id="52883-220">Tooltip</span></span>|  
|<span data-ttu-id="52883-221">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="52883-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="52883-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="52883-222">Slider</span></span>|  
|<span data-ttu-id="52883-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="52883-223">SuperGrid</span></span>|<span data-ttu-id="52883-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="52883-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="52883-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52883-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="52883-226">Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="52883-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="52883-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52883-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="52883-228">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obvykle podporují model Windows Forms ovládací prvky, které jsou spravované obálky pro běžné ovládací prvky Win32.</span><span class="sxs-lookup"><span data-stu-id="52883-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="52883-229">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="52883-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="52883-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="52883-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="52883-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="52883-231">Button</span></span>|  
|<span data-ttu-id="52883-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="52883-232">CheckBox</span></span>|  
|<span data-ttu-id="52883-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="52883-233">CheckedListBox</span></span>|  
|<span data-ttu-id="52883-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="52883-234">ColorDialog</span></span>|  
|<span data-ttu-id="52883-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="52883-235">ComboBox</span></span>|  
|<span data-ttu-id="52883-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="52883-236">FolderBrowser</span></span>|  
|<span data-ttu-id="52883-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="52883-237">FontDialog</span></span>|  
|<span data-ttu-id="52883-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="52883-238">GroupBox</span></span>|  
|<span data-ttu-id="52883-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="52883-239">HscrollBar</span></span>|  
|<span data-ttu-id="52883-240">Obrázků</span><span class="sxs-lookup"><span data-stu-id="52883-240">ImageList</span></span>|  
|<span data-ttu-id="52883-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="52883-241">Label</span></span>|  
|<span data-ttu-id="52883-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="52883-242">ListBox</span></span>|  
|<span data-ttu-id="52883-243">ListView</span><span class="sxs-lookup"><span data-stu-id="52883-243">ListView</span></span>|  
|<span data-ttu-id="52883-244">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="52883-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="52883-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="52883-245">MonthCalendar</span></span>|  
|<span data-ttu-id="52883-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="52883-246">NotifyIcon</span></span>|  
|<span data-ttu-id="52883-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="52883-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="52883-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="52883-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="52883-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="52883-249">PrintDialog</span></span>|  
|<span data-ttu-id="52883-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="52883-250">ProgressBar</span></span>|  
|<span data-ttu-id="52883-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="52883-251">RadioButton</span></span>|  
|<span data-ttu-id="52883-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="52883-252">RichTextBox</span></span>|  
|<span data-ttu-id="52883-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="52883-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="52883-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="52883-254">ScrollableControl</span></span>|  
|<span data-ttu-id="52883-255">Komponentu</span><span class="sxs-lookup"><span data-stu-id="52883-255">SoundPlayer</span></span>|  
|<span data-ttu-id="52883-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="52883-256">StatusBar</span></span>|  
|<span data-ttu-id="52883-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="52883-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="52883-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="52883-258">TextBox</span></span>|  
|<span data-ttu-id="52883-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="52883-259">Timer</span></span>|  
|<span data-ttu-id="52883-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="52883-260">Toolbar</span></span>|  
|<span data-ttu-id="52883-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="52883-261">ToolTip</span></span>|  
|<span data-ttu-id="52883-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="52883-262">TrackBar</span></span>|  
|<span data-ttu-id="52883-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="52883-263">TreeView</span></span>|  
|<span data-ttu-id="52883-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="52883-264">VscrollBar</span></span>|  
|<span data-ttu-id="52883-265">Navig</span><span class="sxs-lookup"><span data-stu-id="52883-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="52883-266">Následující ovládací prvky jsou k dispozici pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jenom prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="52883-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="52883-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="52883-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="52883-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="52883-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="52883-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="52883-269">BindingSource</span></span>|  
|<span data-ttu-id="52883-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="52883-270">DataGrid</span></span>|  
|<span data-ttu-id="52883-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="52883-271">DataGridView</span></span>|  
|<span data-ttu-id="52883-272">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="52883-272">DataNavigator</span></span>|  
|<span data-ttu-id="52883-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="52883-273">DomainUpDown</span></span>|  
|<span data-ttu-id="52883-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="52883-274">ErrorProvider</span></span>|  
|<span data-ttu-id="52883-275">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="52883-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="52883-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="52883-276">Form</span></span>|  
|<span data-ttu-id="52883-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="52883-277">LinkLabel</span></span>|  
|<span data-ttu-id="52883-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="52883-278">HelpProvider</span></span>|  
|<span data-ttu-id="52883-279">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="52883-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="52883-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="52883-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="52883-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="52883-281">NumericUpDown</span></span>|  
|<span data-ttu-id="52883-282">Panel</span><span class="sxs-lookup"><span data-stu-id="52883-282">Panel</span></span>|  
|<span data-ttu-id="52883-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="52883-283">PictureBox</span></span>|  
|<span data-ttu-id="52883-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="52883-284">PrintDocument</span></span>|  
|<span data-ttu-id="52883-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="52883-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="52883-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="52883-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="52883-287">Mřížky</span><span class="sxs-lookup"><span data-stu-id="52883-287">PropertyGrid</span></span>|  
|<span data-ttu-id="52883-288">Type</span><span class="sxs-lookup"><span data-stu-id="52883-288">UserControl</span></span>|  
|<span data-ttu-id="52883-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="52883-289">ToolStrip</span></span>|  
|<span data-ttu-id="52883-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="52883-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="52883-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="52883-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="52883-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="52883-292">Splitter</span></span>|  
|<span data-ttu-id="52883-293">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="52883-293">RaftingContainer</span></span>|  
|<span data-ttu-id="52883-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="52883-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52883-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52883-295">See also</span></span>

- [<span data-ttu-id="52883-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="52883-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
