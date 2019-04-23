---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 3fde9779205ea7d0902ddd99ed192f097a159d2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221476"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="49e4e-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="49e4e-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="49e4e-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="49e4e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="49e4e-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="49e4e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="49e4e-105">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.</span><span class="sxs-lookup"><span data-stu-id="49e4e-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="49e4e-106">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="49e4e-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="49e4e-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e4e-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="49e4e-108">Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e4e-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="49e4e-109">Ovládací prvky systému Win32</span><span class="sxs-lookup"><span data-stu-id="49e4e-109">Win32 Controls</span></span>  
 <span data-ttu-id="49e4e-110">Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="49e4e-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="49e4e-111">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="49e4e-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="49e4e-112">Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="49e4e-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="49e4e-113">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="49e4e-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="49e4e-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49e4e-114">Class name</span></span>|<span data-ttu-id="49e4e-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49e4e-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="49e4e-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-116">Button</span></span>|<span data-ttu-id="49e4e-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-117">Button</span></span>|  
|<span data-ttu-id="49e4e-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-118">Button</span></span>|<span data-ttu-id="49e4e-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49e4e-119">RadioButton</span></span>|  
|<span data-ttu-id="49e4e-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-120">Button</span></span>|<span data-ttu-id="49e4e-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="49e4e-121">Group</span></span>|  
|<span data-ttu-id="49e4e-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-122">Button</span></span>|<span data-ttu-id="49e4e-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-123">CheckBox</span></span>|  
|<span data-ttu-id="49e4e-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-124">Button</span></span>|<span data-ttu-id="49e4e-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="49e4e-125">Hyperlink</span></span>|  
|<span data-ttu-id="49e4e-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-126">Button</span></span>|<span data-ttu-id="49e4e-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="49e4e-127">SplitButton</span></span>|  
|<span data-ttu-id="49e4e-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-128">Button</span></span>|<span data-ttu-id="49e4e-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-129">CheckBox</span></span>|  
|<span data-ttu-id="49e4e-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="49e4e-130">ComboBoxEx32</span></span>|<span data-ttu-id="49e4e-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-131">ComboBox</span></span>|  
|<span data-ttu-id="49e4e-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-132">ComboBox</span></span>|<span data-ttu-id="49e4e-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-133">ComboBox</span></span>|  
|<span data-ttu-id="49e4e-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="49e4e-134">Edit</span></span>|<span data-ttu-id="49e4e-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="49e4e-135">Document</span></span>|  
|<span data-ttu-id="49e4e-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="49e4e-136">Edit</span></span>|<span data-ttu-id="49e4e-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="49e4e-137">Edit</span></span>|  
|<span data-ttu-id="49e4e-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="49e4e-138">SysLink</span></span>|<span data-ttu-id="49e4e-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="49e4e-139">Hyperlink</span></span>|  
|<span data-ttu-id="49e4e-140">Static</span><span class="sxs-lookup"><span data-stu-id="49e4e-140">Static</span></span>|<span data-ttu-id="49e4e-141">Text</span><span class="sxs-lookup"><span data-stu-id="49e4e-141">Text</span></span>|  
|<span data-ttu-id="49e4e-142">Static</span><span class="sxs-lookup"><span data-stu-id="49e4e-142">Static</span></span>|<span data-ttu-id="49e4e-143">Image</span><span class="sxs-lookup"><span data-stu-id="49e4e-143">Image</span></span>|  
|<span data-ttu-id="49e4e-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="49e4e-144">SysIPAddress32</span></span>|<span data-ttu-id="49e4e-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49e4e-145">Custom</span></span>|  
|<span data-ttu-id="49e4e-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="49e4e-146">SysHeader32</span></span>|<span data-ttu-id="49e4e-147">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="49e4e-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="49e4e-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="49e4e-148">SysListView32</span></span>|<span data-ttu-id="49e4e-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="49e4e-149">DataGrid</span></span>|  
|<span data-ttu-id="49e4e-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="49e4e-150">SysListView32</span></span>|<span data-ttu-id="49e4e-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="49e4e-151">List</span></span>|  
|<span data-ttu-id="49e4e-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-152">ListBox</span></span>|<span data-ttu-id="49e4e-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="49e4e-153">List</span></span>|  
|<span data-ttu-id="49e4e-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-154">ListBox</span></span>|<span data-ttu-id="49e4e-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="49e4e-155">ListItem</span></span>|  
|<span data-ttu-id="49e4e-156">#32768</span><span class="sxs-lookup"><span data-stu-id="49e4e-156">#32768</span></span>|<span data-ttu-id="49e4e-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="49e4e-157">Menu</span></span>|  
|<span data-ttu-id="49e4e-158">#32768</span><span class="sxs-lookup"><span data-stu-id="49e4e-158">#32768</span></span>|<span data-ttu-id="49e4e-159">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="49e4e-159">MenuItem</span></span>|  
|<span data-ttu-id="49e4e-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="49e4e-160">msctls_progress32</span></span>|<span data-ttu-id="49e4e-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-161">ProgressBar</span></span>|  
|<span data-ttu-id="49e4e-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="49e4e-162">RichEdit</span></span>|<span data-ttu-id="49e4e-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="49e4e-163">Document.</span></span> <span data-ttu-id="49e4e-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="49e4e-164">See note.</span></span>|  
|<span data-ttu-id="49e4e-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="49e4e-165">RichEdit20A</span></span>|<span data-ttu-id="49e4e-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="49e4e-166">Document</span></span>|  
|<span data-ttu-id="49e4e-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="49e4e-167">RichEdit20W</span></span>|<span data-ttu-id="49e4e-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="49e4e-168">Document</span></span>|  
|<span data-ttu-id="49e4e-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="49e4e-169">RichEdit50W</span></span>|<span data-ttu-id="49e4e-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="49e4e-170">Document</span></span>|  
|<span data-ttu-id="49e4e-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-171">ScrollBar</span></span>|<span data-ttu-id="49e4e-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49e4e-172">Slider</span></span>|  
|<span data-ttu-id="49e4e-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="49e4e-173">msctls_trackbar32</span></span>|<span data-ttu-id="49e4e-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49e4e-174">Slider</span></span>|  
|<span data-ttu-id="49e4e-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="49e4e-175">msctls_updown32</span></span>|<span data-ttu-id="49e4e-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="49e4e-176">Spinner</span></span>|  
|<span data-ttu-id="49e4e-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="49e4e-177">msctls_statusbar32</span></span>|<span data-ttu-id="49e4e-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-178">StatusBar</span></span>|  
|<span data-ttu-id="49e4e-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="49e4e-179">SysTabControl32</span></span>|<span data-ttu-id="49e4e-180">Karta</span><span class="sxs-lookup"><span data-stu-id="49e4e-180">Tab</span></span>|  
|<span data-ttu-id="49e4e-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="49e4e-181">SysTabControl32</span></span>|<span data-ttu-id="49e4e-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="49e4e-182">TabItem</span></span>|  
|<span data-ttu-id="49e4e-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-183">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-184">ToolBar</span></span>|  
|<span data-ttu-id="49e4e-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-185">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-186">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="49e4e-186">MenuItem</span></span>|  
|<span data-ttu-id="49e4e-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-187">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-188">Button</span></span>|  
|<span data-ttu-id="49e4e-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-189">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-190">CheckBox</span></span>|  
|<span data-ttu-id="49e4e-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-191">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49e4e-192">RadioButton</span></span>|  
|<span data-ttu-id="49e4e-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-193">ToolbarWindow32</span></span>|<span data-ttu-id="49e4e-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="49e4e-194">Separator</span></span>|  
|<span data-ttu-id="49e4e-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="49e4e-195">tooltips_class32</span></span>|<span data-ttu-id="49e4e-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49e4e-196">ToolTip</span></span>|  
|<span data-ttu-id="49e4e-197">#32774</span><span class="sxs-lookup"><span data-stu-id="49e4e-197">#32774</span></span>|<span data-ttu-id="49e4e-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49e4e-198">ToolTip</span></span>|  
|<span data-ttu-id="49e4e-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="49e4e-199">ReBarWindow32</span></span>|<span data-ttu-id="49e4e-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="49e4e-200">Toolbar</span></span>|  
|<span data-ttu-id="49e4e-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="49e4e-201">SysTreeView32</span></span>|<span data-ttu-id="49e4e-202">Strom</span><span class="sxs-lookup"><span data-stu-id="49e4e-202">Tree</span></span>|  
|<span data-ttu-id="49e4e-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="49e4e-203">SysTreeView32</span></span>|<span data-ttu-id="49e4e-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="49e4e-204">TreeItem</span></span>|  
  
 <span data-ttu-id="49e4e-205">**Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="49e4e-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="49e4e-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="49e4e-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="49e4e-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49e4e-207">Class name</span></span>|<span data-ttu-id="49e4e-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49e4e-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="49e4e-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="49e4e-209">SysAnimate32</span></span>|<span data-ttu-id="49e4e-210">Image</span><span class="sxs-lookup"><span data-stu-id="49e4e-210">Image</span></span>|  
