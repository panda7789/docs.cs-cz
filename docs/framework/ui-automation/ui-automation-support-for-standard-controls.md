---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041999"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="d9b7d-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d9b7d-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="d9b7d-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d9b7d-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d9b7d-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře standardních ovládacích prvků v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]rozhraní [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d9b7d-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="d9b7d-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d9b7d-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="d9b7d-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky ovládacích prvků, které poskytují informace nebo podporu pro interakci s uživatelem, mají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]úplnou nativní podporu pro.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d9b7d-108">Jiné prvky, například panely, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9b7d-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="d9b7d-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-109">Win32 Controls</span></span>  
 <span data-ttu-id="d9b7d-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků je vystavena prostřednictvím poskytovatelů na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d9b7d-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d9b7d-112">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 Comctrl32. dll ( [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] k dispozici v a novějších verzích).</span><span class="sxs-lookup"><span data-stu-id="d9b7d-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="d9b7d-113">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d9b7d-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="d9b7d-114">Class name</span></span>|<span data-ttu-id="d9b7d-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9b7d-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d9b7d-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-116">Button</span></span>|<span data-ttu-id="d9b7d-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-117">Button</span></span>|  
|<span data-ttu-id="d9b7d-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-118">Button</span></span>|<span data-ttu-id="d9b7d-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d9b7d-119">RadioButton</span></span>|  
|<span data-ttu-id="d9b7d-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-120">Button</span></span>|<span data-ttu-id="d9b7d-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="d9b7d-121">Group</span></span>|  
|<span data-ttu-id="d9b7d-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-122">Button</span></span>|<span data-ttu-id="d9b7d-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-123">CheckBox</span></span>|  
|<span data-ttu-id="d9b7d-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-124">Button</span></span>|<span data-ttu-id="d9b7d-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="d9b7d-125">Hyperlink</span></span>|  
|<span data-ttu-id="d9b7d-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-126">Button</span></span>|<span data-ttu-id="d9b7d-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="d9b7d-127">SplitButton</span></span>|  
|<span data-ttu-id="d9b7d-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-128">Button</span></span>|<span data-ttu-id="d9b7d-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-129">CheckBox</span></span>|  
|<span data-ttu-id="d9b7d-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-130">ComboBoxEx32</span></span>|<span data-ttu-id="d9b7d-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-131">ComboBox</span></span>|  
|<span data-ttu-id="d9b7d-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-132">ComboBox</span></span>|<span data-ttu-id="d9b7d-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-133">ComboBox</span></span>|  
|<span data-ttu-id="d9b7d-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="d9b7d-134">Edit</span></span>|<span data-ttu-id="d9b7d-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="d9b7d-135">Document</span></span>|  
|<span data-ttu-id="d9b7d-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="d9b7d-136">Edit</span></span>|<span data-ttu-id="d9b7d-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="d9b7d-137">Edit</span></span>|  
|<span data-ttu-id="d9b7d-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="d9b7d-138">SysLink</span></span>|<span data-ttu-id="d9b7d-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="d9b7d-139">Hyperlink</span></span>|  
|<span data-ttu-id="d9b7d-140">Static</span><span class="sxs-lookup"><span data-stu-id="d9b7d-140">Static</span></span>|<span data-ttu-id="d9b7d-141">Text</span><span class="sxs-lookup"><span data-stu-id="d9b7d-141">Text</span></span>|  
|<span data-ttu-id="d9b7d-142">Static</span><span class="sxs-lookup"><span data-stu-id="d9b7d-142">Static</span></span>|<span data-ttu-id="d9b7d-143">Image</span><span class="sxs-lookup"><span data-stu-id="d9b7d-143">Image</span></span>|  
|<span data-ttu-id="d9b7d-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-144">SysIPAddress32</span></span>|<span data-ttu-id="d9b7d-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="d9b7d-145">Custom</span></span>|  
|<span data-ttu-id="d9b7d-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-146">SysHeader32</span></span>|<span data-ttu-id="d9b7d-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="d9b7d-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="d9b7d-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-148">SysListView32</span></span>|<span data-ttu-id="d9b7d-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d9b7d-149">DataGrid</span></span>|  
|<span data-ttu-id="d9b7d-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-150">SysListView32</span></span>|<span data-ttu-id="d9b7d-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="d9b7d-151">List</span></span>|  
|<span data-ttu-id="d9b7d-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-152">ListBox</span></span>|<span data-ttu-id="d9b7d-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="d9b7d-153">List</span></span>|  
|<span data-ttu-id="d9b7d-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-154">ListBox</span></span>|<span data-ttu-id="d9b7d-155">Collection</span><span class="sxs-lookup"><span data-stu-id="d9b7d-155">ListItem</span></span>|  
|<span data-ttu-id="d9b7d-156">#32768</span><span class="sxs-lookup"><span data-stu-id="d9b7d-156">#32768</span></span>|<span data-ttu-id="d9b7d-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="d9b7d-157">Menu</span></span>|  
|<span data-ttu-id="d9b7d-158">#32768</span><span class="sxs-lookup"><span data-stu-id="d9b7d-158">#32768</span></span>|<span data-ttu-id="d9b7d-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d9b7d-159">MenuItem</span></span>|  
|<span data-ttu-id="d9b7d-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-160">msctls_progress32</span></span>|<span data-ttu-id="d9b7d-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-161">ProgressBar</span></span>|  
|<span data-ttu-id="d9b7d-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="d9b7d-162">RichEdit</span></span>|<span data-ttu-id="d9b7d-163">dokumentů.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-163">Document.</span></span> <span data-ttu-id="d9b7d-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-164">See note.</span></span>|  
|<span data-ttu-id="d9b7d-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="d9b7d-165">RichEdit20A</span></span>|<span data-ttu-id="d9b7d-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="d9b7d-166">Document</span></span>|  
|<span data-ttu-id="d9b7d-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="d9b7d-167">RichEdit20W</span></span>|<span data-ttu-id="d9b7d-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="d9b7d-168">Document</span></span>|  
|<span data-ttu-id="d9b7d-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="d9b7d-169">RichEdit50W</span></span>|<span data-ttu-id="d9b7d-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="d9b7d-170">Document</span></span>|  
|<span data-ttu-id="d9b7d-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-171">ScrollBar</span></span>|<span data-ttu-id="d9b7d-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="d9b7d-172">Slider</span></span>|  
|<span data-ttu-id="d9b7d-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-173">msctls_trackbar32</span></span>|<span data-ttu-id="d9b7d-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="d9b7d-174">Slider</span></span>|  
|<span data-ttu-id="d9b7d-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-175">msctls_updown32</span></span>|<span data-ttu-id="d9b7d-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="d9b7d-176">Spinner</span></span>|  
|<span data-ttu-id="d9b7d-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-177">msctls_statusbar32</span></span>|<span data-ttu-id="d9b7d-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-178">StatusBar</span></span>|  
|<span data-ttu-id="d9b7d-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-179">SysTabControl32</span></span>|<span data-ttu-id="d9b7d-180">Karta</span><span class="sxs-lookup"><span data-stu-id="d9b7d-180">Tab</span></span>|  
|<span data-ttu-id="d9b7d-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-181">SysTabControl32</span></span>|<span data-ttu-id="d9b7d-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="d9b7d-182">TabItem</span></span>|  
|<span data-ttu-id="d9b7d-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-183">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-184">ToolBar</span></span>|  
|<span data-ttu-id="d9b7d-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-185">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d9b7d-186">MenuItem</span></span>|  
|<span data-ttu-id="d9b7d-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-187">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-188">Button</span></span>|  
|<span data-ttu-id="d9b7d-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-189">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-190">CheckBox</span></span>|  
|<span data-ttu-id="d9b7d-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-191">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d9b7d-192">RadioButton</span></span>|  
|<span data-ttu-id="d9b7d-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-193">ToolbarWindow32</span></span>|<span data-ttu-id="d9b7d-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="d9b7d-194">Separator</span></span>|  
|<span data-ttu-id="d9b7d-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-195">tooltips_class32</span></span>|<span data-ttu-id="d9b7d-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="d9b7d-196">ToolTip</span></span>|  
|<span data-ttu-id="d9b7d-197">#32774</span><span class="sxs-lookup"><span data-stu-id="d9b7d-197">#32774</span></span>|<span data-ttu-id="d9b7d-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="d9b7d-198">ToolTip</span></span>|  
|<span data-ttu-id="d9b7d-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-199">ReBarWindow32</span></span>|<span data-ttu-id="d9b7d-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="d9b7d-200">Toolbar</span></span>|  
|<span data-ttu-id="d9b7d-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-201">SysTreeView32</span></span>|<span data-ttu-id="d9b7d-202">Strom</span><span class="sxs-lookup"><span data-stu-id="d9b7d-202">Tree</span></span>|  
|<span data-ttu-id="d9b7d-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-203">SysTreeView32</span></span>|<span data-ttu-id="d9b7d-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="d9b7d-204">TreeItem</span></span>|  
  
 <span data-ttu-id="d9b7d-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] systémem (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="d9b7d-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="d9b7d-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="d9b7d-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="d9b7d-207">Class name</span></span>|<span data-ttu-id="d9b7d-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9b7d-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d9b7d-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-209">SysAnimate32</span></span>|<span data-ttu-id="d9b7d-210">Image</span><span class="sxs-lookup"><span data-stu-id="d9b7d-210">Image</span></span>|  
