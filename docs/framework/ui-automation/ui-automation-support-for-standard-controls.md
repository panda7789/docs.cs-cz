---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro standardní ovládací prvky v aplikacích vyvinutých pro Windows Presentation Foundation (WPF), Win32 a model Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166124"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="a89e7-103">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="a89e7-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="a89e7-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a89e7-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a89e7-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a89e7-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a89e7-106">Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře standardních ovládacích prvků v aplikacích vyvinutých pro rozhraní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Win32 a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a89e7-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="a89e7-107">Ovládací prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a89e7-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="a89e7-108">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky ovládacích prvků, které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a89e7-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a89e7-109">Jiné prvky, například panely, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a89e7-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="a89e7-110">Ovládací prvky Win32</span><span class="sxs-lookup"><span data-stu-id="a89e7-110">Win32 Controls</span></span>  
 <span data-ttu-id="a89e7-111">Většina ovládacích prvků Win32 se zveřejňuje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="a89e7-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a89e7-112">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a89e7-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a89e7-113">Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="a89e7-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="a89e7-114">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a89e7-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a89e7-115">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a89e7-115">Class name</span></span>|<span data-ttu-id="a89e7-116">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a89e7-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a89e7-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-117">Button</span></span>|<span data-ttu-id="a89e7-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-118">Button</span></span>|  
