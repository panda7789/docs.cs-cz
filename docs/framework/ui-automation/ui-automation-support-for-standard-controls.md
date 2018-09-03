---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cbfb640a068a2c1178d321480ee3a112db07b6ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463889"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="27789-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="27789-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="27789-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="27789-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="27789-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="27789-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="27789-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="27789-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="27789-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="27789-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="27789-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27789-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="27789-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27789-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="27789-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="27789-109">Win32 Controls</span></span>  
 <span data-ttu-id="27789-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="27789-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="27789-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="27789-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="27789-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="27789-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="27789-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="27789-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="27789-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="27789-114">Class name</span></span>|<span data-ttu-id="27789-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="27789-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="27789-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-116">Button</span></span>|<span data-ttu-id="27789-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-117">Button</span></span>|  
|<span data-ttu-id="27789-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-118">Button</span></span>|<span data-ttu-id="27789-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="27789-119">RadioButton</span></span>|  
|<span data-ttu-id="27789-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-120">Button</span></span>|<span data-ttu-id="27789-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="27789-121">Group</span></span>|  
|<span data-ttu-id="27789-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-122">Button</span></span>|<span data-ttu-id="27789-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="27789-123">CheckBox</span></span>|  
|<span data-ttu-id="27789-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-124">Button</span></span>|<span data-ttu-id="27789-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="27789-125">Hyperlink</span></span>|  
|<span data-ttu-id="27789-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-126">Button</span></span>|<span data-ttu-id="27789-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="27789-127">SplitButton</span></span>|  
|<span data-ttu-id="27789-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-128">Button</span></span>|<span data-ttu-id="27789-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="27789-129">CheckBox</span></span>|  
|<span data-ttu-id="27789-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="27789-130">ComboBoxEx32</span></span>|<span data-ttu-id="27789-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="27789-131">ComboBox</span></span>|  
|<span data-ttu-id="27789-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="27789-132">ComboBox</span></span>|<span data-ttu-id="27789-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="27789-133">ComboBox</span></span>|  
|<span data-ttu-id="27789-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="27789-134">Edit</span></span>|<span data-ttu-id="27789-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="27789-135">Document</span></span>|  
|<span data-ttu-id="27789-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="27789-136">Edit</span></span>|<span data-ttu-id="27789-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="27789-137">Edit</span></span>|  
|<span data-ttu-id="27789-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="27789-138">SysLink</span></span>|<span data-ttu-id="27789-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="27789-139">Hyperlink</span></span>|  
|<span data-ttu-id="27789-140">Static</span><span class="sxs-lookup"><span data-stu-id="27789-140">Static</span></span>|<span data-ttu-id="27789-141">Text</span><span class="sxs-lookup"><span data-stu-id="27789-141">Text</span></span>|  
|<span data-ttu-id="27789-142">Static</span><span class="sxs-lookup"><span data-stu-id="27789-142">Static</span></span>|<span data-ttu-id="27789-143">Image</span><span class="sxs-lookup"><span data-stu-id="27789-143">Image</span></span>|  
|<span data-ttu-id="27789-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="27789-144">SysIPAddress32</span></span>|<span data-ttu-id="27789-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="27789-145">Custom</span></span>|  
|<span data-ttu-id="27789-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="27789-146">SysHeader32</span></span>|<span data-ttu-id="27789-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="27789-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="27789-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="27789-148">SysListView32</span></span>|<span data-ttu-id="27789-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="27789-149">DataGrid</span></span>|  
|<span data-ttu-id="27789-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="27789-150">SysListView32</span></span>|<span data-ttu-id="27789-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="27789-151">List</span></span>|  
|<span data-ttu-id="27789-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="27789-152">ListBox</span></span>|<span data-ttu-id="27789-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="27789-153">List</span></span>|  
|<span data-ttu-id="27789-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="27789-154">ListBox</span></span>|<span data-ttu-id="27789-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="27789-155">ListItem</span></span>|  
|<span data-ttu-id="27789-156">#32768</span><span class="sxs-lookup"><span data-stu-id="27789-156">#32768</span></span>|<span data-ttu-id="27789-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="27789-157">Menu</span></span>|  
|<span data-ttu-id="27789-158">#32768</span><span class="sxs-lookup"><span data-stu-id="27789-158">#32768</span></span>|<span data-ttu-id="27789-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="27789-159">MenuItem</span></span>|  
|<span data-ttu-id="27789-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="27789-160">msctls_progress32</span></span>|<span data-ttu-id="27789-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="27789-161">ProgressBar</span></span>|  
|<span data-ttu-id="27789-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="27789-162">RichEdit</span></span>|<span data-ttu-id="27789-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="27789-163">Document.</span></span> <span data-ttu-id="27789-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="27789-164">See note.</span></span>|  
|<span data-ttu-id="27789-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="27789-165">RichEdit20A</span></span>|<span data-ttu-id="27789-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="27789-166">Document</span></span>|  
|<span data-ttu-id="27789-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="27789-167">RichEdit20W</span></span>|<span data-ttu-id="27789-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="27789-168">Document</span></span>|  
|<span data-ttu-id="27789-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="27789-169">RichEdit50W</span></span>|<span data-ttu-id="27789-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="27789-170">Document</span></span>|  
|<span data-ttu-id="27789-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="27789-171">ScrollBar</span></span>|<span data-ttu-id="27789-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="27789-172">Slider</span></span>|  
|<span data-ttu-id="27789-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="27789-173">msctls_trackbar32</span></span>|<span data-ttu-id="27789-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="27789-174">Slider</span></span>|  
|<span data-ttu-id="27789-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="27789-175">msctls_updown32</span></span>|<span data-ttu-id="27789-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="27789-176">Spinner</span></span>|  
|<span data-ttu-id="27789-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="27789-177">msctls_statusbar32</span></span>|<span data-ttu-id="27789-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="27789-178">StatusBar</span></span>|  
|<span data-ttu-id="27789-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="27789-179">SysTabControl32</span></span>|<span data-ttu-id="27789-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="27789-180">Tab</span></span>|  
|<span data-ttu-id="27789-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="27789-181">SysTabControl32</span></span>|<span data-ttu-id="27789-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="27789-182">TabItem</span></span>|  
|<span data-ttu-id="27789-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-183">ToolbarWindow32</span></span>|<span data-ttu-id="27789-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="27789-184">ToolBar</span></span>|  
|<span data-ttu-id="27789-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-185">ToolbarWindow32</span></span>|<span data-ttu-id="27789-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="27789-186">MenuItem</span></span>|  
|<span data-ttu-id="27789-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-187">ToolbarWindow32</span></span>|<span data-ttu-id="27789-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-188">Button</span></span>|  
|<span data-ttu-id="27789-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-189">ToolbarWindow32</span></span>|<span data-ttu-id="27789-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="27789-190">CheckBox</span></span>|  
|<span data-ttu-id="27789-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-191">ToolbarWindow32</span></span>|<span data-ttu-id="27789-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="27789-192">RadioButton</span></span>|  
|<span data-ttu-id="27789-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-193">ToolbarWindow32</span></span>|<span data-ttu-id="27789-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="27789-194">Separator</span></span>|  
|<span data-ttu-id="27789-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="27789-195">tooltips_class32</span></span>|<span data-ttu-id="27789-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="27789-196">ToolTip</span></span>|  
|<span data-ttu-id="27789-197">#32774</span><span class="sxs-lookup"><span data-stu-id="27789-197">#32774</span></span>|<span data-ttu-id="27789-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="27789-198">ToolTip</span></span>|  
|<span data-ttu-id="27789-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="27789-199">ReBarWindow32</span></span>|<span data-ttu-id="27789-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="27789-200">Toolbar</span></span>|  
|<span data-ttu-id="27789-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="27789-201">SysTreeView32</span></span>|<span data-ttu-id="27789-202">Strom</span><span class="sxs-lookup"><span data-stu-id="27789-202">Tree</span></span>|  
|<span data-ttu-id="27789-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="27789-203">SysTreeView32</span></span>|<span data-ttu-id="27789-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="27789-204">TreeItem</span></span>|  
  
 <span data-ttu-id="27789-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="27789-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="27789-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="27789-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="27789-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="27789-207">Class name</span></span>|<span data-ttu-id="27789-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="27789-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="27789-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="27789-209">SysAnimate32</span></span>|<span data-ttu-id="27789-210">Image</span><span class="sxs-lookup"><span data-stu-id="27789-210">Image</span></span>|  
