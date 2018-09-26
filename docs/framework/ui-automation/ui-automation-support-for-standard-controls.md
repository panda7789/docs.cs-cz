---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68fa7753be76b0681c40e540e86b11c89e7a8ca1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193878"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="a6467-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="a6467-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="a6467-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a6467-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a6467-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a6467-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a6467-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="a6467-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="a6467-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a6467-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="a6467-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6467-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a6467-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6467-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="a6467-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="a6467-109">Win32 Controls</span></span>  
 <span data-ttu-id="a6467-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="a6467-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a6467-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6467-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a6467-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="a6467-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="a6467-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a6467-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a6467-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a6467-114">Class name</span></span>|<span data-ttu-id="a6467-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a6467-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a6467-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-116">Button</span></span>|<span data-ttu-id="a6467-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-117">Button</span></span>|  
|<span data-ttu-id="a6467-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-118">Button</span></span>|<span data-ttu-id="a6467-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a6467-119">RadioButton</span></span>|  
|<span data-ttu-id="a6467-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-120">Button</span></span>|<span data-ttu-id="a6467-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="a6467-121">Group</span></span>|  
|<span data-ttu-id="a6467-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-122">Button</span></span>|<span data-ttu-id="a6467-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a6467-123">CheckBox</span></span>|  
|<span data-ttu-id="a6467-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-124">Button</span></span>|<span data-ttu-id="a6467-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="a6467-125">Hyperlink</span></span>|  
|<span data-ttu-id="a6467-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-126">Button</span></span>|<span data-ttu-id="a6467-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="a6467-127">SplitButton</span></span>|  
|<span data-ttu-id="a6467-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-128">Button</span></span>|<span data-ttu-id="a6467-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a6467-129">CheckBox</span></span>|  
|<span data-ttu-id="a6467-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="a6467-130">ComboBoxEx32</span></span>|<span data-ttu-id="a6467-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a6467-131">ComboBox</span></span>|  
|<span data-ttu-id="a6467-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a6467-132">ComboBox</span></span>|<span data-ttu-id="a6467-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a6467-133">ComboBox</span></span>|  
|<span data-ttu-id="a6467-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="a6467-134">Edit</span></span>|<span data-ttu-id="a6467-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="a6467-135">Document</span></span>|  
|<span data-ttu-id="a6467-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="a6467-136">Edit</span></span>|<span data-ttu-id="a6467-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="a6467-137">Edit</span></span>|  
|<span data-ttu-id="a6467-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="a6467-138">SysLink</span></span>|<span data-ttu-id="a6467-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="a6467-139">Hyperlink</span></span>|  
|<span data-ttu-id="a6467-140">Static</span><span class="sxs-lookup"><span data-stu-id="a6467-140">Static</span></span>|<span data-ttu-id="a6467-141">Text</span><span class="sxs-lookup"><span data-stu-id="a6467-141">Text</span></span>|  
|<span data-ttu-id="a6467-142">Static</span><span class="sxs-lookup"><span data-stu-id="a6467-142">Static</span></span>|<span data-ttu-id="a6467-143">Image</span><span class="sxs-lookup"><span data-stu-id="a6467-143">Image</span></span>|  
|<span data-ttu-id="a6467-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="a6467-144">SysIPAddress32</span></span>|<span data-ttu-id="a6467-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a6467-145">Custom</span></span>|  
|<span data-ttu-id="a6467-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="a6467-146">SysHeader32</span></span>|<span data-ttu-id="a6467-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="a6467-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="a6467-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a6467-148">SysListView32</span></span>|<span data-ttu-id="a6467-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a6467-149">DataGrid</span></span>|  
|<span data-ttu-id="a6467-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a6467-150">SysListView32</span></span>|<span data-ttu-id="a6467-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="a6467-151">List</span></span>|  
|<span data-ttu-id="a6467-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="a6467-152">ListBox</span></span>|<span data-ttu-id="a6467-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="a6467-153">List</span></span>|  
|<span data-ttu-id="a6467-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="a6467-154">ListBox</span></span>|<span data-ttu-id="a6467-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="a6467-155">ListItem</span></span>|  
|<span data-ttu-id="a6467-156">#32768</span><span class="sxs-lookup"><span data-stu-id="a6467-156">#32768</span></span>|<span data-ttu-id="a6467-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="a6467-157">Menu</span></span>|  
|<span data-ttu-id="a6467-158">#32768</span><span class="sxs-lookup"><span data-stu-id="a6467-158">#32768</span></span>|<span data-ttu-id="a6467-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="a6467-159">MenuItem</span></span>|  
|<span data-ttu-id="a6467-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="a6467-160">msctls_progress32</span></span>|<span data-ttu-id="a6467-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a6467-161">ProgressBar</span></span>|  
|<span data-ttu-id="a6467-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="a6467-162">RichEdit</span></span>|<span data-ttu-id="a6467-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="a6467-163">Document.</span></span> <span data-ttu-id="a6467-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="a6467-164">See note.</span></span>|  
|<span data-ttu-id="a6467-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="a6467-165">RichEdit20A</span></span>|<span data-ttu-id="a6467-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="a6467-166">Document</span></span>|  
|<span data-ttu-id="a6467-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="a6467-167">RichEdit20W</span></span>|<span data-ttu-id="a6467-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="a6467-168">Document</span></span>|  
|<span data-ttu-id="a6467-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="a6467-169">RichEdit50W</span></span>|<span data-ttu-id="a6467-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="a6467-170">Document</span></span>|  
|<span data-ttu-id="a6467-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="a6467-171">ScrollBar</span></span>|<span data-ttu-id="a6467-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a6467-172">Slider</span></span>|  
|<span data-ttu-id="a6467-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="a6467-173">msctls_trackbar32</span></span>|<span data-ttu-id="a6467-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a6467-174">Slider</span></span>|  
|<span data-ttu-id="a6467-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="a6467-175">msctls_updown32</span></span>|<span data-ttu-id="a6467-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="a6467-176">Spinner</span></span>|  
|<span data-ttu-id="a6467-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="a6467-177">msctls_statusbar32</span></span>|<span data-ttu-id="a6467-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a6467-178">StatusBar</span></span>|  
|<span data-ttu-id="a6467-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a6467-179">SysTabControl32</span></span>|<span data-ttu-id="a6467-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="a6467-180">Tab</span></span>|  
|<span data-ttu-id="a6467-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a6467-181">SysTabControl32</span></span>|<span data-ttu-id="a6467-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="a6467-182">TabItem</span></span>|  
|<span data-ttu-id="a6467-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-183">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="a6467-184">ToolBar</span></span>|  
|<span data-ttu-id="a6467-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-185">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="a6467-186">MenuItem</span></span>|  
|<span data-ttu-id="a6467-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-187">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-188">Button</span></span>|  
|<span data-ttu-id="a6467-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-189">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a6467-190">CheckBox</span></span>|  
|<span data-ttu-id="a6467-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-191">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a6467-192">RadioButton</span></span>|  
|<span data-ttu-id="a6467-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-193">ToolbarWindow32</span></span>|<span data-ttu-id="a6467-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a6467-194">Separator</span></span>|  
|<span data-ttu-id="a6467-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="a6467-195">tooltips_class32</span></span>|<span data-ttu-id="a6467-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a6467-196">ToolTip</span></span>|  
|<span data-ttu-id="a6467-197">#32774</span><span class="sxs-lookup"><span data-stu-id="a6467-197">#32774</span></span>|<span data-ttu-id="a6467-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a6467-198">ToolTip</span></span>|  
|<span data-ttu-id="a6467-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="a6467-199">ReBarWindow32</span></span>|<span data-ttu-id="a6467-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="a6467-200">Toolbar</span></span>|  
|<span data-ttu-id="a6467-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a6467-201">SysTreeView32</span></span>|<span data-ttu-id="a6467-202">Strom</span><span class="sxs-lookup"><span data-stu-id="a6467-202">Tree</span></span>|  
|<span data-ttu-id="a6467-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a6467-203">SysTreeView32</span></span>|<span data-ttu-id="a6467-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="a6467-204">TreeItem</span></span>|  
  
 <span data-ttu-id="a6467-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="a6467-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="a6467-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a6467-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="a6467-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a6467-207">Class name</span></span>|<span data-ttu-id="a6467-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a6467-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a6467-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="a6467-209">SysAnimate32</span></span>|<span data-ttu-id="a6467-210">Image</span><span class="sxs-lookup"><span data-stu-id="a6467-210">Image</span></span>|  