|<span data-ttu-id="49e4e-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="49e4e-211">SysPager</span></span>|<span data-ttu-id="49e4e-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="49e4e-212">Spinner</span></span>|  
|<span data-ttu-id="49e4e-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="49e4e-213">SysDateTimePick32</span></span>|<span data-ttu-id="49e4e-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49e4e-214">Custom</span></span>|  
|<span data-ttu-id="49e4e-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="49e4e-215">SysMonthCal32</span></span>|<span data-ttu-id="49e4e-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="49e4e-216">Calendar</span></span>|  
|<span data-ttu-id="49e4e-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="49e4e-217">MS_WINNOTE</span></span>|<span data-ttu-id="49e4e-218">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="49e4e-218">Tooltip</span></span>|  
|<span data-ttu-id="49e4e-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="49e4e-219">VBBubble</span></span>|<span data-ttu-id="49e4e-220">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="49e4e-220">Tooltip</span></span>|  
|<span data-ttu-id="49e4e-221">Posuvník (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="49e4e-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="49e4e-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="49e4e-222">Slider</span></span>|  
|<span data-ttu-id="49e4e-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="49e4e-223">SuperGrid</span></span>|<span data-ttu-id="49e4e-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="49e4e-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="49e4e-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49e4e-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="49e4e-226">Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="49e4e-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="49e4e-227">Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="49e4e-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="49e4e-228">Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e4e-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="49e4e-229">Podporují se následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="49e4e-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="49e4e-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="49e4e-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="49e4e-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="49e4e-231">Button</span></span>|  
|<span data-ttu-id="49e4e-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-232">CheckBox</span></span>|  
|<span data-ttu-id="49e4e-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-233">CheckedListBox</span></span>|  
|<span data-ttu-id="49e4e-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-234">ColorDialog</span></span>|  
|<span data-ttu-id="49e4e-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-235">ComboBox</span></span>|  
|<span data-ttu-id="49e4e-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="49e4e-236">FolderBrowser</span></span>|  
|<span data-ttu-id="49e4e-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-237">FontDialog</span></span>|  
|<span data-ttu-id="49e4e-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-238">GroupBox</span></span>|  
|<span data-ttu-id="49e4e-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-239">HscrollBar</span></span>|  
|<span data-ttu-id="49e4e-240">Ovládací prvek ImageList</span><span class="sxs-lookup"><span data-stu-id="49e4e-240">ImageList</span></span>|  
|<span data-ttu-id="49e4e-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="49e4e-241">Label</span></span>|  
|<span data-ttu-id="49e4e-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-242">ListBox</span></span>|  
|<span data-ttu-id="49e4e-243">ListView</span><span class="sxs-lookup"><span data-stu-id="49e4e-243">ListView</span></span>|  
|<span data-ttu-id="49e4e-244">MainMenu – / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="49e4e-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="49e4e-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="49e4e-245">MonthCalendar</span></span>|  
|<span data-ttu-id="49e4e-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="49e4e-246">NotifyIcon</span></span>|  
|<span data-ttu-id="49e4e-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="49e4e-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="49e4e-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-249">PrintDialog</span></span>|  
|<span data-ttu-id="49e4e-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-250">ProgressBar</span></span>|  
|<span data-ttu-id="49e4e-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="49e4e-251">RadioButton</span></span>|  
|<span data-ttu-id="49e4e-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-252">RichTextBox</span></span>|  
|<span data-ttu-id="49e4e-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="49e4e-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="49e4e-254">ScrollableControl</span></span>|  
|<span data-ttu-id="49e4e-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="49e4e-255">SoundPlayer</span></span>|  
|<span data-ttu-id="49e4e-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-256">StatusBar</span></span>|  
|<span data-ttu-id="49e4e-257">TabControl – / TabPage –</span><span class="sxs-lookup"><span data-stu-id="49e4e-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="49e4e-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-258">TextBox</span></span>|  
|<span data-ttu-id="49e4e-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="49e4e-259">Timer</span></span>|  
|<span data-ttu-id="49e4e-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="49e4e-260">Toolbar</span></span>|  
|<span data-ttu-id="49e4e-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="49e4e-261">ToolTip</span></span>|  
|<span data-ttu-id="49e4e-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-262">TrackBar</span></span>|  
|<span data-ttu-id="49e4e-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="49e4e-263">TreeView</span></span>|  
|<span data-ttu-id="49e4e-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="49e4e-264">VscrollBar</span></span>|  
|<span data-ttu-id="49e4e-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="49e4e-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="49e4e-266">Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e4e-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="49e4e-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="49e4e-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="49e4e-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="49e4e-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="49e4e-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="49e4e-269">BindingSource</span></span>|  
|<span data-ttu-id="49e4e-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="49e4e-270">DataGrid</span></span>|  
|<span data-ttu-id="49e4e-271">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="49e4e-271">DataGridView</span></span>|  
|<span data-ttu-id="49e4e-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="49e4e-272">DataNavigator</span></span>|  
|<span data-ttu-id="49e4e-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="49e4e-273">DomainUpDown</span></span>|  
|<span data-ttu-id="49e4e-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="49e4e-274">ErrorProvider</span></span>|  
|<span data-ttu-id="49e4e-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="49e4e-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="49e4e-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="49e4e-276">Form</span></span>|  
|<span data-ttu-id="49e4e-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="49e4e-277">LinkLabel</span></span>|  
|<span data-ttu-id="49e4e-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="49e4e-278">HelpProvider</span></span>|  
|<span data-ttu-id="49e4e-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="49e4e-280">MenuStrip – / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="49e4e-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="49e4e-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="49e4e-281">NumericUpDown</span></span>|  
|<span data-ttu-id="49e4e-282">Panel</span><span class="sxs-lookup"><span data-stu-id="49e4e-282">Panel</span></span>|  
|<span data-ttu-id="49e4e-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="49e4e-283">PictureBox</span></span>|  
|<span data-ttu-id="49e4e-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="49e4e-284">PrintDocument</span></span>|  
|<span data-ttu-id="49e4e-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="49e4e-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="49e4e-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="49e4e-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="49e4e-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="49e4e-287">PropertyGrid</span></span>|  
|<span data-ttu-id="49e4e-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="49e4e-288">UserControl</span></span>|  
|<span data-ttu-id="49e4e-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="49e4e-289">ToolStrip</span></span>|  
|<span data-ttu-id="49e4e-290">Kontejner TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="49e4e-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="49e4e-291">SplitContainer – / SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="49e4e-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="49e4e-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="49e4e-292">Splitter</span></span>|  
|<span data-ttu-id="49e4e-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="49e4e-293">RaftingContainer</span></span>|  
|<span data-ttu-id="49e4e-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="49e4e-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49e4e-295">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49e4e-295">See also</span></span>

- [<span data-ttu-id="49e4e-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="49e4e-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
