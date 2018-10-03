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
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037336"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="2e409-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="2e409-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="2e409-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e409-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2e409-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="2e409-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2e409-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="2e409-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="2e409-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="2e409-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="2e409-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e409-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2e409-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e409-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="2e409-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="2e409-109">Win32 Controls</span></span>  
 <span data-ttu-id="2e409-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="2e409-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2e409-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e409-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2e409-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="2e409-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="2e409-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2e409-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2e409-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="2e409-114">Class name</span></span>|<span data-ttu-id="2e409-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2e409-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2e409-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-116">Button</span></span>|<span data-ttu-id="2e409-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-117">Button</span></span>|  
|<span data-ttu-id="2e409-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-118">Button</span></span>|<span data-ttu-id="2e409-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2e409-119">RadioButton</span></span>|  
|<span data-ttu-id="2e409-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-120">Button</span></span>|<span data-ttu-id="2e409-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="2e409-121">Group</span></span>|  
|<span data-ttu-id="2e409-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-122">Button</span></span>|<span data-ttu-id="2e409-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2e409-123">CheckBox</span></span>|  
|<span data-ttu-id="2e409-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-124">Button</span></span>|<span data-ttu-id="2e409-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="2e409-125">Hyperlink</span></span>|  
|<span data-ttu-id="2e409-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-126">Button</span></span>|<span data-ttu-id="2e409-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="2e409-127">SplitButton</span></span>|  
|<span data-ttu-id="2e409-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-128">Button</span></span>|<span data-ttu-id="2e409-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2e409-129">CheckBox</span></span>|  
|<span data-ttu-id="2e409-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="2e409-130">ComboBoxEx32</span></span>|<span data-ttu-id="2e409-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2e409-131">ComboBox</span></span>|  
|<span data-ttu-id="2e409-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2e409-132">ComboBox</span></span>|<span data-ttu-id="2e409-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2e409-133">ComboBox</span></span>|  
|<span data-ttu-id="2e409-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="2e409-134">Edit</span></span>|<span data-ttu-id="2e409-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="2e409-135">Document</span></span>|  
|<span data-ttu-id="2e409-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="2e409-136">Edit</span></span>|<span data-ttu-id="2e409-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="2e409-137">Edit</span></span>|  
|<span data-ttu-id="2e409-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="2e409-138">SysLink</span></span>|<span data-ttu-id="2e409-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="2e409-139">Hyperlink</span></span>|  
|<span data-ttu-id="2e409-140">Static</span><span class="sxs-lookup"><span data-stu-id="2e409-140">Static</span></span>|<span data-ttu-id="2e409-141">Text</span><span class="sxs-lookup"><span data-stu-id="2e409-141">Text</span></span>|  
|<span data-ttu-id="2e409-142">Static</span><span class="sxs-lookup"><span data-stu-id="2e409-142">Static</span></span>|<span data-ttu-id="2e409-143">Image</span><span class="sxs-lookup"><span data-stu-id="2e409-143">Image</span></span>|  
|<span data-ttu-id="2e409-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="2e409-144">SysIPAddress32</span></span>|<span data-ttu-id="2e409-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="2e409-145">Custom</span></span>|  
|<span data-ttu-id="2e409-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="2e409-146">SysHeader32</span></span>|<span data-ttu-id="2e409-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="2e409-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="2e409-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2e409-148">SysListView32</span></span>|<span data-ttu-id="2e409-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2e409-149">DataGrid</span></span>|  
|<span data-ttu-id="2e409-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2e409-150">SysListView32</span></span>|<span data-ttu-id="2e409-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="2e409-151">List</span></span>|  
|<span data-ttu-id="2e409-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="2e409-152">ListBox</span></span>|<span data-ttu-id="2e409-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="2e409-153">List</span></span>|  
|<span data-ttu-id="2e409-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="2e409-154">ListBox</span></span>|<span data-ttu-id="2e409-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="2e409-155">ListItem</span></span>|  
|<span data-ttu-id="2e409-156">#32768</span><span class="sxs-lookup"><span data-stu-id="2e409-156">#32768</span></span>|<span data-ttu-id="2e409-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="2e409-157">Menu</span></span>|  
|<span data-ttu-id="2e409-158">#32768</span><span class="sxs-lookup"><span data-stu-id="2e409-158">#32768</span></span>|<span data-ttu-id="2e409-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="2e409-159">MenuItem</span></span>|  
|<span data-ttu-id="2e409-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="2e409-160">msctls_progress32</span></span>|<span data-ttu-id="2e409-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2e409-161">ProgressBar</span></span>|  
|<span data-ttu-id="2e409-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="2e409-162">RichEdit</span></span>|<span data-ttu-id="2e409-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="2e409-163">Document.</span></span> <span data-ttu-id="2e409-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="2e409-164">See note.</span></span>|  
|<span data-ttu-id="2e409-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="2e409-165">RichEdit20A</span></span>|<span data-ttu-id="2e409-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="2e409-166">Document</span></span>|  
|<span data-ttu-id="2e409-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="2e409-167">RichEdit20W</span></span>|<span data-ttu-id="2e409-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="2e409-168">Document</span></span>|  
|<span data-ttu-id="2e409-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="2e409-169">RichEdit50W</span></span>|<span data-ttu-id="2e409-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="2e409-170">Document</span></span>|  
|<span data-ttu-id="2e409-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2e409-171">ScrollBar</span></span>|<span data-ttu-id="2e409-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="2e409-172">Slider</span></span>|  
|<span data-ttu-id="2e409-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="2e409-173">msctls_trackbar32</span></span>|<span data-ttu-id="2e409-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="2e409-174">Slider</span></span>|  
|<span data-ttu-id="2e409-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="2e409-175">msctls_updown32</span></span>|<span data-ttu-id="2e409-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="2e409-176">Spinner</span></span>|  
|<span data-ttu-id="2e409-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="2e409-177">msctls_statusbar32</span></span>|<span data-ttu-id="2e409-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2e409-178">StatusBar</span></span>|  
|<span data-ttu-id="2e409-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2e409-179">SysTabControl32</span></span>|<span data-ttu-id="2e409-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="2e409-180">Tab</span></span>|  
|<span data-ttu-id="2e409-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2e409-181">SysTabControl32</span></span>|<span data-ttu-id="2e409-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="2e409-182">TabItem</span></span>|  
|<span data-ttu-id="2e409-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-183">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="2e409-184">ToolBar</span></span>|  
|<span data-ttu-id="2e409-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-185">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="2e409-186">MenuItem</span></span>|  
|<span data-ttu-id="2e409-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-187">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-188">Button</span></span>|  
|<span data-ttu-id="2e409-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-189">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2e409-190">CheckBox</span></span>|  
|<span data-ttu-id="2e409-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-191">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2e409-192">RadioButton</span></span>|  
|<span data-ttu-id="2e409-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-193">ToolbarWindow32</span></span>|<span data-ttu-id="2e409-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="2e409-194">Separator</span></span>|  
|<span data-ttu-id="2e409-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="2e409-195">tooltips_class32</span></span>|<span data-ttu-id="2e409-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="2e409-196">ToolTip</span></span>|  
|<span data-ttu-id="2e409-197">#32774</span><span class="sxs-lookup"><span data-stu-id="2e409-197">#32774</span></span>|<span data-ttu-id="2e409-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="2e409-198">ToolTip</span></span>|  
|<span data-ttu-id="2e409-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="2e409-199">ReBarWindow32</span></span>|<span data-ttu-id="2e409-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="2e409-200">Toolbar</span></span>|  
|<span data-ttu-id="2e409-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2e409-201">SysTreeView32</span></span>|<span data-ttu-id="2e409-202">Strom</span><span class="sxs-lookup"><span data-stu-id="2e409-202">Tree</span></span>|  
|<span data-ttu-id="2e409-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2e409-203">SysTreeView32</span></span>|<span data-ttu-id="2e409-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="2e409-204">TreeItem</span></span>|  
  
 <span data-ttu-id="2e409-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="2e409-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="2e409-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2e409-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="2e409-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="2e409-207">Class name</span></span>|<span data-ttu-id="2e409-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2e409-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2e409-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="2e409-209">SysAnimate32</span></span>|<span data-ttu-id="2e409-210">Image</span><span class="sxs-lookup"><span data-stu-id="2e409-210">Image</span></span>|  
