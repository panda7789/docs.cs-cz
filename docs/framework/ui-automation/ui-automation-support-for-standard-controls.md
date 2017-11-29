---
title: "Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 71a5a2e4319debf1a4d8ddd08d7f0979443682b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="5aa22-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="5aa22-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="5aa22-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5aa22-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5aa22-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5aa22-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5aa22-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpora pro standardní ovládací prvky v aplikacích vytvořených pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.</span><span class="sxs-lookup"><span data-stu-id="5aa22-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="5aa22-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="5aa22-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="5aa22-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mít úplná nativní podpora pro ovládací prvky, které poskytují informace ani podporu pro interakci s uživatelem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aa22-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5aa22-108">Další prvky, jako jsou například panelů, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aa22-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="5aa22-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="5aa22-109">Win32 Controls</span></span>  
 <span data-ttu-id="5aa22-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="5aa22-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5aa22-111">Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5aa22-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5aa22-112">Úplná podpora je k dispozici pouze pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="5aa22-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="5aa22-113">Jsou podporovány následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5aa22-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5aa22-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="5aa22-114">Class name</span></span>|<span data-ttu-id="5aa22-115">– Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5aa22-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5aa22-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-116">Button</span></span>|<span data-ttu-id="5aa22-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-117">Button</span></span>|  