|<span data-ttu-id="a89e7-119">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-119">Button</span></span>|<span data-ttu-id="a89e7-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a89e7-120">RadioButton</span></span>|  
|<span data-ttu-id="a89e7-121">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-121">Button</span></span>|<span data-ttu-id="a89e7-122">Skupina</span><span class="sxs-lookup"><span data-stu-id="a89e7-122">Group</span></span>|  
|<span data-ttu-id="a89e7-123">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-123">Button</span></span>|<span data-ttu-id="a89e7-124">Zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="a89e7-124">CheckBox</span></span>|  
|<span data-ttu-id="a89e7-125">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-125">Button</span></span>|<span data-ttu-id="a89e7-126">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="a89e7-126">Hyperlink</span></span>|  
|<span data-ttu-id="a89e7-127">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-127">Button</span></span>|<span data-ttu-id="a89e7-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="a89e7-128">SplitButton</span></span>|  
|<span data-ttu-id="a89e7-129">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-129">Button</span></span>|<span data-ttu-id="a89e7-130">Zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="a89e7-130">CheckBox</span></span>|  
|<span data-ttu-id="a89e7-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="a89e7-131">ComboBoxEx32</span></span>|<span data-ttu-id="a89e7-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-132">ComboBox</span></span>|  
|<span data-ttu-id="a89e7-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-133">ComboBox</span></span>|<span data-ttu-id="a89e7-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-134">ComboBox</span></span>|  
|<span data-ttu-id="a89e7-135">Upravit</span><span class="sxs-lookup"><span data-stu-id="a89e7-135">Edit</span></span>|<span data-ttu-id="a89e7-136">Dokument</span><span class="sxs-lookup"><span data-stu-id="a89e7-136">Document</span></span>|  
|<span data-ttu-id="a89e7-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="a89e7-137">Edit</span></span>|<span data-ttu-id="a89e7-138">Upravit</span><span class="sxs-lookup"><span data-stu-id="a89e7-138">Edit</span></span>|  
|<span data-ttu-id="a89e7-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="a89e7-139">SysLink</span></span>|<span data-ttu-id="a89e7-140">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="a89e7-140">Hyperlink</span></span>|  
|<span data-ttu-id="a89e7-141">Statická</span><span class="sxs-lookup"><span data-stu-id="a89e7-141">Static</span></span>|<span data-ttu-id="a89e7-142">Text</span><span class="sxs-lookup"><span data-stu-id="a89e7-142">Text</span></span>|  
|<span data-ttu-id="a89e7-143">Statická</span><span class="sxs-lookup"><span data-stu-id="a89e7-143">Static</span></span>|<span data-ttu-id="a89e7-144">Image</span><span class="sxs-lookup"><span data-stu-id="a89e7-144">Image</span></span>|  
|<span data-ttu-id="a89e7-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="a89e7-145">SysIPAddress32</span></span>|<span data-ttu-id="a89e7-146">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a89e7-146">Custom</span></span>|  
|<span data-ttu-id="a89e7-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="a89e7-147">SysHeader32</span></span>|<span data-ttu-id="a89e7-148">Záhlaví/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="a89e7-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="a89e7-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a89e7-149">SysListView32</span></span>|<span data-ttu-id="a89e7-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a89e7-150">DataGrid</span></span>|  
|<span data-ttu-id="a89e7-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="a89e7-151">SysListView32</span></span>|<span data-ttu-id="a89e7-152">Seznam</span><span class="sxs-lookup"><span data-stu-id="a89e7-152">List</span></span>|  
|<span data-ttu-id="a89e7-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-153">ListBox</span></span>|<span data-ttu-id="a89e7-154">Seznam</span><span class="sxs-lookup"><span data-stu-id="a89e7-154">List</span></span>|  
|<span data-ttu-id="a89e7-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-155">ListBox</span></span>|<span data-ttu-id="a89e7-156">Collection</span><span class="sxs-lookup"><span data-stu-id="a89e7-156">ListItem</span></span>|  
|<span data-ttu-id="a89e7-157">#32768</span><span class="sxs-lookup"><span data-stu-id="a89e7-157">#32768</span></span>|<span data-ttu-id="a89e7-158">Nabídka</span><span class="sxs-lookup"><span data-stu-id="a89e7-158">Menu</span></span>|  
|<span data-ttu-id="a89e7-159">#32768</span><span class="sxs-lookup"><span data-stu-id="a89e7-159">#32768</span></span>|<span data-ttu-id="a89e7-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a89e7-160">MenuItem</span></span>|  
|<span data-ttu-id="a89e7-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="a89e7-161">msctls_progress32</span></span>|<span data-ttu-id="a89e7-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-162">ProgressBar</span></span>|  
|<span data-ttu-id="a89e7-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="a89e7-163">RichEdit</span></span>|<span data-ttu-id="a89e7-164">Dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a89e7-164">Document.</span></span> <span data-ttu-id="a89e7-165">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="a89e7-165">See note.</span></span>|  
|<span data-ttu-id="a89e7-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="a89e7-166">RichEdit20A</span></span>|<span data-ttu-id="a89e7-167">Dokument</span><span class="sxs-lookup"><span data-stu-id="a89e7-167">Document</span></span>|  
|<span data-ttu-id="a89e7-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="a89e7-168">RichEdit20W</span></span>|<span data-ttu-id="a89e7-169">Dokument</span><span class="sxs-lookup"><span data-stu-id="a89e7-169">Document</span></span>|  
|<span data-ttu-id="a89e7-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="a89e7-170">RichEdit50W</span></span>|<span data-ttu-id="a89e7-171">Dokument</span><span class="sxs-lookup"><span data-stu-id="a89e7-171">Document</span></span>|  
|<span data-ttu-id="a89e7-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-172">ScrollBar</span></span>|<span data-ttu-id="a89e7-173">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a89e7-173">Slider</span></span>|  
|<span data-ttu-id="a89e7-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="a89e7-174">msctls_trackbar32</span></span>|<span data-ttu-id="a89e7-175">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a89e7-175">Slider</span></span>|  
|<span data-ttu-id="a89e7-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="a89e7-176">msctls_updown32</span></span>|<span data-ttu-id="a89e7-177">Číselník</span><span class="sxs-lookup"><span data-stu-id="a89e7-177">Spinner</span></span>|  
|<span data-ttu-id="a89e7-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="a89e7-178">msctls_statusbar32</span></span>|<span data-ttu-id="a89e7-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-179">StatusBar</span></span>|  
|<span data-ttu-id="a89e7-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a89e7-180">SysTabControl32</span></span>|<span data-ttu-id="a89e7-181">Karta</span><span class="sxs-lookup"><span data-stu-id="a89e7-181">Tab</span></span>|  
|<span data-ttu-id="a89e7-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="a89e7-182">SysTabControl32</span></span>|<span data-ttu-id="a89e7-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="a89e7-183">TabItem</span></span>|  
|<span data-ttu-id="a89e7-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-184">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-185">ToolBar</span></span>|  
|<span data-ttu-id="a89e7-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-186">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a89e7-187">MenuItem</span></span>|  
|<span data-ttu-id="a89e7-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-188">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-189">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-189">Button</span></span>|  
|<span data-ttu-id="a89e7-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-190">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-191">Zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="a89e7-191">CheckBox</span></span>|  
|<span data-ttu-id="a89e7-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-192">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a89e7-193">RadioButton</span></span>|  
|<span data-ttu-id="a89e7-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-194">ToolbarWindow32</span></span>|<span data-ttu-id="a89e7-195">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a89e7-195">Separator</span></span>|  
|<span data-ttu-id="a89e7-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="a89e7-196">tooltips_class32</span></span>|<span data-ttu-id="a89e7-197">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a89e7-197">ToolTip</span></span>|  
|<span data-ttu-id="a89e7-198">#32774</span><span class="sxs-lookup"><span data-stu-id="a89e7-198">#32774</span></span>|<span data-ttu-id="a89e7-199">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a89e7-199">ToolTip</span></span>|  
|<span data-ttu-id="a89e7-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="a89e7-200">ReBarWindow32</span></span>|<span data-ttu-id="a89e7-201">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="a89e7-201">Toolbar</span></span>|  
|<span data-ttu-id="a89e7-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a89e7-202">SysTreeView32</span></span>|<span data-ttu-id="a89e7-203">Strom</span><span class="sxs-lookup"><span data-stu-id="a89e7-203">Tree</span></span>|  
|<span data-ttu-id="a89e7-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="a89e7-204">SysTreeView32</span></span>|<span data-ttu-id="a89e7-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="a89e7-205">TreeItem</span></span>|  
  
 <span data-ttu-id="a89e7-206">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v RichEd20.dll verze 3,1 a novější a MsftEdit.dll verze 4,1 a novější).</span><span class="sxs-lookup"><span data-stu-id="a89e7-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="a89e7-207">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a89e7-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="a89e7-208">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a89e7-208">Class name</span></span>|<span data-ttu-id="a89e7-209">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a89e7-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a89e7-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="a89e7-210">SysAnimate32</span></span>|<span data-ttu-id="a89e7-211">Image</span><span class="sxs-lookup"><span data-stu-id="a89e7-211">Image</span></span>|  