|<span data-ttu-id="2e409-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="2e409-211">SysPager</span></span>|<span data-ttu-id="2e409-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="2e409-212">Spinner</span></span>|  
|<span data-ttu-id="2e409-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="2e409-213">SysDateTimePick32</span></span>|<span data-ttu-id="2e409-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="2e409-214">Custom</span></span>|  
|<span data-ttu-id="2e409-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="2e409-215">SysMonthCal32</span></span>|<span data-ttu-id="2e409-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="2e409-216">Calendar</span></span>|  
|<span data-ttu-id="2e409-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="2e409-217">MS_WINNOTE</span></span>|<span data-ttu-id="2e409-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="2e409-218">Tooltip</span></span>|  
|<span data-ttu-id="2e409-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="2e409-219">VBBubble</span></span>|<span data-ttu-id="2e409-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="2e409-220">Tooltip</span></span>|  
|<span data-ttu-id="2e409-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="2e409-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="2e409-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="2e409-222">Slider</span></span>|  
|<span data-ttu-id="2e409-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="2e409-223">SuperGrid</span></span>|<span data-ttu-id="2e409-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="2e409-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="2e409-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e409-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="2e409-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="2e409-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2e409-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e409-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2e409-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e409-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2e409-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2e409-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2e409-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="2e409-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="2e409-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="2e409-231">Button</span></span>|  
|<span data-ttu-id="2e409-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2e409-232">CheckBox</span></span>|  
|<span data-ttu-id="2e409-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="2e409-233">CheckedListBox</span></span>|  
|<span data-ttu-id="2e409-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-234">ColorDialog</span></span>|  
|<span data-ttu-id="2e409-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2e409-235">ComboBox</span></span>|  
|<span data-ttu-id="2e409-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="2e409-236">FolderBrowser</span></span>|  
|<span data-ttu-id="2e409-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-237">FontDialog</span></span>|  
|<span data-ttu-id="2e409-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="2e409-238">GroupBox</span></span>|  
|<span data-ttu-id="2e409-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="2e409-239">HscrollBar</span></span>|  
|<span data-ttu-id="2e409-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="2e409-240">ImageList</span></span>|  
|<span data-ttu-id="2e409-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="2e409-241">Label</span></span>|  
|<span data-ttu-id="2e409-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="2e409-242">ListBox</span></span>|  
|<span data-ttu-id="2e409-243">ListView</span><span class="sxs-lookup"><span data-stu-id="2e409-243">ListView</span></span>|  
|<span data-ttu-id="2e409-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="2e409-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="2e409-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="2e409-245">MonthCalendar</span></span>|  
|<span data-ttu-id="2e409-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="2e409-246">NotifyIcon</span></span>|  
|<span data-ttu-id="2e409-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="2e409-248">Objekt PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="2e409-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-249">PrintDialog</span></span>|  
|<span data-ttu-id="2e409-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2e409-250">ProgressBar</span></span>|  
|<span data-ttu-id="2e409-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2e409-251">RadioButton</span></span>|  
|<span data-ttu-id="2e409-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2e409-252">RichTextBox</span></span>|  
|<span data-ttu-id="2e409-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2e409-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="2e409-254">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="2e409-254">ScrollableControl</span></span>|  
|<span data-ttu-id="2e409-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="2e409-255">SoundPlayer</span></span>|  
|<span data-ttu-id="2e409-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2e409-256">StatusBar</span></span>|  
|<span data-ttu-id="2e409-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="2e409-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="2e409-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="2e409-258">TextBox</span></span>|  
|<span data-ttu-id="2e409-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="2e409-259">Timer</span></span>|  
|<span data-ttu-id="2e409-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="2e409-260">Toolbar</span></span>|  
|<span data-ttu-id="2e409-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="2e409-261">ToolTip</span></span>|  
|<span data-ttu-id="2e409-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="2e409-262">TrackBar</span></span>|  
|<span data-ttu-id="2e409-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="2e409-263">TreeView</span></span>|  
|<span data-ttu-id="2e409-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="2e409-264">VscrollBar</span></span>|  
|<span data-ttu-id="2e409-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="2e409-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="2e409-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e409-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="2e409-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2e409-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="2e409-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2e409-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="2e409-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="2e409-269">BindingSource</span></span>|  
|<span data-ttu-id="2e409-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2e409-270">DataGrid</span></span>|  
|<span data-ttu-id="2e409-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="2e409-271">DataGridView</span></span>|  
|<span data-ttu-id="2e409-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="2e409-272">DataNavigator</span></span>|  
|<span data-ttu-id="2e409-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="2e409-273">DomainUpDown</span></span>|  
|<span data-ttu-id="2e409-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="2e409-274">ErrorProvider</span></span>|  
|<span data-ttu-id="2e409-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2e409-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="2e409-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="2e409-276">Form</span></span>|  
|<span data-ttu-id="2e409-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="2e409-277">LinkLabel</span></span>|  
|<span data-ttu-id="2e409-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="2e409-278">HelpProvider</span></span>|  
|<span data-ttu-id="2e409-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="2e409-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="2e409-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="2e409-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="2e409-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="2e409-281">NumericUpDown</span></span>|  
|<span data-ttu-id="2e409-282">Panel</span><span class="sxs-lookup"><span data-stu-id="2e409-282">Panel</span></span>|  
|<span data-ttu-id="2e409-283">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="2e409-283">PictureBox</span></span>|  
|<span data-ttu-id="2e409-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="2e409-284">PrintDocument</span></span>|  
|<span data-ttu-id="2e409-285">Printpreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2e409-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="2e409-286">Printpreview – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="2e409-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="2e409-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="2e409-287">PropertyGrid</span></span>|  
|<span data-ttu-id="2e409-288">Uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2e409-288">UserControl</span></span>|  
|<span data-ttu-id="2e409-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2e409-289">ToolStrip</span></span>|  
|<span data-ttu-id="2e409-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2e409-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="2e409-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="2e409-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="2e409-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="2e409-292">Splitter</span></span>|  
|<span data-ttu-id="2e409-293">Prvku RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="2e409-293">RaftingContainer</span></span>|  
|<span data-ttu-id="2e409-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="2e409-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e409-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e409-295">See Also</span></span>  
 [<span data-ttu-id="2e409-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e409-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