|<span data-ttu-id="a6467-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="a6467-211">SysPager</span></span>|<span data-ttu-id="a6467-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="a6467-212">Spinner</span></span>|  
|<span data-ttu-id="a6467-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="a6467-213">SysDateTimePick32</span></span>|<span data-ttu-id="a6467-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a6467-214">Custom</span></span>|  
|<span data-ttu-id="a6467-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="a6467-215">SysMonthCal32</span></span>|<span data-ttu-id="a6467-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="a6467-216">Calendar</span></span>|  
|<span data-ttu-id="a6467-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="a6467-217">MS_WINNOTE</span></span>|<span data-ttu-id="a6467-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="a6467-218">Tooltip</span></span>|  
|<span data-ttu-id="a6467-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="a6467-219">VBBubble</span></span>|<span data-ttu-id="a6467-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="a6467-220">Tooltip</span></span>|  
|<span data-ttu-id="a6467-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="a6467-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="a6467-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a6467-222">Slider</span></span>|  
|<span data-ttu-id="a6467-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="a6467-223">SuperGrid</span></span>|<span data-ttu-id="a6467-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a6467-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="a6467-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6467-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="a6467-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="a6467-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a6467-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6467-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a6467-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6467-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a6467-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a6467-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a6467-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a6467-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="a6467-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a6467-231">Button</span></span>|  
|<span data-ttu-id="a6467-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a6467-232">CheckBox</span></span>|  
|<span data-ttu-id="a6467-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a6467-233">CheckedListBox</span></span>|  
|<span data-ttu-id="a6467-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-234">ColorDialog</span></span>|  
|<span data-ttu-id="a6467-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a6467-235">ComboBox</span></span>|  
|<span data-ttu-id="a6467-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="a6467-236">FolderBrowser</span></span>|  
|<span data-ttu-id="a6467-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-237">FontDialog</span></span>|  
|<span data-ttu-id="a6467-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="a6467-238">GroupBox</span></span>|  
|<span data-ttu-id="a6467-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="a6467-239">HscrollBar</span></span>|  
|<span data-ttu-id="a6467-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="a6467-240">ImageList</span></span>|  
|<span data-ttu-id="a6467-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="a6467-241">Label</span></span>|  
|<span data-ttu-id="a6467-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="a6467-242">ListBox</span></span>|  
|<span data-ttu-id="a6467-243">ListView</span><span class="sxs-lookup"><span data-stu-id="a6467-243">ListView</span></span>|  
|<span data-ttu-id="a6467-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="a6467-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="a6467-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="a6467-245">MonthCalendar</span></span>|  
|<span data-ttu-id="a6467-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="a6467-246">NotifyIcon</span></span>|  
|<span data-ttu-id="a6467-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="a6467-248">Objekt PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="a6467-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-249">PrintDialog</span></span>|  
|<span data-ttu-id="a6467-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a6467-250">ProgressBar</span></span>|  
|<span data-ttu-id="a6467-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a6467-251">RadioButton</span></span>|  
|<span data-ttu-id="a6467-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="a6467-252">RichTextBox</span></span>|  
|<span data-ttu-id="a6467-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="a6467-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="a6467-254">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="a6467-254">ScrollableControl</span></span>|  
|<span data-ttu-id="a6467-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="a6467-255">SoundPlayer</span></span>|  
|<span data-ttu-id="a6467-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a6467-256">StatusBar</span></span>|  
|<span data-ttu-id="a6467-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="a6467-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="a6467-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="a6467-258">TextBox</span></span>|  
|<span data-ttu-id="a6467-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="a6467-259">Timer</span></span>|  
|<span data-ttu-id="a6467-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="a6467-260">Toolbar</span></span>|  
|<span data-ttu-id="a6467-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a6467-261">ToolTip</span></span>|  
|<span data-ttu-id="a6467-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="a6467-262">TrackBar</span></span>|  
|<span data-ttu-id="a6467-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="a6467-263">TreeView</span></span>|  
|<span data-ttu-id="a6467-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="a6467-264">VscrollBar</span></span>|  
|<span data-ttu-id="a6467-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="a6467-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="a6467-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6467-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="a6467-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a6467-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="a6467-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a6467-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="a6467-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="a6467-269">BindingSource</span></span>|  
|<span data-ttu-id="a6467-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a6467-270">DataGrid</span></span>|  
|<span data-ttu-id="a6467-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="a6467-271">DataGridView</span></span>|  
|<span data-ttu-id="a6467-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="a6467-272">DataNavigator</span></span>|  
|<span data-ttu-id="a6467-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a6467-273">DomainUpDown</span></span>|  
|<span data-ttu-id="a6467-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="a6467-274">ErrorProvider</span></span>|  
|<span data-ttu-id="a6467-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a6467-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="a6467-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="a6467-276">Form</span></span>|  
|<span data-ttu-id="a6467-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a6467-277">LinkLabel</span></span>|  
|<span data-ttu-id="a6467-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="a6467-278">HelpProvider</span></span>|  
|<span data-ttu-id="a6467-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="a6467-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="a6467-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="a6467-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="a6467-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a6467-281">NumericUpDown</span></span>|  
|<span data-ttu-id="a6467-282">Panel</span><span class="sxs-lookup"><span data-stu-id="a6467-282">Panel</span></span>|  
|<span data-ttu-id="a6467-283">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="a6467-283">PictureBox</span></span>|  
|<span data-ttu-id="a6467-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="a6467-284">PrintDocument</span></span>|  
|<span data-ttu-id="a6467-285">Printpreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a6467-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="a6467-286">Printpreview – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="a6467-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="a6467-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a6467-287">PropertyGrid</span></span>|  
|<span data-ttu-id="a6467-288">Uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a6467-288">UserControl</span></span>|  
|<span data-ttu-id="a6467-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a6467-289">ToolStrip</span></span>|  
|<span data-ttu-id="a6467-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a6467-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="a6467-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="a6467-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="a6467-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="a6467-292">Splitter</span></span>|  
|<span data-ttu-id="a6467-293">Prvku RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="a6467-293">RaftingContainer</span></span>|  
|<span data-ttu-id="a6467-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="a6467-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6467-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6467-295">See Also</span></span>  
 [<span data-ttu-id="a6467-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6467-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
