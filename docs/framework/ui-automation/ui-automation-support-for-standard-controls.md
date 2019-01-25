---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9c5e4133a3bc1f019ada00299df929c2e3915880
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726582"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="f01fc-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f01fc-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="f01fc-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f01fc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f01fc-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f01fc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f01fc-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="f01fc-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="f01fc-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="f01fc-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="f01fc-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f01fc-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="f01fc-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f01fc-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="f01fc-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="f01fc-109">Win32 Controls</span></span>  
 <span data-ttu-id="f01fc-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="f01fc-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="f01fc-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="f01fc-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="f01fc-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="f01fc-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="f01fc-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f01fc-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="f01fc-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="f01fc-114">Class name</span></span>|<span data-ttu-id="f01fc-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f01fc-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="f01fc-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-116">Button</span></span>|<span data-ttu-id="f01fc-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-117">Button</span></span>|  
|<span data-ttu-id="f01fc-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-118">Button</span></span>|<span data-ttu-id="f01fc-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f01fc-119">RadioButton</span></span>|  
|<span data-ttu-id="f01fc-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-120">Button</span></span>|<span data-ttu-id="f01fc-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="f01fc-121">Group</span></span>|  
|<span data-ttu-id="f01fc-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-122">Button</span></span>|<span data-ttu-id="f01fc-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-123">CheckBox</span></span>|  
|<span data-ttu-id="f01fc-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-124">Button</span></span>|<span data-ttu-id="f01fc-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="f01fc-125">Hyperlink</span></span>|  
|<span data-ttu-id="f01fc-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-126">Button</span></span>|<span data-ttu-id="f01fc-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="f01fc-127">SplitButton</span></span>|  
|<span data-ttu-id="f01fc-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-128">Button</span></span>|<span data-ttu-id="f01fc-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-129">CheckBox</span></span>|  
|<span data-ttu-id="f01fc-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="f01fc-130">ComboBoxEx32</span></span>|<span data-ttu-id="f01fc-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-131">ComboBox</span></span>|  
|<span data-ttu-id="f01fc-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-132">ComboBox</span></span>|<span data-ttu-id="f01fc-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-133">ComboBox</span></span>|  
|<span data-ttu-id="f01fc-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="f01fc-134">Edit</span></span>|<span data-ttu-id="f01fc-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="f01fc-135">Document</span></span>|  
|<span data-ttu-id="f01fc-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="f01fc-136">Edit</span></span>|<span data-ttu-id="f01fc-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="f01fc-137">Edit</span></span>|  
|<span data-ttu-id="f01fc-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="f01fc-138">SysLink</span></span>|<span data-ttu-id="f01fc-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="f01fc-139">Hyperlink</span></span>|  
|<span data-ttu-id="f01fc-140">Static</span><span class="sxs-lookup"><span data-stu-id="f01fc-140">Static</span></span>|<span data-ttu-id="f01fc-141">Text</span><span class="sxs-lookup"><span data-stu-id="f01fc-141">Text</span></span>|  
|<span data-ttu-id="f01fc-142">Static</span><span class="sxs-lookup"><span data-stu-id="f01fc-142">Static</span></span>|<span data-ttu-id="f01fc-143">Image</span><span class="sxs-lookup"><span data-stu-id="f01fc-143">Image</span></span>|  
|<span data-ttu-id="f01fc-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="f01fc-144">SysIPAddress32</span></span>|<span data-ttu-id="f01fc-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="f01fc-145">Custom</span></span>|  
|<span data-ttu-id="f01fc-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="f01fc-146">SysHeader32</span></span>|<span data-ttu-id="f01fc-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="f01fc-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="f01fc-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="f01fc-148">SysListView32</span></span>|<span data-ttu-id="f01fc-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="f01fc-149">DataGrid</span></span>|  
|<span data-ttu-id="f01fc-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="f01fc-150">SysListView32</span></span>|<span data-ttu-id="f01fc-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="f01fc-151">List</span></span>|  
|<span data-ttu-id="f01fc-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-152">ListBox</span></span>|<span data-ttu-id="f01fc-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="f01fc-153">List</span></span>|  
|<span data-ttu-id="f01fc-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-154">ListBox</span></span>|<span data-ttu-id="f01fc-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="f01fc-155">ListItem</span></span>|  
|<span data-ttu-id="f01fc-156">#32768</span><span class="sxs-lookup"><span data-stu-id="f01fc-156">#32768</span></span>|<span data-ttu-id="f01fc-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="f01fc-157">Menu</span></span>|  
|<span data-ttu-id="f01fc-158">#32768</span><span class="sxs-lookup"><span data-stu-id="f01fc-158">#32768</span></span>|<span data-ttu-id="f01fc-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="f01fc-159">MenuItem</span></span>|  
|<span data-ttu-id="f01fc-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="f01fc-160">msctls_progress32</span></span>|<span data-ttu-id="f01fc-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-161">ProgressBar</span></span>|  
|<span data-ttu-id="f01fc-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="f01fc-162">RichEdit</span></span>|<span data-ttu-id="f01fc-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="f01fc-163">Document.</span></span> <span data-ttu-id="f01fc-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="f01fc-164">See note.</span></span>|  
|<span data-ttu-id="f01fc-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="f01fc-165">RichEdit20A</span></span>|<span data-ttu-id="f01fc-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="f01fc-166">Document</span></span>|  
|<span data-ttu-id="f01fc-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="f01fc-167">RichEdit20W</span></span>|<span data-ttu-id="f01fc-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="f01fc-168">Document</span></span>|  
|<span data-ttu-id="f01fc-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="f01fc-169">RichEdit50W</span></span>|<span data-ttu-id="f01fc-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="f01fc-170">Document</span></span>|  
|<span data-ttu-id="f01fc-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-171">ScrollBar</span></span>|<span data-ttu-id="f01fc-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="f01fc-172">Slider</span></span>|  
|<span data-ttu-id="f01fc-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="f01fc-173">msctls_trackbar32</span></span>|<span data-ttu-id="f01fc-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="f01fc-174">Slider</span></span>|  
|<span data-ttu-id="f01fc-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="f01fc-175">msctls_updown32</span></span>|<span data-ttu-id="f01fc-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="f01fc-176">Spinner</span></span>|  
|<span data-ttu-id="f01fc-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="f01fc-177">msctls_statusbar32</span></span>|<span data-ttu-id="f01fc-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-178">StatusBar</span></span>|  
|<span data-ttu-id="f01fc-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="f01fc-179">SysTabControl32</span></span>|<span data-ttu-id="f01fc-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="f01fc-180">Tab</span></span>|  
|<span data-ttu-id="f01fc-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="f01fc-181">SysTabControl32</span></span>|<span data-ttu-id="f01fc-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="f01fc-182">TabItem</span></span>|  
|<span data-ttu-id="f01fc-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-183">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-184">ToolBar</span></span>|  
|<span data-ttu-id="f01fc-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-185">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="f01fc-186">MenuItem</span></span>|  
|<span data-ttu-id="f01fc-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-187">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-188">Button</span></span>|  
|<span data-ttu-id="f01fc-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-189">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-190">CheckBox</span></span>|  
|<span data-ttu-id="f01fc-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-191">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f01fc-192">RadioButton</span></span>|  
|<span data-ttu-id="f01fc-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-193">ToolbarWindow32</span></span>|<span data-ttu-id="f01fc-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="f01fc-194">Separator</span></span>|  
|<span data-ttu-id="f01fc-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="f01fc-195">tooltips_class32</span></span>|<span data-ttu-id="f01fc-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="f01fc-196">ToolTip</span></span>|  
|<span data-ttu-id="f01fc-197">#32774</span><span class="sxs-lookup"><span data-stu-id="f01fc-197">#32774</span></span>|<span data-ttu-id="f01fc-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="f01fc-198">ToolTip</span></span>|  
|<span data-ttu-id="f01fc-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="f01fc-199">ReBarWindow32</span></span>|<span data-ttu-id="f01fc-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="f01fc-200">Toolbar</span></span>|  
|<span data-ttu-id="f01fc-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="f01fc-201">SysTreeView32</span></span>|<span data-ttu-id="f01fc-202">Strom</span><span class="sxs-lookup"><span data-stu-id="f01fc-202">Tree</span></span>|  
|<span data-ttu-id="f01fc-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="f01fc-203">SysTreeView32</span></span>|<span data-ttu-id="f01fc-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="f01fc-204">TreeItem</span></span>|  
  
 <span data-ttu-id="f01fc-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="f01fc-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="f01fc-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="f01fc-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="f01fc-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="f01fc-207">Class name</span></span>|<span data-ttu-id="f01fc-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f01fc-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="f01fc-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="f01fc-209">SysAnimate32</span></span>|<span data-ttu-id="f01fc-210">Image</span><span class="sxs-lookup"><span data-stu-id="f01fc-210">Image</span></span>|  
