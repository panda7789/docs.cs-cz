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
ms.workload: dotnet
ms.openlocfilehash: f7529c68e96f93ebbba9fc5e750e09331bda9699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="7f9e1-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7f9e1-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="7f9e1-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7f9e1-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="7f9e1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7f9e1-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpora pro standardní ovládací prvky v aplikacích vytvořených pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="7f9e1-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="7f9e1-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="7f9e1-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mít úplná nativní podpora pro ovládací prvky, které poskytují informace ani podporu pro interakci s uživatelem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9e1-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="7f9e1-108">Další prvky, jako jsou například panelů, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9e1-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="7f9e1-109">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-109">Win32 Controls</span></span>  
 <span data-ttu-id="7f9e1-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="7f9e1-111">Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="7f9e1-112">Úplná podpora je k dispozici pouze pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="7f9e1-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="7f9e1-113">Jsou podporovány následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="7f9e1-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="7f9e1-114">Class name</span></span>|<span data-ttu-id="7f9e1-115">– Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7f9e1-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="7f9e1-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-116">Button</span></span>|<span data-ttu-id="7f9e1-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-117">Button</span></span>|  
|<span data-ttu-id="7f9e1-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-118">Button</span></span>|<span data-ttu-id="7f9e1-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7f9e1-119">RadioButton</span></span>|  
|<span data-ttu-id="7f9e1-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-120">Button</span></span>|<span data-ttu-id="7f9e1-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="7f9e1-121">Group</span></span>|  
|<span data-ttu-id="7f9e1-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-122">Button</span></span>|<span data-ttu-id="7f9e1-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-123">CheckBox</span></span>|  
|<span data-ttu-id="7f9e1-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-124">Button</span></span>|<span data-ttu-id="7f9e1-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="7f9e1-125">Hyperlink</span></span>|  
|<span data-ttu-id="7f9e1-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-126">Button</span></span>|<span data-ttu-id="7f9e1-127">Tlačítko rozdělení</span><span class="sxs-lookup"><span data-stu-id="7f9e1-127">SplitButton</span></span>|  
|<span data-ttu-id="7f9e1-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-128">Button</span></span>|<span data-ttu-id="7f9e1-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-129">CheckBox</span></span>|  
|<span data-ttu-id="7f9e1-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-130">ComboBoxEx32</span></span>|<span data-ttu-id="7f9e1-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-131">ComboBox</span></span>|  
|<span data-ttu-id="7f9e1-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-132">ComboBox</span></span>|<span data-ttu-id="7f9e1-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-133">ComboBox</span></span>|  
|<span data-ttu-id="7f9e1-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="7f9e1-134">Edit</span></span>|<span data-ttu-id="7f9e1-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="7f9e1-135">Document</span></span>|  
|<span data-ttu-id="7f9e1-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="7f9e1-136">Edit</span></span>|<span data-ttu-id="7f9e1-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="7f9e1-137">Edit</span></span>|  
|<span data-ttu-id="7f9e1-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="7f9e1-138">SysLink</span></span>|<span data-ttu-id="7f9e1-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="7f9e1-139">Hyperlink</span></span>|  
|<span data-ttu-id="7f9e1-140">Static</span><span class="sxs-lookup"><span data-stu-id="7f9e1-140">Static</span></span>|<span data-ttu-id="7f9e1-141">Text</span><span class="sxs-lookup"><span data-stu-id="7f9e1-141">Text</span></span>|  
|<span data-ttu-id="7f9e1-142">Static</span><span class="sxs-lookup"><span data-stu-id="7f9e1-142">Static</span></span>|<span data-ttu-id="7f9e1-143">Image</span><span class="sxs-lookup"><span data-stu-id="7f9e1-143">Image</span></span>|  
|<span data-ttu-id="7f9e1-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-144">SysIPAddress32</span></span>|<span data-ttu-id="7f9e1-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="7f9e1-145">Custom</span></span>|  
|<span data-ttu-id="7f9e1-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-146">SysHeader32</span></span>|<span data-ttu-id="7f9e1-147">Hlavička/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="7f9e1-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="7f9e1-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-148">SysListView32</span></span>|<span data-ttu-id="7f9e1-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="7f9e1-149">DataGrid</span></span>|  
|<span data-ttu-id="7f9e1-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-150">SysListView32</span></span>|<span data-ttu-id="7f9e1-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="7f9e1-151">List</span></span>|  
|<span data-ttu-id="7f9e1-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-152">ListBox</span></span>|<span data-ttu-id="7f9e1-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="7f9e1-153">List</span></span>|  
|<span data-ttu-id="7f9e1-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-154">ListBox</span></span>|<span data-ttu-id="7f9e1-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="7f9e1-155">ListItem</span></span>|  
|<span data-ttu-id="7f9e1-156">#32768</span><span class="sxs-lookup"><span data-stu-id="7f9e1-156">#32768</span></span>|<span data-ttu-id="7f9e1-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="7f9e1-157">Menu</span></span>|  
|<span data-ttu-id="7f9e1-158">#32768</span><span class="sxs-lookup"><span data-stu-id="7f9e1-158">#32768</span></span>|<span data-ttu-id="7f9e1-159">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="7f9e1-159">MenuItem</span></span>|  
|<span data-ttu-id="7f9e1-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-160">msctls_progress32</span></span>|<span data-ttu-id="7f9e1-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-161">ProgressBar</span></span>|  
|<span data-ttu-id="7f9e1-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="7f9e1-162">RichEdit</span></span>|<span data-ttu-id="7f9e1-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-163">Document.</span></span> <span data-ttu-id="7f9e1-164">Další informace v poznámce.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-164">See note.</span></span>|  
|<span data-ttu-id="7f9e1-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="7f9e1-165">RichEdit20A</span></span>|<span data-ttu-id="7f9e1-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="7f9e1-166">Document</span></span>|  
|<span data-ttu-id="7f9e1-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="7f9e1-167">RichEdit20W</span></span>|<span data-ttu-id="7f9e1-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="7f9e1-168">Document</span></span>|  
|<span data-ttu-id="7f9e1-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="7f9e1-169">RichEdit50W</span></span>|<span data-ttu-id="7f9e1-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="7f9e1-170">Document</span></span>|  
|<span data-ttu-id="7f9e1-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-171">ScrollBar</span></span>|<span data-ttu-id="7f9e1-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="7f9e1-172">Slider</span></span>|  
|<span data-ttu-id="7f9e1-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-173">msctls_trackbar32</span></span>|<span data-ttu-id="7f9e1-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="7f9e1-174">Slider</span></span>|  
|<span data-ttu-id="7f9e1-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-175">msctls_updown32</span></span>|<span data-ttu-id="7f9e1-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="7f9e1-176">Spinner</span></span>|  
|<span data-ttu-id="7f9e1-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-177">msctls_statusbar32</span></span>|<span data-ttu-id="7f9e1-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-178">StatusBar</span></span>|  
|<span data-ttu-id="7f9e1-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-179">SysTabControl32</span></span>|<span data-ttu-id="7f9e1-180">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="7f9e1-180">Tab</span></span>|  
|<span data-ttu-id="7f9e1-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-181">SysTabControl32</span></span>|<span data-ttu-id="7f9e1-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="7f9e1-182">TabItem</span></span>|  
|<span data-ttu-id="7f9e1-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-183">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-184">ToolBar</span></span>|  
|<span data-ttu-id="7f9e1-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-185">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-186">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="7f9e1-186">MenuItem</span></span>|  
|<span data-ttu-id="7f9e1-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-187">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-188">Button</span></span>|  
|<span data-ttu-id="7f9e1-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-189">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-190">CheckBox</span></span>|  
|<span data-ttu-id="7f9e1-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-191">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7f9e1-192">RadioButton</span></span>|  
|<span data-ttu-id="7f9e1-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-193">ToolbarWindow32</span></span>|<span data-ttu-id="7f9e1-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="7f9e1-194">Separator</span></span>|  
|<span data-ttu-id="7f9e1-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-195">tooltips_class32</span></span>|<span data-ttu-id="7f9e1-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-196">ToolTip</span></span>|  
|<span data-ttu-id="7f9e1-197">#32774</span><span class="sxs-lookup"><span data-stu-id="7f9e1-197">#32774</span></span>|<span data-ttu-id="7f9e1-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-198">ToolTip</span></span>|  
|<span data-ttu-id="7f9e1-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-199">ReBarWindow32</span></span>|<span data-ttu-id="7f9e1-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="7f9e1-200">Toolbar</span></span>|  
|<span data-ttu-id="7f9e1-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-201">SysTreeView32</span></span>|<span data-ttu-id="7f9e1-202">Strom</span><span class="sxs-lookup"><span data-stu-id="7f9e1-202">Tree</span></span>|  
|<span data-ttu-id="7f9e1-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-203">SysTreeView32</span></span>|<span data-ttu-id="7f9e1-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="7f9e1-204">TreeItem</span></span>|  
  
 <span data-ttu-id="7f9e1-205">**Poznámka:** ovládacího prvku RichEdit je podporována pouze pro verze součástí [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (v knihovny RichEd20.dll verze 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="7f9e1-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="7f9e1-206">Ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="7f9e1-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="7f9e1-207">Class name</span></span>|<span data-ttu-id="7f9e1-208">– Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7f9e1-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="7f9e1-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-209">SysAnimate32</span></span>|<span data-ttu-id="7f9e1-210">Image</span><span class="sxs-lookup"><span data-stu-id="7f9e1-210">Image</span></span>|  
|<span data-ttu-id="7f9e1-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="7f9e1-211">SysPager</span></span>|<span data-ttu-id="7f9e1-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="7f9e1-212">Spinner</span></span>|  
|<span data-ttu-id="7f9e1-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-213">SysDateTimePick32</span></span>|<span data-ttu-id="7f9e1-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="7f9e1-214">Custom</span></span>|  
|<span data-ttu-id="7f9e1-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="7f9e1-215">SysMonthCal32</span></span>|<span data-ttu-id="7f9e1-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="7f9e1-216">Calendar</span></span>|  
|<span data-ttu-id="7f9e1-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="7f9e1-217">MS_WINNOTE</span></span>|<span data-ttu-id="7f9e1-218">Popisek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-218">Tooltip</span></span>|  
|<span data-ttu-id="7f9e1-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="7f9e1-219">VBBubble</span></span>|<span data-ttu-id="7f9e1-220">Popisek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-220">Tooltip</span></span>|  
|<span data-ttu-id="7f9e1-221">ScrollBar (když se použije jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="7f9e1-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="7f9e1-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="7f9e1-222">Slider</span></span>|  
|<span data-ttu-id="7f9e1-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="7f9e1-223">SuperGrid</span></span>|<span data-ttu-id="7f9e1-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="7f9e1-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="7f9e1-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f9e1-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="7f9e1-226">ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="7f9e1-227">Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="7f9e1-228">Obvykle [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] ovládací prvky, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9e1-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="7f9e1-229">Jsou podporovány následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="7f9e1-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="7f9e1-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="7f9e1-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="7f9e1-231">Button</span></span>|  
|<span data-ttu-id="7f9e1-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-232">CheckBox</span></span>|  
|<span data-ttu-id="7f9e1-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-233">CheckedListBox</span></span>|  
|<span data-ttu-id="7f9e1-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="7f9e1-234">ColorDialog</span></span>|  
|<span data-ttu-id="7f9e1-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-235">ComboBox</span></span>|  
|<span data-ttu-id="7f9e1-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="7f9e1-236">FolderBrowser</span></span>|  
|<span data-ttu-id="7f9e1-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="7f9e1-237">FontDialog</span></span>|  
|<span data-ttu-id="7f9e1-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-238">GroupBox</span></span>|  
|<span data-ttu-id="7f9e1-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-239">HscrollBar</span></span>|  
|<span data-ttu-id="7f9e1-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="7f9e1-240">ImageList</span></span>|  
|<span data-ttu-id="7f9e1-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-241">Label</span></span>|  
|<span data-ttu-id="7f9e1-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-242">ListBox</span></span>|  
|<span data-ttu-id="7f9e1-243">ListView</span><span class="sxs-lookup"><span data-stu-id="7f9e1-243">ListView</span></span>|  
|<span data-ttu-id="7f9e1-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7f9e1-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="7f9e1-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-245">MonthCalendar</span></span>|  
|<span data-ttu-id="7f9e1-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="7f9e1-246">NotifyIcon</span></span>|  
|<span data-ttu-id="7f9e1-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="7f9e1-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="7f9e1-248">PageSetupDialog –</span><span class="sxs-lookup"><span data-stu-id="7f9e1-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="7f9e1-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="7f9e1-249">PrintDialog</span></span>|  
|<span data-ttu-id="7f9e1-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-250">ProgressBar</span></span>|  
|<span data-ttu-id="7f9e1-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7f9e1-251">RadioButton</span></span>|  
|<span data-ttu-id="7f9e1-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-252">RichTextBox</span></span>|  
|<span data-ttu-id="7f9e1-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="7f9e1-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="7f9e1-254">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="7f9e1-254">ScrollableControl</span></span>|  
|<span data-ttu-id="7f9e1-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="7f9e1-255">SoundPlayer</span></span>|  
|<span data-ttu-id="7f9e1-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-256">StatusBar</span></span>|  
|<span data-ttu-id="7f9e1-257">TabControl/TabPage –</span><span class="sxs-lookup"><span data-stu-id="7f9e1-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="7f9e1-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-258">TextBox</span></span>|  
|<span data-ttu-id="7f9e1-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="7f9e1-259">Timer</span></span>|  
|<span data-ttu-id="7f9e1-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="7f9e1-260">Toolbar</span></span>|  
|<span data-ttu-id="7f9e1-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-261">ToolTip</span></span>|  
|<span data-ttu-id="7f9e1-262">TrackBar –</span><span class="sxs-lookup"><span data-stu-id="7f9e1-262">TrackBar</span></span>|  
|<span data-ttu-id="7f9e1-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="7f9e1-263">TreeView</span></span>|  
|<span data-ttu-id="7f9e1-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="7f9e1-264">VscrollBar</span></span>|  
|<span data-ttu-id="7f9e1-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="7f9e1-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="7f9e1-266">Ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podpora [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9e1-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="7f9e1-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7f9e1-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="7f9e1-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7f9e1-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="7f9e1-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="7f9e1-269">BindingSource</span></span>|  
|<span data-ttu-id="7f9e1-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="7f9e1-270">DataGrid</span></span>|  
|<span data-ttu-id="7f9e1-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="7f9e1-271">DataGridView</span></span>|  
|<span data-ttu-id="7f9e1-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="7f9e1-272">DataNavigator</span></span>|  
|<span data-ttu-id="7f9e1-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="7f9e1-273">DomainUpDown</span></span>|  
|<span data-ttu-id="7f9e1-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="7f9e1-274">ErrorProvider</span></span>|  
|<span data-ttu-id="7f9e1-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7f9e1-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="7f9e1-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="7f9e1-276">Form</span></span>|  
|<span data-ttu-id="7f9e1-277">Linklabel –</span><span class="sxs-lookup"><span data-stu-id="7f9e1-277">LinkLabel</span></span>|  
|<span data-ttu-id="7f9e1-278">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="7f9e1-278">HelpProvider</span></span>|  
|<span data-ttu-id="7f9e1-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="7f9e1-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="7f9e1-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="7f9e1-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="7f9e1-281">NumericUpDown</span></span>|  
|<span data-ttu-id="7f9e1-282">Panel</span><span class="sxs-lookup"><span data-stu-id="7f9e1-282">Panel</span></span>|  
|<span data-ttu-id="7f9e1-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="7f9e1-283">PictureBox</span></span>|  
|<span data-ttu-id="7f9e1-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7f9e1-284">PrintDocument</span></span>|  
|<span data-ttu-id="7f9e1-285">Printpreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7f9e1-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="7f9e1-286">Printpreview – – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="7f9e1-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="7f9e1-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="7f9e1-287">PropertyGrid</span></span>|  
|<span data-ttu-id="7f9e1-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="7f9e1-288">UserControl</span></span>|  
|<span data-ttu-id="7f9e1-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7f9e1-289">ToolStrip</span></span>|  
|<span data-ttu-id="7f9e1-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7f9e1-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="7f9e1-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="7f9e1-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="7f9e1-292">Rozdělovače</span><span class="sxs-lookup"><span data-stu-id="7f9e1-292">Splitter</span></span>|  
|<span data-ttu-id="7f9e1-293">Prvku RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="7f9e1-293">RaftingContainer</span></span>|  
|<span data-ttu-id="7f9e1-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="7f9e1-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f9e1-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f9e1-295">See Also</span></span>  
 [<span data-ttu-id="7f9e1-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f9e1-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