|<span data-ttu-id="a89e7-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="a89e7-212">SysPager</span></span>|<span data-ttu-id="a89e7-213">Číselník</span><span class="sxs-lookup"><span data-stu-id="a89e7-213">Spinner</span></span>|  
|<span data-ttu-id="a89e7-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="a89e7-214">SysDateTimePick32</span></span>|<span data-ttu-id="a89e7-215">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a89e7-215">Custom</span></span>|  
|<span data-ttu-id="a89e7-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="a89e7-216">SysMonthCal32</span></span>|<span data-ttu-id="a89e7-217">Kalendář</span><span class="sxs-lookup"><span data-stu-id="a89e7-217">Calendar</span></span>|  
|<span data-ttu-id="a89e7-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="a89e7-218">MS_WINNOTE</span></span>|<span data-ttu-id="a89e7-219">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="a89e7-219">Tooltip</span></span>|  
|<span data-ttu-id="a89e7-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="a89e7-220">VBBubble</span></span>|<span data-ttu-id="a89e7-221">Popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="a89e7-221">Tooltip</span></span>|  
|<span data-ttu-id="a89e7-222">ScrollBar (při použití jako samostatného ovládacího prvku)</span><span class="sxs-lookup"><span data-stu-id="a89e7-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="a89e7-223">Posuvník</span><span class="sxs-lookup"><span data-stu-id="a89e7-223">Slider</span></span>|  
|<span data-ttu-id="a89e7-224">Mřížka</span><span class="sxs-lookup"><span data-stu-id="a89e7-224">SuperGrid</span></span>|<span data-ttu-id="a89e7-225">Vlastní</span><span class="sxs-lookup"><span data-stu-id="a89e7-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="a89e7-226">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a89e7-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="a89e7-227">Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="a89e7-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="a89e7-228">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a89e7-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="a89e7-229">Obvykle jsou model Windows Forms ovládací prvky, které jsou spravované obálky pro běžné ovládací prvky Win32, podporovány nástrojem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a89e7-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="a89e7-230">Podporovány jsou následující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a89e7-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="a89e7-231">Název třídy</span><span class="sxs-lookup"><span data-stu-id="a89e7-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="a89e7-232">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a89e7-232">Button</span></span>|  
|<span data-ttu-id="a89e7-233">Zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="a89e7-233">CheckBox</span></span>|  
|<span data-ttu-id="a89e7-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-234">CheckedListBox</span></span>|  
|<span data-ttu-id="a89e7-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-235">ColorDialog</span></span>|  
|<span data-ttu-id="a89e7-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-236">ComboBox</span></span>|  
|<span data-ttu-id="a89e7-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="a89e7-237">FolderBrowser</span></span>|  
|<span data-ttu-id="a89e7-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-238">FontDialog</span></span>|  
|<span data-ttu-id="a89e7-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-239">GroupBox</span></span>|  
|<span data-ttu-id="a89e7-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-240">HscrollBar</span></span>|  
|<span data-ttu-id="a89e7-241">Obrázků</span><span class="sxs-lookup"><span data-stu-id="a89e7-241">ImageList</span></span>|  
|<span data-ttu-id="a89e7-242">Popisek</span><span class="sxs-lookup"><span data-stu-id="a89e7-242">Label</span></span>|  
|<span data-ttu-id="a89e7-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-243">ListBox</span></span>|  
|<span data-ttu-id="a89e7-244">ListView</span><span class="sxs-lookup"><span data-stu-id="a89e7-244">ListView</span></span>|  
|<span data-ttu-id="a89e7-245">MainMenu/vynabídku</span><span class="sxs-lookup"><span data-stu-id="a89e7-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="a89e7-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="a89e7-246">MonthCalendar</span></span>|  
|<span data-ttu-id="a89e7-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="a89e7-247">NotifyIcon</span></span>|  
|<span data-ttu-id="a89e7-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="a89e7-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="a89e7-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-250">PrintDialog</span></span>|  
|<span data-ttu-id="a89e7-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-251">ProgressBar</span></span>|  
|<span data-ttu-id="a89e7-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a89e7-252">RadioButton</span></span>|  
|<span data-ttu-id="a89e7-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-253">RichTextBox</span></span>|  
|<span data-ttu-id="a89e7-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="a89e7-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="a89e7-255">Ovládací prvek ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="a89e7-255">ScrollableControl</span></span>|  
|<span data-ttu-id="a89e7-256">Komponentu</span><span class="sxs-lookup"><span data-stu-id="a89e7-256">SoundPlayer</span></span>|  
|<span data-ttu-id="a89e7-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-257">StatusBar</span></span>|  
|<span data-ttu-id="a89e7-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="a89e7-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="a89e7-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-259">TextBox</span></span>|  
|<span data-ttu-id="a89e7-260">Časovač</span><span class="sxs-lookup"><span data-stu-id="a89e7-260">Timer</span></span>|  
|<span data-ttu-id="a89e7-261">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="a89e7-261">Toolbar</span></span>|  
|<span data-ttu-id="a89e7-262">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="a89e7-262">ToolTip</span></span>|  
|<span data-ttu-id="a89e7-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-263">TrackBar</span></span>|  
|<span data-ttu-id="a89e7-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="a89e7-264">TreeView</span></span>|  
|<span data-ttu-id="a89e7-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="a89e7-265">VscrollBar</span></span>|  
|<span data-ttu-id="a89e7-266">Navig</span><span class="sxs-lookup"><span data-stu-id="a89e7-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="a89e7-267">Následující ovládací prvky jsou k dispozici [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podpory pro Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="a89e7-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="a89e7-268">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a89e7-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="a89e7-269">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a89e7-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="a89e7-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="a89e7-270">BindingSource</span></span>|  
|<span data-ttu-id="a89e7-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a89e7-271">DataGrid</span></span>|  
|<span data-ttu-id="a89e7-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="a89e7-272">DataGridView</span></span>|  
|<span data-ttu-id="a89e7-273">Datanavigator</span><span class="sxs-lookup"><span data-stu-id="a89e7-273">DataNavigator</span></span>|  
|<span data-ttu-id="a89e7-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a89e7-274">DomainUpDown</span></span>|  
|<span data-ttu-id="a89e7-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="a89e7-275">ErrorProvider</span></span>|  
|<span data-ttu-id="a89e7-276">Kontejneru</span><span class="sxs-lookup"><span data-stu-id="a89e7-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="a89e7-277">Formulář</span><span class="sxs-lookup"><span data-stu-id="a89e7-277">Form</span></span>|  
|<span data-ttu-id="a89e7-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a89e7-278">LinkLabel</span></span>|  
|<span data-ttu-id="a89e7-279">HelpProvider –</span><span class="sxs-lookup"><span data-stu-id="a89e7-279">HelpProvider</span></span>|  
|<span data-ttu-id="a89e7-280">Ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="a89e7-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="a89e7-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="a89e7-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a89e7-282">NumericUpDown</span></span>|  
|<span data-ttu-id="a89e7-283">Panel</span><span class="sxs-lookup"><span data-stu-id="a89e7-283">Panel</span></span>|  
|<span data-ttu-id="a89e7-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="a89e7-284">PictureBox</span></span>|  
|<span data-ttu-id="a89e7-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="a89e7-285">PrintDocument</span></span>|  
|<span data-ttu-id="a89e7-286">PrintPreview – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a89e7-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="a89e7-287">PrintPreview – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="a89e7-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="a89e7-288">Mřížky</span><span class="sxs-lookup"><span data-stu-id="a89e7-288">PropertyGrid</span></span>|  
|<span data-ttu-id="a89e7-289">Type</span><span class="sxs-lookup"><span data-stu-id="a89e7-289">UserControl</span></span>|  
|<span data-ttu-id="a89e7-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a89e7-290">ToolStrip</span></span>|  
|<span data-ttu-id="a89e7-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a89e7-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="a89e7-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="a89e7-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="a89e7-293">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="a89e7-293">Splitter</span></span>|  
|<span data-ttu-id="a89e7-294">Ovládacím RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="a89e7-294">RaftingContainer</span></span>|  
|<span data-ttu-id="a89e7-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="a89e7-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a89e7-296">Viz také</span><span class="sxs-lookup"><span data-stu-id="a89e7-296">See also</span></span>

- [<span data-ttu-id="a89e7-297">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a89e7-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