|<span data-ttu-id="f01fc-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="f01fc-211">SysPager</span></span>|<span data-ttu-id="f01fc-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="f01fc-212">Spinner</span></span>|  
|<span data-ttu-id="f01fc-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="f01fc-213">SysDateTimePick32</span></span>|<span data-ttu-id="f01fc-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="f01fc-214">Custom</span></span>|  
|<span data-ttu-id="f01fc-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="f01fc-215">SysMonthCal32</span></span>|<span data-ttu-id="f01fc-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="f01fc-216">Calendar</span></span>|  
|<span data-ttu-id="f01fc-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="f01fc-217">MS_WINNOTE</span></span>|<span data-ttu-id="f01fc-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="f01fc-218">Tooltip</span></span>|  
|<span data-ttu-id="f01fc-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="f01fc-219">VBBubble</span></span>|<span data-ttu-id="f01fc-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="f01fc-220">Tooltip</span></span>|  
|<span data-ttu-id="f01fc-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="f01fc-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="f01fc-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="f01fc-222">Slider</span></span>|  
|<span data-ttu-id="f01fc-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="f01fc-223">SuperGrid</span></span>|<span data-ttu-id="f01fc-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="f01fc-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="f01fc-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f01fc-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="f01fc-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="f01fc-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="f01fc-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="f01fc-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="f01fc-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f01fc-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="f01fc-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f01fc-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="f01fc-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="f01fc-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="f01fc-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="f01fc-231">Button</span></span>|  
|<span data-ttu-id="f01fc-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-232">CheckBox</span></span>|  
|<span data-ttu-id="f01fc-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-233">CheckedListBox</span></span>|  
|<span data-ttu-id="f01fc-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-234">ColorDialog</span></span>|  
|<span data-ttu-id="f01fc-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-235">ComboBox</span></span>|  
|<span data-ttu-id="f01fc-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="f01fc-236">FolderBrowser</span></span>|  
|<span data-ttu-id="f01fc-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-237">FontDialog</span></span>|  
|<span data-ttu-id="f01fc-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-238">GroupBox</span></span>|  
|<span data-ttu-id="f01fc-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-239">HscrollBar</span></span>|  
|<span data-ttu-id="f01fc-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="f01fc-240">ImageList</span></span>|  
|<span data-ttu-id="f01fc-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="f01fc-241">Label</span></span>|  
|<span data-ttu-id="f01fc-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-242">ListBox</span></span>|  
|<span data-ttu-id="f01fc-243">ListView</span><span class="sxs-lookup"><span data-stu-id="f01fc-243">ListView</span></span>|  
|<span data-ttu-id="f01fc-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="f01fc-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="f01fc-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f01fc-245">MonthCalendar</span></span>|  
|<span data-ttu-id="f01fc-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="f01fc-246">NotifyIcon</span></span>|  
|<span data-ttu-id="f01fc-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="f01fc-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="f01fc-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-249">PrintDialog</span></span>|  
|<span data-ttu-id="f01fc-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-250">ProgressBar</span></span>|  
|<span data-ttu-id="f01fc-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f01fc-251">RadioButton</span></span>|  
|<span data-ttu-id="f01fc-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-252">RichTextBox</span></span>|  
|<span data-ttu-id="f01fc-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="f01fc-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="f01fc-254">ScrollableControl</span></span>|  
|<span data-ttu-id="f01fc-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="f01fc-255">SoundPlayer</span></span>|  
|<span data-ttu-id="f01fc-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-256">StatusBar</span></span>|  
|<span data-ttu-id="f01fc-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="f01fc-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="f01fc-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-258">TextBox</span></span>|  
|<span data-ttu-id="f01fc-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="f01fc-259">Timer</span></span>|  
|<span data-ttu-id="f01fc-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="f01fc-260">Toolbar</span></span>|  
|<span data-ttu-id="f01fc-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="f01fc-261">ToolTip</span></span>|  
|<span data-ttu-id="f01fc-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-262">TrackBar</span></span>|  
|<span data-ttu-id="f01fc-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="f01fc-263">TreeView</span></span>|  
|<span data-ttu-id="f01fc-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="f01fc-264">VscrollBar</span></span>|  
|<span data-ttu-id="f01fc-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="f01fc-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="f01fc-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f01fc-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="f01fc-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f01fc-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="f01fc-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f01fc-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="f01fc-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="f01fc-269">BindingSource</span></span>|  
|<span data-ttu-id="f01fc-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="f01fc-270">DataGrid</span></span>|  
|<span data-ttu-id="f01fc-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01fc-271">DataGridView</span></span>|  
|<span data-ttu-id="f01fc-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="f01fc-272">DataNavigator</span></span>|  
|<span data-ttu-id="f01fc-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="f01fc-273">DomainUpDown</span></span>|  
|<span data-ttu-id="f01fc-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="f01fc-274">ErrorProvider</span></span>|  
|<span data-ttu-id="f01fc-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f01fc-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="f01fc-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="f01fc-276">Form</span></span>|  
|<span data-ttu-id="f01fc-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="f01fc-277">LinkLabel</span></span>|  
|<span data-ttu-id="f01fc-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="f01fc-278">HelpProvider</span></span>|  
|<span data-ttu-id="f01fc-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="f01fc-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="f01fc-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="f01fc-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="f01fc-281">NumericUpDown</span></span>|  
|<span data-ttu-id="f01fc-282">Panel</span><span class="sxs-lookup"><span data-stu-id="f01fc-282">Panel</span></span>|  
|<span data-ttu-id="f01fc-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="f01fc-283">PictureBox</span></span>|  
|<span data-ttu-id="f01fc-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="f01fc-284">PrintDocument</span></span>|  
|<span data-ttu-id="f01fc-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="f01fc-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="f01fc-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="f01fc-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="f01fc-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="f01fc-287">PropertyGrid</span></span>|  
|<span data-ttu-id="f01fc-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="f01fc-288">UserControl</span></span>|  
|<span data-ttu-id="f01fc-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f01fc-289">ToolStrip</span></span>|  
|<span data-ttu-id="f01fc-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f01fc-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="f01fc-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="f01fc-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="f01fc-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="f01fc-292">Splitter</span></span>|  
|<span data-ttu-id="f01fc-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="f01fc-293">RaftingContainer</span></span>|  
|<span data-ttu-id="f01fc-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="f01fc-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f01fc-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f01fc-295">See also</span></span>
- [<span data-ttu-id="f01fc-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f01fc-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
