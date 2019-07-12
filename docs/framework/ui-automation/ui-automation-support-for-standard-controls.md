---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 641fc3f8dfca3ff6506354c076b98cc88073a1b7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802121"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="efd61-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="efd61-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="efd61-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="efd61-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="efd61-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="efd61-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="efd61-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="efd61-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="efd61-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="efd61-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="efd61-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd61-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="efd61-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd61-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="efd61-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="efd61-109">Win32 Controls</span></span>  
 <span data-ttu-id="efd61-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="efd61-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="efd61-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="efd61-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="efd61-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="efd61-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="efd61-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="efd61-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="efd61-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="efd61-114">Class name</span></span>|<span data-ttu-id="efd61-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="efd61-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="efd61-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-116">Button</span></span>|<span data-ttu-id="efd61-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-117">Button</span></span>|  
|<span data-ttu-id="efd61-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-118">Button</span></span>|<span data-ttu-id="efd61-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="efd61-119">RadioButton</span></span>|  
|<span data-ttu-id="efd61-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-120">Button</span></span>|<span data-ttu-id="efd61-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="efd61-121">Group</span></span>|  
|<span data-ttu-id="efd61-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-122">Button</span></span>|<span data-ttu-id="efd61-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="efd61-123">CheckBox</span></span>|  
|<span data-ttu-id="efd61-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-124">Button</span></span>|<span data-ttu-id="efd61-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="efd61-125">Hyperlink</span></span>|  
|<span data-ttu-id="efd61-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-126">Button</span></span>|<span data-ttu-id="efd61-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="efd61-127">SplitButton</span></span>|  
|<span data-ttu-id="efd61-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-128">Button</span></span>|<span data-ttu-id="efd61-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="efd61-129">CheckBox</span></span>|  
|<span data-ttu-id="efd61-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="efd61-130">ComboBoxEx32</span></span>|<span data-ttu-id="efd61-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="efd61-131">ComboBox</span></span>|  
|<span data-ttu-id="efd61-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="efd61-132">ComboBox</span></span>|<span data-ttu-id="efd61-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="efd61-133">ComboBox</span></span>|  
|<span data-ttu-id="efd61-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="efd61-134">Edit</span></span>|<span data-ttu-id="efd61-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="efd61-135">Document</span></span>|  
|<span data-ttu-id="efd61-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="efd61-136">Edit</span></span>|<span data-ttu-id="efd61-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="efd61-137">Edit</span></span>|  
|<span data-ttu-id="efd61-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="efd61-138">SysLink</span></span>|<span data-ttu-id="efd61-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="efd61-139">Hyperlink</span></span>|  
|<span data-ttu-id="efd61-140">Static</span><span class="sxs-lookup"><span data-stu-id="efd61-140">Static</span></span>|<span data-ttu-id="efd61-141">Text</span><span class="sxs-lookup"><span data-stu-id="efd61-141">Text</span></span>|  
|<span data-ttu-id="efd61-142">Static</span><span class="sxs-lookup"><span data-stu-id="efd61-142">Static</span></span>|<span data-ttu-id="efd61-143">Image</span><span class="sxs-lookup"><span data-stu-id="efd61-143">Image</span></span>|  
|<span data-ttu-id="efd61-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="efd61-144">SysIPAddress32</span></span>|<span data-ttu-id="efd61-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="efd61-145">Custom</span></span>|  
|<span data-ttu-id="efd61-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="efd61-146">SysHeader32</span></span>|<span data-ttu-id="efd61-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="efd61-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="efd61-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="efd61-148">SysListView32</span></span>|<span data-ttu-id="efd61-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="efd61-149">DataGrid</span></span>|  
|<span data-ttu-id="efd61-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="efd61-150">SysListView32</span></span>|<span data-ttu-id="efd61-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="efd61-151">List</span></span>|  
|<span data-ttu-id="efd61-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="efd61-152">ListBox</span></span>|<span data-ttu-id="efd61-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="efd61-153">List</span></span>|  
|<span data-ttu-id="efd61-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="efd61-154">ListBox</span></span>|<span data-ttu-id="efd61-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="efd61-155">ListItem</span></span>|  
|<span data-ttu-id="efd61-156">#32768</span><span class="sxs-lookup"><span data-stu-id="efd61-156">#32768</span></span>|<span data-ttu-id="efd61-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="efd61-157">Menu</span></span>|  
|<span data-ttu-id="efd61-158">#32768</span><span class="sxs-lookup"><span data-stu-id="efd61-158">#32768</span></span>|<span data-ttu-id="efd61-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="efd61-159">MenuItem</span></span>|  
|<span data-ttu-id="efd61-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="efd61-160">msctls_progress32</span></span>|<span data-ttu-id="efd61-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="efd61-161">ProgressBar</span></span>|  
|<span data-ttu-id="efd61-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="efd61-162">RichEdit</span></span>|<span data-ttu-id="efd61-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="efd61-163">Document.</span></span> <span data-ttu-id="efd61-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="efd61-164">See note.</span></span>|  
|<span data-ttu-id="efd61-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="efd61-165">RichEdit20A</span></span>|<span data-ttu-id="efd61-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="efd61-166">Document</span></span>|  
|<span data-ttu-id="efd61-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="efd61-167">RichEdit20W</span></span>|<span data-ttu-id="efd61-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="efd61-168">Document</span></span>|  
|<span data-ttu-id="efd61-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="efd61-169">RichEdit50W</span></span>|<span data-ttu-id="efd61-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="efd61-170">Document</span></span>|  
|<span data-ttu-id="efd61-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="efd61-171">ScrollBar</span></span>|<span data-ttu-id="efd61-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="efd61-172">Slider</span></span>|  
|<span data-ttu-id="efd61-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="efd61-173">msctls_trackbar32</span></span>|<span data-ttu-id="efd61-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="efd61-174">Slider</span></span>|  
|<span data-ttu-id="efd61-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="efd61-175">msctls_updown32</span></span>|<span data-ttu-id="efd61-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="efd61-176">Spinner</span></span>|  
|<span data-ttu-id="efd61-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="efd61-177">msctls_statusbar32</span></span>|<span data-ttu-id="efd61-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="efd61-178">StatusBar</span></span>|  
|<span data-ttu-id="efd61-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="efd61-179">SysTabControl32</span></span>|<span data-ttu-id="efd61-180">Karta</span><span class="sxs-lookup"><span data-stu-id="efd61-180">Tab</span></span>|  
|<span data-ttu-id="efd61-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="efd61-181">SysTabControl32</span></span>|<span data-ttu-id="efd61-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="efd61-182">TabItem</span></span>|  
|<span data-ttu-id="efd61-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-183">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="efd61-184">ToolBar</span></span>|  
|<span data-ttu-id="efd61-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-185">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="efd61-186">MenuItem</span></span>|  
|<span data-ttu-id="efd61-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-187">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-188">Button</span></span>|  
|<span data-ttu-id="efd61-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-189">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="efd61-190">CheckBox</span></span>|  
|<span data-ttu-id="efd61-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-191">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="efd61-192">RadioButton</span></span>|  
|<span data-ttu-id="efd61-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-193">ToolbarWindow32</span></span>|<span data-ttu-id="efd61-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="efd61-194">Separator</span></span>|  
|<span data-ttu-id="efd61-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="efd61-195">tooltips_class32</span></span>|<span data-ttu-id="efd61-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="efd61-196">ToolTip</span></span>|  
|<span data-ttu-id="efd61-197">#32774</span><span class="sxs-lookup"><span data-stu-id="efd61-197">#32774</span></span>|<span data-ttu-id="efd61-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="efd61-198">ToolTip</span></span>|  
|<span data-ttu-id="efd61-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="efd61-199">ReBarWindow32</span></span>|<span data-ttu-id="efd61-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="efd61-200">Toolbar</span></span>|  
|<span data-ttu-id="efd61-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="efd61-201">SysTreeView32</span></span>|<span data-ttu-id="efd61-202">Strom</span><span class="sxs-lookup"><span data-stu-id="efd61-202">Tree</span></span>|  
|<span data-ttu-id="efd61-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="efd61-203">SysTreeView32</span></span>|<span data-ttu-id="efd61-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="efd61-204">TreeItem</span></span>|  
  
 <span data-ttu-id="efd61-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="efd61-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="efd61-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="efd61-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="efd61-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="efd61-207">Class name</span></span>|<span data-ttu-id="efd61-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="efd61-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="efd61-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="efd61-209">SysAnimate32</span></span>|<span data-ttu-id="efd61-210">Image</span><span class="sxs-lookup"><span data-stu-id="efd61-210">Image</span></span>|  