|<span data-ttu-id="27789-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="27789-211">SysPager</span></span>|<span data-ttu-id="27789-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="27789-212">Spinner</span></span>|  
|<span data-ttu-id="27789-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="27789-213">SysDateTimePick32</span></span>|<span data-ttu-id="27789-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="27789-214">Custom</span></span>|  
|<span data-ttu-id="27789-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="27789-215">SysMonthCal32</span></span>|<span data-ttu-id="27789-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="27789-216">Calendar</span></span>|  
|<span data-ttu-id="27789-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="27789-217">MS_WINNOTE</span></span>|<span data-ttu-id="27789-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="27789-218">Tooltip</span></span>|  
|<span data-ttu-id="27789-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="27789-219">VBBubble</span></span>|<span data-ttu-id="27789-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="27789-220">Tooltip</span></span>|  
|<span data-ttu-id="27789-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="27789-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="27789-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="27789-222">Slider</span></span>|  
|<span data-ttu-id="27789-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="27789-223">SuperGrid</span></span>|<span data-ttu-id="27789-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="27789-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="27789-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27789-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="27789-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="27789-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="27789-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="27789-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="27789-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27789-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="27789-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="27789-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="27789-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="27789-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="27789-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="27789-231">Button</span></span>|  
|<span data-ttu-id="27789-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="27789-232">CheckBox</span></span>|  
|<span data-ttu-id="27789-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="27789-233">CheckedListBox</span></span>|  
|<span data-ttu-id="27789-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="27789-234">ColorDialog</span></span>|  
|<span data-ttu-id="27789-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="27789-235">ComboBox</span></span>|  
|<span data-ttu-id="27789-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="27789-236">FolderBrowser</span></span>|  
|<span data-ttu-id="27789-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="27789-237">FontDialog</span></span>|  
|<span data-ttu-id="27789-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="27789-238">GroupBox</span></span>|  
|<span data-ttu-id="27789-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="27789-239">HscrollBar</span></span>|  
|<span data-ttu-id="27789-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="27789-240">ImageList</span></span>|  
|<span data-ttu-id="27789-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="27789-241">Label</span></span>|  
|<span data-ttu-id="27789-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="27789-242">ListBox</span></span>|  
|<span data-ttu-id="27789-243">ListView</span><span class="sxs-lookup"><span data-stu-id="27789-243">ListView</span></span>|  
|<span data-ttu-id="27789-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="27789-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="27789-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="27789-245">MonthCalendar</span></span>|  
|<span data-ttu-id="27789-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="27789-246">NotifyIcon</span></span>|  
|<span data-ttu-id="27789-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="27789-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="27789-248">Objekt PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="27789-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="27789-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="27789-249">PrintDialog</span></span>|  
|<span data-ttu-id="27789-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="27789-250">ProgressBar</span></span>|  
|<span data-ttu-id="27789-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="27789-251">RadioButton</span></span>|  
|<span data-ttu-id="27789-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="27789-252">RichTextBox</span></span>|  
|<span data-ttu-id="27789-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="27789-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="27789-254">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="27789-254">ScrollableControl</span></span>|  
|<span data-ttu-id="27789-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="27789-255">SoundPlayer</span></span>|  
|<span data-ttu-id="27789-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="27789-256">StatusBar</span></span>|  
|<span data-ttu-id="27789-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="27789-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="27789-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="27789-258">TextBox</span></span>|  
|<span data-ttu-id="27789-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="27789-259">Timer</span></span>|  
|<span data-ttu-id="27789-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="27789-260">Toolbar</span></span>|  
|<span data-ttu-id="27789-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="27789-261">ToolTip</span></span>|  
|<span data-ttu-id="27789-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="27789-262">TrackBar</span></span>|  
|<span data-ttu-id="27789-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="27789-263">TreeView</span></span>|  
|<span data-ttu-id="27789-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="27789-264">VscrollBar</span></span>|  
|<span data-ttu-id="27789-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="27789-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="27789-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27789-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="27789-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="27789-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="27789-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="27789-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="27789-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="27789-269">BindingSource</span></span>|  
|<span data-ttu-id="27789-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="27789-270">DataGrid</span></span>|  
|<span data-ttu-id="27789-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="27789-271">DataGridView</span></span>|  
|<span data-ttu-id="27789-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="27789-272">DataNavigator</span></span>|  
|<span data-ttu-id="27789-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="27789-273">DomainUpDown</span></span>|  
|<span data-ttu-id="27789-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="27789-274">ErrorProvider</span></span>|  
|<span data-ttu-id="27789-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="27789-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="27789-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="27789-276">Form</span></span>|  
|<span data-ttu-id="27789-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="27789-277">LinkLabel</span></span>|  
|<span data-ttu-id="27789-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="27789-278">HelpProvider</span></span>|  
|<span data-ttu-id="27789-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="27789-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="27789-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="27789-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="27789-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="27789-281">NumericUpDown</span></span>|  
|<span data-ttu-id="27789-282">Panel</span><span class="sxs-lookup"><span data-stu-id="27789-282">Panel</span></span>|  
|<span data-ttu-id="27789-283">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="27789-283">PictureBox</span></span>|  
|<span data-ttu-id="27789-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="27789-284">PrintDocument</span></span>|  
|<span data-ttu-id="27789-285">Printpreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="27789-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="27789-286">Printpreview – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="27789-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="27789-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="27789-287">PropertyGrid</span></span>|  
|<span data-ttu-id="27789-288">Uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="27789-288">UserControl</span></span>|  
|<span data-ttu-id="27789-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="27789-289">ToolStrip</span></span>|  
|<span data-ttu-id="27789-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="27789-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="27789-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="27789-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="27789-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="27789-292">Splitter</span></span>|  
|<span data-ttu-id="27789-293">Prvku RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="27789-293">RaftingContainer</span></span>|  
|<span data-ttu-id="27789-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="27789-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27789-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="27789-295">See Also</span></span>  
 [<span data-ttu-id="27789-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="27789-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
