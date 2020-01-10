---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: ed5e4f6ab23fe9ae77c94616a668da8accb46d4b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741697"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="49b31-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="49b31-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="49b31-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="49b31-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="49b31-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="49b31-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="49b31-105">Toto téma obsahuje informace o podpoře [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro standardní ovládací prvky v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.</span><span class="sxs-lookup"><span data-stu-id="49b31-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="49b31-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="49b31-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="49b31-107">Všechny prvky ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49b31-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="49b31-108">Jiné prvky, například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49b31-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="49b31-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="49b31-109">Win32 Controls</span></span>  
 <span data-ttu-id="49b31-110">Většina ovládacích prvků Win32 je vystavena [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="49b31-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="49b31-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49b31-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="49b31-112">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 souboru *Comctrl32. dll*.</span><span class="sxs-lookup"><span data-stu-id="49b31-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="49b31-113">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="49b31-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="49b31-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49b31-114">Class name</span></span>|<span data-ttu-id="49b31-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49b31-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="49b31-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-116">Button</span></span>|<span data-ttu-id="49b31-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-117">Button</span></span>|  
|<span data-ttu-id="49b31-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-118">Button</span></span>|<span data-ttu-id="49b31-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49b31-119">RadioButton</span></span>|  
|<span data-ttu-id="49b31-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-120">Button</span></span>|<span data-ttu-id="49b31-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="49b31-121">Group</span></span>|  
|<span data-ttu-id="49b31-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-122">Button</span></span>|<span data-ttu-id="49b31-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49b31-123">CheckBox</span></span>|  
|<span data-ttu-id="49b31-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-124">Button</span></span>|<span data-ttu-id="49b31-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="49b31-125">Hyperlink</span></span>|  
|<span data-ttu-id="49b31-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-126">Button</span></span>|<span data-ttu-id="49b31-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="49b31-127">SplitButton</span></span>|  
|<span data-ttu-id="49b31-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-128">Button</span></span>|<span data-ttu-id="49b31-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49b31-129">CheckBox</span></span>|  
|<span data-ttu-id="49b31-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="49b31-130">ComboBoxEx32</span></span>|<span data-ttu-id="49b31-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49b31-131">ComboBox</span></span>|  
|<span data-ttu-id="49b31-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49b31-132">ComboBox</span></span>|<span data-ttu-id="49b31-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49b31-133">ComboBox</span></span>|  
|<span data-ttu-id="49b31-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="49b31-134">Edit</span></span>|<span data-ttu-id="49b31-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="49b31-135">Document</span></span>|  
|<span data-ttu-id="49b31-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="49b31-136">Edit</span></span>|<span data-ttu-id="49b31-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="49b31-137">Edit</span></span>|  
|<span data-ttu-id="49b31-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="49b31-138">SysLink</span></span>|<span data-ttu-id="49b31-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="49b31-139">Hyperlink</span></span>|  
|<span data-ttu-id="49b31-140">Statické</span><span class="sxs-lookup"><span data-stu-id="49b31-140">Static</span></span>|<span data-ttu-id="49b31-141">Text</span><span class="sxs-lookup"><span data-stu-id="49b31-141">Text</span></span>|  
|<span data-ttu-id="49b31-142">Statické</span><span class="sxs-lookup"><span data-stu-id="49b31-142">Static</span></span>|<span data-ttu-id="49b31-143">Obrázek</span><span class="sxs-lookup"><span data-stu-id="49b31-143">Image</span></span>|  
|<span data-ttu-id="49b31-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="49b31-144">SysIPAddress32</span></span>|<span data-ttu-id="49b31-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49b31-145">Custom</span></span>|  
|<span data-ttu-id="49b31-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="49b31-146">SysHeader32</span></span>|<span data-ttu-id="49b31-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="49b31-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="49b31-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="49b31-148">SysListView32</span></span>|<span data-ttu-id="49b31-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="49b31-149">DataGrid</span></span>|  
|<span data-ttu-id="49b31-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="49b31-150">SysListView32</span></span>|<span data-ttu-id="49b31-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="49b31-151">List</span></span>|  
|<span data-ttu-id="49b31-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="49b31-152">ListBox</span></span>|<span data-ttu-id="49b31-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="49b31-153">List</span></span>|  
|<span data-ttu-id="49b31-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="49b31-154">ListBox</span></span>|<span data-ttu-id="49b31-155">Collection</span><span class="sxs-lookup"><span data-stu-id="49b31-155">ListItem</span></span>|  
|<span data-ttu-id="49b31-156">#32768</span><span class="sxs-lookup"><span data-stu-id="49b31-156">#32768</span></span>|<span data-ttu-id="49b31-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="49b31-157">Menu</span></span>|  
|<span data-ttu-id="49b31-158">#32768</span><span class="sxs-lookup"><span data-stu-id="49b31-158">#32768</span></span>|<span data-ttu-id="49b31-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="49b31-159">MenuItem</span></span>|  
|<span data-ttu-id="49b31-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="49b31-160">msctls_progress32</span></span>|<span data-ttu-id="49b31-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="49b31-161">ProgressBar</span></span>|  
|<span data-ttu-id="49b31-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="49b31-162">RichEdit</span></span>|<span data-ttu-id="49b31-163">Dokumentů.</span><span class="sxs-lookup"><span data-stu-id="49b31-163">Document.</span></span> <span data-ttu-id="49b31-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="49b31-164">See note.</span></span>|  
|<span data-ttu-id="49b31-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="49b31-165">RichEdit20A</span></span>|<span data-ttu-id="49b31-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="49b31-166">Document</span></span>|  
|<span data-ttu-id="49b31-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="49b31-167">RichEdit20W</span></span>|<span data-ttu-id="49b31-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="49b31-168">Document</span></span>|  
|<span data-ttu-id="49b31-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="49b31-169">RichEdit50W</span></span>|<span data-ttu-id="49b31-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="49b31-170">Document</span></span>|  
|<span data-ttu-id="49b31-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="49b31-171">ScrollBar</span></span>|<span data-ttu-id="49b31-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49b31-172">Slider</span></span>|  
|<span data-ttu-id="49b31-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="49b31-173">msctls_trackbar32</span></span>|<span data-ttu-id="49b31-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49b31-174">Slider</span></span>|  
|<span data-ttu-id="49b31-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="49b31-175">msctls_updown32</span></span>|<span data-ttu-id="49b31-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="49b31-176">Spinner</span></span>|  
|<span data-ttu-id="49b31-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="49b31-177">msctls_statusbar32</span></span>|<span data-ttu-id="49b31-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="49b31-178">StatusBar</span></span>|  
|<span data-ttu-id="49b31-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="49b31-179">SysTabControl32</span></span>|<span data-ttu-id="49b31-180">Karta</span><span class="sxs-lookup"><span data-stu-id="49b31-180">Tab</span></span>|  
|<span data-ttu-id="49b31-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="49b31-181">SysTabControl32</span></span>|<span data-ttu-id="49b31-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="49b31-182">TabItem</span></span>|  
|<span data-ttu-id="49b31-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-183">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="49b31-184">ToolBar</span></span>|  
|<span data-ttu-id="49b31-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-185">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="49b31-186">MenuItem</span></span>|  
|<span data-ttu-id="49b31-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-187">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-188">Button</span></span>|  
|<span data-ttu-id="49b31-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-189">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49b31-190">CheckBox</span></span>|  
|<span data-ttu-id="49b31-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-191">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49b31-192">RadioButton</span></span>|  
|<span data-ttu-id="49b31-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-193">ToolbarWindow32</span></span>|<span data-ttu-id="49b31-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="49b31-194">Separator</span></span>|  
|<span data-ttu-id="49b31-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="49b31-195">tooltips_class32</span></span>|<span data-ttu-id="49b31-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49b31-196">ToolTip</span></span>|  
|<span data-ttu-id="49b31-197">#32774</span><span class="sxs-lookup"><span data-stu-id="49b31-197">#32774</span></span>|<span data-ttu-id="49b31-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49b31-198">ToolTip</span></span>|  
|<span data-ttu-id="49b31-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="49b31-199">ReBarWindow32</span></span>|<span data-ttu-id="49b31-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="49b31-200">Toolbar</span></span>|  
|<span data-ttu-id="49b31-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="49b31-201">SysTreeView32</span></span>|<span data-ttu-id="49b31-202">Strom</span><span class="sxs-lookup"><span data-stu-id="49b31-202">Tree</span></span>|  
|<span data-ttu-id="49b31-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="49b31-203">SysTreeView32</span></span>|<span data-ttu-id="49b31-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="49b31-204">TreeItem</span></span>|  
  
 <span data-ttu-id="49b31-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="49b31-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="49b31-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="49b31-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="49b31-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49b31-207">Class name</span></span>|<span data-ttu-id="49b31-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49b31-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="49b31-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="49b31-209">SysAnimate32</span></span>|<span data-ttu-id="49b31-210">Obrázek</span><span class="sxs-lookup"><span data-stu-id="49b31-210">Image</span></span>|  
|<span data-ttu-id="49b31-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="49b31-211">SysPager</span></span>|<span data-ttu-id="49b31-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="49b31-212">Spinner</span></span>|  
|<span data-ttu-id="49b31-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="49b31-213">SysDateTimePick32</span></span>|<span data-ttu-id="49b31-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49b31-214">Custom</span></span>|  
|<span data-ttu-id="49b31-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="49b31-215">SysMonthCal32</span></span>|<span data-ttu-id="49b31-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="49b31-216">Calendar</span></span>|  
|<span data-ttu-id="49b31-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="49b31-217">MS_WINNOTE</span></span>|<span data-ttu-id="49b31-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="49b31-218">Tooltip</span></span>|  
|<span data-ttu-id="49b31-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="49b31-219">VBBubble</span></span>|<span data-ttu-id="49b31-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="49b31-220">Tooltip</span></span>|  
|<span data-ttu-id="49b31-221">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="49b31-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="49b31-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49b31-222">Slider</span></span>|  
|<span data-ttu-id="49b31-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="49b31-223">SuperGrid</span></span>|<span data-ttu-id="49b31-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49b31-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="49b31-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49b31-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="49b31-226">Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="49b31-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="49b31-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49b31-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="49b31-228">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obvykle podporují model Windows Forms ovládací prvky, které jsou spravované obálky pro běžné ovládací prvky Win32.</span><span class="sxs-lookup"><span data-stu-id="49b31-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="49b31-229">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="49b31-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="49b31-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49b31-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="49b31-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49b31-231">Button</span></span>|  
|<span data-ttu-id="49b31-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49b31-232">CheckBox</span></span>|  
|<span data-ttu-id="49b31-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="49b31-233">CheckedListBox</span></span>|  
|<span data-ttu-id="49b31-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-234">ColorDialog</span></span>|  
|<span data-ttu-id="49b31-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49b31-235">ComboBox</span></span>|  
|<span data-ttu-id="49b31-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="49b31-236">FolderBrowser</span></span>|  
|<span data-ttu-id="49b31-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-237">FontDialog</span></span>|  
|<span data-ttu-id="49b31-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="49b31-238">GroupBox</span></span>|  
|<span data-ttu-id="49b31-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="49b31-239">HscrollBar</span></span>|  
|<span data-ttu-id="49b31-240">Obrázků</span><span class="sxs-lookup"><span data-stu-id="49b31-240">ImageList</span></span>|  
|<span data-ttu-id="49b31-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="49b31-241">Label</span></span>|  
|<span data-ttu-id="49b31-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="49b31-242">ListBox</span></span>|  
|<span data-ttu-id="49b31-243">ListView</span><span class="sxs-lookup"><span data-stu-id="49b31-243">ListView</span></span>|  
|<span data-ttu-id="49b31-244">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="49b31-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="49b31-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="49b31-245">MonthCalendar</span></span>|  
|<span data-ttu-id="49b31-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="49b31-246">NotifyIcon</span></span>|  
|<span data-ttu-id="49b31-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="49b31-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="49b31-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-249">PrintDialog</span></span>|  
|<span data-ttu-id="49b31-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="49b31-250">ProgressBar</span></span>|  
|<span data-ttu-id="49b31-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49b31-251">RadioButton</span></span>|  
|<span data-ttu-id="49b31-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="49b31-252">RichTextBox</span></span>|  
|<span data-ttu-id="49b31-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="49b31-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="49b31-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="49b31-254">ScrollableControl</span></span>|  
|<span data-ttu-id="49b31-255">Komponentu</span><span class="sxs-lookup"><span data-stu-id="49b31-255">SoundPlayer</span></span>|  
|<span data-ttu-id="49b31-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="49b31-256">StatusBar</span></span>|  
|<span data-ttu-id="49b31-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="49b31-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="49b31-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="49b31-258">TextBox</span></span>|  
|<span data-ttu-id="49b31-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="49b31-259">Timer</span></span>|  
|<span data-ttu-id="49b31-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="49b31-260">Toolbar</span></span>|  
|<span data-ttu-id="49b31-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49b31-261">ToolTip</span></span>|  
|<span data-ttu-id="49b31-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="49b31-262">TrackBar</span></span>|  
|<span data-ttu-id="49b31-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="49b31-263">TreeView</span></span>|  
|<span data-ttu-id="49b31-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="49b31-264">VscrollBar</span></span>|  
|<span data-ttu-id="49b31-265">Navig</span><span class="sxs-lookup"><span data-stu-id="49b31-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="49b31-266">Následující ovládací prvky jsou k dispozici pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jenom prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="49b31-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="49b31-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="49b31-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="49b31-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49b31-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="49b31-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="49b31-269">BindingSource</span></span>|  
|<span data-ttu-id="49b31-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="49b31-270">DataGrid</span></span>|  
|<span data-ttu-id="49b31-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="49b31-271">DataGridView</span></span>|  
|<span data-ttu-id="49b31-272">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="49b31-272">DataNavigator</span></span>|  
|<span data-ttu-id="49b31-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="49b31-273">DomainUpDown</span></span>|  
|<span data-ttu-id="49b31-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="49b31-274">ErrorProvider</span></span>|  
|<span data-ttu-id="49b31-275">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="49b31-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="49b31-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="49b31-276">Form</span></span>|  
|<span data-ttu-id="49b31-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="49b31-277">LinkLabel</span></span>|  
|<span data-ttu-id="49b31-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="49b31-278">HelpProvider</span></span>|  
|<span data-ttu-id="49b31-279">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="49b31-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="49b31-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="49b31-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="49b31-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="49b31-281">NumericUpDown</span></span>|  
|<span data-ttu-id="49b31-282">Panel</span><span class="sxs-lookup"><span data-stu-id="49b31-282">Panel</span></span>|  
|<span data-ttu-id="49b31-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="49b31-283">PictureBox</span></span>|  
|<span data-ttu-id="49b31-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="49b31-284">PrintDocument</span></span>|  
|<span data-ttu-id="49b31-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="49b31-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="49b31-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="49b31-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="49b31-287">Mřížky</span><span class="sxs-lookup"><span data-stu-id="49b31-287">PropertyGrid</span></span>|  
|<span data-ttu-id="49b31-288">Type</span><span class="sxs-lookup"><span data-stu-id="49b31-288">UserControl</span></span>|  
|<span data-ttu-id="49b31-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="49b31-289">ToolStrip</span></span>|  
|<span data-ttu-id="49b31-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="49b31-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="49b31-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="49b31-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="49b31-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="49b31-292">Splitter</span></span>|  
|<span data-ttu-id="49b31-293">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="49b31-293">RaftingContainer</span></span>|  
|<span data-ttu-id="49b31-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="49b31-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49b31-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49b31-295">See also</span></span>

- [<span data-ttu-id="49b31-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="49b31-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