|<span data-ttu-id="efd61-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="efd61-211">SysPager</span></span>|<span data-ttu-id="efd61-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="efd61-212">Spinner</span></span>|  
|<span data-ttu-id="efd61-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="efd61-213">SysDateTimePick32</span></span>|<span data-ttu-id="efd61-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="efd61-214">Custom</span></span>|  
|<span data-ttu-id="efd61-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="efd61-215">SysMonthCal32</span></span>|<span data-ttu-id="efd61-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="efd61-216">Calendar</span></span>|  
|<span data-ttu-id="efd61-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="efd61-217">MS_WINNOTE</span></span>|<span data-ttu-id="efd61-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="efd61-218">Tooltip</span></span>|  
|<span data-ttu-id="efd61-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="efd61-219">VBBubble</span></span>|<span data-ttu-id="efd61-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="efd61-220">Tooltip</span></span>|  
|<span data-ttu-id="efd61-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="efd61-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="efd61-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="efd61-222">Slider</span></span>|  
|<span data-ttu-id="efd61-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="efd61-223">SuperGrid</span></span>|<span data-ttu-id="efd61-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="efd61-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="efd61-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="efd61-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="efd61-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="efd61-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="efd61-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="efd61-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="efd61-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd61-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="efd61-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="efd61-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="efd61-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="efd61-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="efd61-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="efd61-231">Button</span></span>|  
|<span data-ttu-id="efd61-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="efd61-232">CheckBox</span></span>|  
|<span data-ttu-id="efd61-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="efd61-233">CheckedListBox</span></span>|  
|<span data-ttu-id="efd61-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-234">ColorDialog</span></span>|  
|<span data-ttu-id="efd61-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="efd61-235">ComboBox</span></span>|  
|<span data-ttu-id="efd61-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="efd61-236">FolderBrowser</span></span>|  
|<span data-ttu-id="efd61-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-237">FontDialog</span></span>|  
|<span data-ttu-id="efd61-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="efd61-238">GroupBox</span></span>|  
|<span data-ttu-id="efd61-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="efd61-239">HscrollBar</span></span>|  
|<span data-ttu-id="efd61-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="efd61-240">ImageList</span></span>|  
|<span data-ttu-id="efd61-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="efd61-241">Label</span></span>|  
|<span data-ttu-id="efd61-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="efd61-242">ListBox</span></span>|  
|<span data-ttu-id="efd61-243">ListView</span><span class="sxs-lookup"><span data-stu-id="efd61-243">ListView</span></span>|  
|<span data-ttu-id="efd61-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="efd61-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="efd61-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="efd61-245">MonthCalendar</span></span>|  
|<span data-ttu-id="efd61-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="efd61-246">NotifyIcon</span></span>|  
|<span data-ttu-id="efd61-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="efd61-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="efd61-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-249">PrintDialog</span></span>|  
|<span data-ttu-id="efd61-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="efd61-250">ProgressBar</span></span>|  
|<span data-ttu-id="efd61-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="efd61-251">RadioButton</span></span>|  
|<span data-ttu-id="efd61-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="efd61-252">RichTextBox</span></span>|  
|<span data-ttu-id="efd61-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="efd61-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="efd61-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="efd61-254">ScrollableControl</span></span>|  
|<span data-ttu-id="efd61-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="efd61-255">SoundPlayer</span></span>|  
|<span data-ttu-id="efd61-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="efd61-256">StatusBar</span></span>|  
|<span data-ttu-id="efd61-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="efd61-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="efd61-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="efd61-258">TextBox</span></span>|  
|<span data-ttu-id="efd61-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="efd61-259">Timer</span></span>|  
|<span data-ttu-id="efd61-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="efd61-260">Toolbar</span></span>|  
|<span data-ttu-id="efd61-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="efd61-261">ToolTip</span></span>|  
|<span data-ttu-id="efd61-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="efd61-262">TrackBar</span></span>|  
|<span data-ttu-id="efd61-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="efd61-263">TreeView</span></span>|  
|<span data-ttu-id="efd61-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="efd61-264">VscrollBar</span></span>|  
|<span data-ttu-id="efd61-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="efd61-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="efd61-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="efd61-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="efd61-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="efd61-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="efd61-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="efd61-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="efd61-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="efd61-269">BindingSource</span></span>|  
|<span data-ttu-id="efd61-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="efd61-270">DataGrid</span></span>|  
|<span data-ttu-id="efd61-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="efd61-271">DataGridView</span></span>|  
|<span data-ttu-id="efd61-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="efd61-272">DataNavigator</span></span>|  
|<span data-ttu-id="efd61-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="efd61-273">DomainUpDown</span></span>|  
|<span data-ttu-id="efd61-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="efd61-274">ErrorProvider</span></span>|  
|<span data-ttu-id="efd61-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="efd61-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="efd61-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="efd61-276">Form</span></span>|  
|<span data-ttu-id="efd61-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="efd61-277">LinkLabel</span></span>|  
|<span data-ttu-id="efd61-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="efd61-278">HelpProvider</span></span>|  
|<span data-ttu-id="efd61-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="efd61-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="efd61-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="efd61-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="efd61-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="efd61-281">NumericUpDown</span></span>|  
|<span data-ttu-id="efd61-282">Panel</span><span class="sxs-lookup"><span data-stu-id="efd61-282">Panel</span></span>|  
|<span data-ttu-id="efd61-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="efd61-283">PictureBox</span></span>|  
|<span data-ttu-id="efd61-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="efd61-284">PrintDocument</span></span>|  
|<span data-ttu-id="efd61-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="efd61-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="efd61-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="efd61-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="efd61-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="efd61-287">PropertyGrid</span></span>|  
|<span data-ttu-id="efd61-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="efd61-288">UserControl</span></span>|  
|<span data-ttu-id="efd61-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="efd61-289">ToolStrip</span></span>|  
|<span data-ttu-id="efd61-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="efd61-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="efd61-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="efd61-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="efd61-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="efd61-292">Splitter</span></span>|  
|<span data-ttu-id="efd61-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="efd61-293">RaftingContainer</span></span>|  
|<span data-ttu-id="efd61-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="efd61-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efd61-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efd61-295">See also</span></span>

- [<span data-ttu-id="efd61-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="efd61-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