|<span data-ttu-id="5aa22-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-118">Button</span></span>|<span data-ttu-id="5aa22-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5aa22-119">RadioButton</span></span>|  
|<span data-ttu-id="5aa22-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-120">Button</span></span>|<span data-ttu-id="5aa22-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="5aa22-121">Group</span></span>|  
|<span data-ttu-id="5aa22-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-122">Button</span></span>|<span data-ttu-id="5aa22-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-123">CheckBox</span></span>|  
|<span data-ttu-id="5aa22-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-124">Button</span></span>|<span data-ttu-id="5aa22-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="5aa22-125">Hyperlink</span></span>|  
|<span data-ttu-id="5aa22-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-126">Button</span></span>|<span data-ttu-id="5aa22-127">Tlačítko rozdělení</span><span class="sxs-lookup"><span data-stu-id="5aa22-127">SplitButton</span></span>|  
|<span data-ttu-id="5aa22-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-128">Button</span></span>|<span data-ttu-id="5aa22-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-129">CheckBox</span></span>|  
|<span data-ttu-id="5aa22-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="5aa22-130">ComboBoxEx32</span></span>|<span data-ttu-id="5aa22-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-131">ComboBox</span></span>|  
|<span data-ttu-id="5aa22-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-132">ComboBox</span></span>|<span data-ttu-id="5aa22-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-133">ComboBox</span></span>|  
|<span data-ttu-id="5aa22-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="5aa22-134">Edit</span></span>|<span data-ttu-id="5aa22-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="5aa22-135">Document</span></span>|  
|<span data-ttu-id="5aa22-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="5aa22-136">Edit</span></span>|<span data-ttu-id="5aa22-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="5aa22-137">Edit</span></span>|  
|<span data-ttu-id="5aa22-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="5aa22-138">SysLink</span></span>|<span data-ttu-id="5aa22-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="5aa22-139">Hyperlink</span></span>|  
|<span data-ttu-id="5aa22-140">Static</span><span class="sxs-lookup"><span data-stu-id="5aa22-140">Static</span></span>|<span data-ttu-id="5aa22-141">Text</span><span class="sxs-lookup"><span data-stu-id="5aa22-141">Text</span></span>|  
|<span data-ttu-id="5aa22-142">Static</span><span class="sxs-lookup"><span data-stu-id="5aa22-142">Static</span></span>|<span data-ttu-id="5aa22-143">Image</span><span class="sxs-lookup"><span data-stu-id="5aa22-143">Image</span></span>|  
|<span data-ttu-id="5aa22-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="5aa22-144">SysIPAddress32</span></span>|<span data-ttu-id="5aa22-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="5aa22-145">Custom</span></span>|  
|<span data-ttu-id="5aa22-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="5aa22-146">SysHeader32</span></span>|<span data-ttu-id="5aa22-147">Hlavička/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="5aa22-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="5aa22-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5aa22-148">SysListView32</span></span>|<span data-ttu-id="5aa22-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5aa22-149">DataGrid</span></span>|  
|<span data-ttu-id="5aa22-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5aa22-150">SysListView32</span></span>|<span data-ttu-id="5aa22-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="5aa22-151">List</span></span>|  
|<span data-ttu-id="5aa22-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-152">ListBox</span></span>|<span data-ttu-id="5aa22-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="5aa22-153">List</span></span>|  
|<span data-ttu-id="5aa22-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-154">ListBox</span></span>|<span data-ttu-id="5aa22-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="5aa22-155">ListItem</span></span>|  
|<span data-ttu-id="5aa22-156">#32768</span><span class="sxs-lookup"><span data-stu-id="5aa22-156">#32768</span></span>|<span data-ttu-id="5aa22-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="5aa22-157">Menu</span></span>|  
|<span data-ttu-id="5aa22-158">#32768</span><span class="sxs-lookup"><span data-stu-id="5aa22-158">#32768</span></span>|<span data-ttu-id="5aa22-159">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="5aa22-159">MenuItem</span></span>|  
|<span data-ttu-id="5aa22-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="5aa22-160">msctls_progress32</span></span>|<span data-ttu-id="5aa22-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-161">ProgressBar</span></span>|  
|<span data-ttu-id="5aa22-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="5aa22-162">RichEdit</span></span>|<span data-ttu-id="5aa22-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="5aa22-163">Document.</span></span> <span data-ttu-id="5aa22-164">Další informace v poznámce.</span><span class="sxs-lookup"><span data-stu-id="5aa22-164">See note.</span></span>|  
|<span data-ttu-id="5aa22-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="5aa22-165">RichEdit20A</span></span>|<span data-ttu-id="5aa22-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="5aa22-166">Document</span></span>|  
|<span data-ttu-id="5aa22-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="5aa22-167">RichEdit20W</span></span>|<span data-ttu-id="5aa22-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="5aa22-168">Document</span></span>|  
|<span data-ttu-id="5aa22-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="5aa22-169">RichEdit50W</span></span>|<span data-ttu-id="5aa22-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="5aa22-170">Document</span></span>|  
|<span data-ttu-id="5aa22-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-171">ScrollBar</span></span>|<span data-ttu-id="5aa22-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="5aa22-172">Slider</span></span>|  
|<span data-ttu-id="5aa22-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="5aa22-173">msctls_trackbar32</span></span>|<span data-ttu-id="5aa22-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="5aa22-174">Slider</span></span>|  
|<span data-ttu-id="5aa22-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="5aa22-175">msctls_updown32</span></span>|<span data-ttu-id="5aa22-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="5aa22-176">Spinner</span></span>|  
|<span data-ttu-id="5aa22-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="5aa22-177">msctls_statusbar32</span></span>|<span data-ttu-id="5aa22-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-178">StatusBar</span></span>|  
|<span data-ttu-id="5aa22-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5aa22-179">SysTabControl32</span></span>|<span data-ttu-id="5aa22-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="5aa22-180">Tab</span></span>|  
|<span data-ttu-id="5aa22-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5aa22-181">SysTabControl32</span></span>|<span data-ttu-id="5aa22-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="5aa22-182">TabItem</span></span>|  
|<span data-ttu-id="5aa22-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-183">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-184">ToolBar</span></span>|  
|<span data-ttu-id="5aa22-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-185">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-186">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="5aa22-186">MenuItem</span></span>|  
|<span data-ttu-id="5aa22-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-187">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-188">Button</span></span>|  
|<span data-ttu-id="5aa22-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-189">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-190">CheckBox</span></span>|  
|<span data-ttu-id="5aa22-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-191">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5aa22-192">RadioButton</span></span>|  
|<span data-ttu-id="5aa22-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-193">ToolbarWindow32</span></span>|<span data-ttu-id="5aa22-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="5aa22-194">Separator</span></span>|  
|<span data-ttu-id="5aa22-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="5aa22-195">tooltips_class32</span></span>|<span data-ttu-id="5aa22-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="5aa22-196">ToolTip</span></span>|  
|<span data-ttu-id="5aa22-197">#32774</span><span class="sxs-lookup"><span data-stu-id="5aa22-197">#32774</span></span>|<span data-ttu-id="5aa22-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="5aa22-198">ToolTip</span></span>|  
|<span data-ttu-id="5aa22-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="5aa22-199">ReBarWindow32</span></span>|<span data-ttu-id="5aa22-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="5aa22-200">Toolbar</span></span>|  
|<span data-ttu-id="5aa22-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5aa22-201">SysTreeView32</span></span>|<span data-ttu-id="5aa22-202">Strom</span><span class="sxs-lookup"><span data-stu-id="5aa22-202">Tree</span></span>|  
|<span data-ttu-id="5aa22-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5aa22-203">SysTreeView32</span></span>|<span data-ttu-id="5aa22-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="5aa22-204">TreeItem</span></span>|  
  
 <span data-ttu-id="5aa22-205">**Poznámka:** ovládacího prvku RichEdit je podporována pouze pro verze součástí [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (v knihovny RichEd20.dll verze 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="5aa22-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="5aa22-206">Ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="5aa22-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="5aa22-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="5aa22-207">Class name</span></span>|<span data-ttu-id="5aa22-208">– Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5aa22-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5aa22-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="5aa22-209">SysAnimate32</span></span>|<span data-ttu-id="5aa22-210">Image</span><span class="sxs-lookup"><span data-stu-id="5aa22-210">Image</span></span>|  
|<span data-ttu-id="5aa22-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="5aa22-211">SysPager</span></span>|<span data-ttu-id="5aa22-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="5aa22-212">Spinner</span></span>|  
|<span data-ttu-id="5aa22-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="5aa22-213">SysDateTimePick32</span></span>|<span data-ttu-id="5aa22-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="5aa22-214">Custom</span></span>|  
|<span data-ttu-id="5aa22-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="5aa22-215">SysMonthCal32</span></span>|<span data-ttu-id="5aa22-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="5aa22-216">Calendar</span></span>|  
|<span data-ttu-id="5aa22-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="5aa22-217">MS_WINNOTE</span></span>|<span data-ttu-id="5aa22-218">Popisek</span><span class="sxs-lookup"><span data-stu-id="5aa22-218">Tooltip</span></span>|  
|<span data-ttu-id="5aa22-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="5aa22-219">VBBubble</span></span>|<span data-ttu-id="5aa22-220">Popisek</span><span class="sxs-lookup"><span data-stu-id="5aa22-220">Tooltip</span></span>|  
|<span data-ttu-id="5aa22-221">ScrollBar (když se použije jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="5aa22-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="5aa22-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="5aa22-222">Slider</span></span>|  
|<span data-ttu-id="5aa22-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="5aa22-223">SuperGrid</span></span>|<span data-ttu-id="5aa22-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="5aa22-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="5aa22-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5aa22-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="5aa22-226">ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="5aa22-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5aa22-227">Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5aa22-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5aa22-228">Obvykle [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] ovládací prvky, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aa22-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5aa22-229">Jsou podporovány následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5aa22-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5aa22-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="5aa22-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="5aa22-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="5aa22-231">Button</span></span>|  
|<span data-ttu-id="5aa22-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-232">CheckBox</span></span>|  
|<span data-ttu-id="5aa22-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-233">CheckedListBox</span></span>|  
|<span data-ttu-id="5aa22-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="5aa22-234">ColorDialog</span></span>|  
|<span data-ttu-id="5aa22-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-235">ComboBox</span></span>|  
|<span data-ttu-id="5aa22-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="5aa22-236">FolderBrowser</span></span>|  
|<span data-ttu-id="5aa22-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="5aa22-237">FontDialog</span></span>|  
|<span data-ttu-id="5aa22-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-238">GroupBox</span></span>|  
|<span data-ttu-id="5aa22-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-239">HscrollBar</span></span>|  
|<span data-ttu-id="5aa22-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="5aa22-240">ImageList</span></span>|  
|<span data-ttu-id="5aa22-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="5aa22-241">Label</span></span>|  
|<span data-ttu-id="5aa22-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-242">ListBox</span></span>|  
|<span data-ttu-id="5aa22-243">ListView</span><span class="sxs-lookup"><span data-stu-id="5aa22-243">ListView</span></span>|  
|<span data-ttu-id="5aa22-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="5aa22-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="5aa22-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="5aa22-245">MonthCalendar</span></span>|  
|<span data-ttu-id="5aa22-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="5aa22-246">NotifyIcon</span></span>|  
|<span data-ttu-id="5aa22-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="5aa22-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="5aa22-248">PageSetupDialog –</span><span class="sxs-lookup"><span data-stu-id="5aa22-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="5aa22-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="5aa22-249">PrintDialog</span></span>|  
|<span data-ttu-id="5aa22-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-250">ProgressBar</span></span>|  
|<span data-ttu-id="5aa22-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5aa22-251">RadioButton</span></span>|  
|<span data-ttu-id="5aa22-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-252">RichTextBox</span></span>|  
|<span data-ttu-id="5aa22-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="5aa22-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="5aa22-254">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="5aa22-254">ScrollableControl</span></span>|  
|<span data-ttu-id="5aa22-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="5aa22-255">SoundPlayer</span></span>|  
|<span data-ttu-id="5aa22-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-256">StatusBar</span></span>|  
|<span data-ttu-id="5aa22-257">TabControl/TabPage –</span><span class="sxs-lookup"><span data-stu-id="5aa22-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="5aa22-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-258">TextBox</span></span>|  
|<span data-ttu-id="5aa22-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="5aa22-259">Timer</span></span>|  
|<span data-ttu-id="5aa22-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="5aa22-260">Toolbar</span></span>|  
|<span data-ttu-id="5aa22-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="5aa22-261">ToolTip</span></span>|  
|<span data-ttu-id="5aa22-262">TrackBar –</span><span class="sxs-lookup"><span data-stu-id="5aa22-262">TrackBar</span></span>|  
|<span data-ttu-id="5aa22-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="5aa22-263">TreeView</span></span>|  
|<span data-ttu-id="5aa22-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="5aa22-264">VscrollBar</span></span>|  
|<span data-ttu-id="5aa22-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="5aa22-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="5aa22-266">Ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podpora [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aa22-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="5aa22-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5aa22-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="5aa22-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5aa22-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="5aa22-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="5aa22-269">BindingSource</span></span>|  
|<span data-ttu-id="5aa22-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5aa22-270">DataGrid</span></span>|  
|<span data-ttu-id="5aa22-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="5aa22-271">DataGridView</span></span>|  
|<span data-ttu-id="5aa22-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="5aa22-272">DataNavigator</span></span>|  
|<span data-ttu-id="5aa22-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="5aa22-273">DomainUpDown</span></span>|  
|<span data-ttu-id="5aa22-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="5aa22-274">ErrorProvider</span></span>|  
|<span data-ttu-id="5aa22-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5aa22-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="5aa22-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="5aa22-276">Form</span></span>|  
|<span data-ttu-id="5aa22-277">Linklabel –</span><span class="sxs-lookup"><span data-stu-id="5aa22-277">LinkLabel</span></span>|  
|<span data-ttu-id="5aa22-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="5aa22-278">HelpProvider</span></span>|  
|<span data-ttu-id="5aa22-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="5aa22-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="5aa22-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="5aa22-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="5aa22-281">NumericUpDown</span></span>|  
|<span data-ttu-id="5aa22-282">Panel</span><span class="sxs-lookup"><span data-stu-id="5aa22-282">Panel</span></span>|  
|<span data-ttu-id="5aa22-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="5aa22-283">PictureBox</span></span>|  
|<span data-ttu-id="5aa22-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="5aa22-284">PrintDocument</span></span>|  
|<span data-ttu-id="5aa22-285">Printpreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="5aa22-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="5aa22-286">Printpreview – – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="5aa22-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="5aa22-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="5aa22-287">PropertyGrid</span></span>|  
|<span data-ttu-id="5aa22-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="5aa22-288">UserControl</span></span>|  
|<span data-ttu-id="5aa22-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5aa22-289">ToolStrip</span></span>|  
|<span data-ttu-id="5aa22-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5aa22-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="5aa22-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="5aa22-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="5aa22-292">Rozdělovače</span><span class="sxs-lookup"><span data-stu-id="5aa22-292">Splitter</span></span>|  
|<span data-ttu-id="5aa22-293">Prvku RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="5aa22-293">RaftingContainer</span></span>|  
|<span data-ttu-id="5aa22-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="5aa22-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5aa22-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aa22-295">See Also</span></span>  
 [<span data-ttu-id="5aa22-296">Typy ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5aa22-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