|<span data-ttu-id="d9b7d-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="d9b7d-211">SysPager</span></span>|<span data-ttu-id="d9b7d-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="d9b7d-212">Spinner</span></span>|  
|<span data-ttu-id="d9b7d-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-213">SysDateTimePick32</span></span>|<span data-ttu-id="d9b7d-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="d9b7d-214">Custom</span></span>|  
|<span data-ttu-id="d9b7d-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="d9b7d-215">SysMonthCal32</span></span>|<span data-ttu-id="d9b7d-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="d9b7d-216">Calendar</span></span>|  
|<span data-ttu-id="d9b7d-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="d9b7d-217">MS_WINNOTE</span></span>|<span data-ttu-id="d9b7d-218">Okna</span><span class="sxs-lookup"><span data-stu-id="d9b7d-218">Tooltip</span></span>|  
|<span data-ttu-id="d9b7d-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="d9b7d-219">VBBubble</span></span>|<span data-ttu-id="d9b7d-220">Okna</span><span class="sxs-lookup"><span data-stu-id="d9b7d-220">Tooltip</span></span>|  
|<span data-ttu-id="d9b7d-221">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="d9b7d-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="d9b7d-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="d9b7d-222">Slider</span></span>|  
|<span data-ttu-id="d9b7d-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="d9b7d-223">SuperGrid</span></span>|<span data-ttu-id="d9b7d-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="d9b7d-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="d9b7d-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9b7d-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="d9b7d-226">Ovládací prvky model Windows Forms jsou zpřístupněny prostřednictvím poskytovatelů na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] straně klienta v knihovně UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d9b7d-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d9b7d-228">Obvykle jsou model Windows Forms ovládací prvky, které jsou spravované obálky [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] pro běžné ovládací prvky, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporovány nástrojem.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d9b7d-229">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d9b7d-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="d9b7d-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="d9b7d-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="d9b7d-231">Button</span></span>|  
|<span data-ttu-id="d9b7d-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-232">CheckBox</span></span>|  
|<span data-ttu-id="d9b7d-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-233">CheckedListBox</span></span>|  
|<span data-ttu-id="d9b7d-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-234">ColorDialog</span></span>|  
|<span data-ttu-id="d9b7d-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-235">ComboBox</span></span>|  
|<span data-ttu-id="d9b7d-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="d9b7d-236">FolderBrowser</span></span>|  
|<span data-ttu-id="d9b7d-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-237">FontDialog</span></span>|  
|<span data-ttu-id="d9b7d-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-238">GroupBox</span></span>|  
|<span data-ttu-id="d9b7d-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-239">HscrollBar</span></span>|  
|<span data-ttu-id="d9b7d-240">Obrázků</span><span class="sxs-lookup"><span data-stu-id="d9b7d-240">ImageList</span></span>|  
|<span data-ttu-id="d9b7d-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="d9b7d-241">Label</span></span>|  
|<span data-ttu-id="d9b7d-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-242">ListBox</span></span>|  
|<span data-ttu-id="d9b7d-243">ListView</span><span class="sxs-lookup"><span data-stu-id="d9b7d-243">ListView</span></span>|  
|<span data-ttu-id="d9b7d-244">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="d9b7d-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="d9b7d-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-245">MonthCalendar</span></span>|  
|<span data-ttu-id="d9b7d-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="d9b7d-246">NotifyIcon</span></span>|  
|<span data-ttu-id="d9b7d-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="d9b7d-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="d9b7d-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-249">PrintDialog</span></span>|  
|<span data-ttu-id="d9b7d-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-250">ProgressBar</span></span>|  
|<span data-ttu-id="d9b7d-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d9b7d-251">RadioButton</span></span>|  
|<span data-ttu-id="d9b7d-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-252">RichTextBox</span></span>|  
|<span data-ttu-id="d9b7d-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="d9b7d-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="d9b7d-254">ScrollableControl</span></span>|  
|<span data-ttu-id="d9b7d-255">Komponentu</span><span class="sxs-lookup"><span data-stu-id="d9b7d-255">SoundPlayer</span></span>|  
|<span data-ttu-id="d9b7d-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-256">StatusBar</span></span>|  
|<span data-ttu-id="d9b7d-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="d9b7d-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="d9b7d-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-258">TextBox</span></span>|  
|<span data-ttu-id="d9b7d-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="d9b7d-259">Timer</span></span>|  
|<span data-ttu-id="d9b7d-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="d9b7d-260">Toolbar</span></span>|  
|<span data-ttu-id="d9b7d-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="d9b7d-261">ToolTip</span></span>|  
|<span data-ttu-id="d9b7d-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-262">TrackBar</span></span>|  
|<span data-ttu-id="d9b7d-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="d9b7d-263">TreeView</span></span>|  
|<span data-ttu-id="d9b7d-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="d9b7d-264">VscrollBar</span></span>|  
|<span data-ttu-id="d9b7d-265">Navig</span><span class="sxs-lookup"><span data-stu-id="d9b7d-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="d9b7d-266">Následující ovládací prvky jsou k [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dispozici pouze prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="d9b7d-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d9b7d-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="d9b7d-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9b7d-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="d9b7d-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="d9b7d-269">BindingSource</span></span>|  
|<span data-ttu-id="d9b7d-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d9b7d-270">DataGrid</span></span>|  
|<span data-ttu-id="d9b7d-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="d9b7d-271">DataGridView</span></span>|  
|<span data-ttu-id="d9b7d-272">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="d9b7d-272">DataNavigator</span></span>|  
|<span data-ttu-id="d9b7d-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="d9b7d-273">DomainUpDown</span></span>|  
|<span data-ttu-id="d9b7d-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="d9b7d-274">ErrorProvider</span></span>|  
|<span data-ttu-id="d9b7d-275">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="d9b7d-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="d9b7d-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="d9b7d-276">Form</span></span>|  
|<span data-ttu-id="d9b7d-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="d9b7d-277">LinkLabel</span></span>|  
|<span data-ttu-id="d9b7d-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="d9b7d-278">HelpProvider</span></span>|  
|<span data-ttu-id="d9b7d-279">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="d9b7d-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="d9b7d-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="d9b7d-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="d9b7d-281">NumericUpDown</span></span>|  
|<span data-ttu-id="d9b7d-282">Panel</span><span class="sxs-lookup"><span data-stu-id="d9b7d-282">Panel</span></span>|  
|<span data-ttu-id="d9b7d-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="d9b7d-283">PictureBox</span></span>|  
|<span data-ttu-id="d9b7d-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="d9b7d-284">PrintDocument</span></span>|  
|<span data-ttu-id="d9b7d-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="d9b7d-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="d9b7d-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="d9b7d-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="d9b7d-287">Mřížky</span><span class="sxs-lookup"><span data-stu-id="d9b7d-287">PropertyGrid</span></span>|  
|<span data-ttu-id="d9b7d-288">Type</span><span class="sxs-lookup"><span data-stu-id="d9b7d-288">UserControl</span></span>|  
|<span data-ttu-id="d9b7d-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d9b7d-289">ToolStrip</span></span>|  
|<span data-ttu-id="d9b7d-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d9b7d-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="d9b7d-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="d9b7d-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="d9b7d-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="d9b7d-292">Splitter</span></span>|  
|<span data-ttu-id="d9b7d-293">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="d9b7d-293">RaftingContainer</span></span>|  
|<span data-ttu-id="d9b7d-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="d9b7d-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9b7d-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9b7d-295">See also</span></span>

- [<span data-ttu-id="d9b7d-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9b7d-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
