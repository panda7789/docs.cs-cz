---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179854"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="73249-102">Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="73249-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="73249-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="73249-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="73249-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="73249-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="73249-105">Toto téma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsahuje informace o podpoře standardních [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]ovládacích prvků v aplikacích vyvinutých pro rozhraní , Win32 a Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="73249-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="73249-106">Ovládací prvky Nadace prezentace systému Windows</span><span class="sxs-lookup"><span data-stu-id="73249-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="73249-107">Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, které poskytují informace nebo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporu pro interakci s uživatelem mají plnou nativní podporu pro .</span><span class="sxs-lookup"><span data-stu-id="73249-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="73249-108">Ostatní prvky, například panely, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nejsou viditelné .</span><span class="sxs-lookup"><span data-stu-id="73249-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="73249-109">Ovládací prvky win32</span><span class="sxs-lookup"><span data-stu-id="73249-109">Win32 Controls</span></span>  
 <span data-ttu-id="73249-110">Většina ovládacích prvků [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 jsou vystaveny prostřednictvím zprostředkovatelů na straně klienta v UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="73249-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="73249-111">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi UI Automation.</span><span class="sxs-lookup"><span data-stu-id="73249-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="73249-112">Plná podpora je poskytována pouze pro ovládací prvky z verze 6 *souboru ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="73249-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="73249-113">Následující ovládací prvky jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="73249-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="73249-114">Název třídy</span><span class="sxs-lookup"><span data-stu-id="73249-114">Class name</span></span>|<span data-ttu-id="73249-115">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="73249-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="73249-116">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-116">Button</span></span>|<span data-ttu-id="73249-117">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-117">Button</span></span>|  
|<span data-ttu-id="73249-118">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-118">Button</span></span>|<span data-ttu-id="73249-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="73249-119">RadioButton</span></span>|  
|<span data-ttu-id="73249-120">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-120">Button</span></span>|<span data-ttu-id="73249-121">Skupina</span><span class="sxs-lookup"><span data-stu-id="73249-121">Group</span></span>|  
|<span data-ttu-id="73249-122">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-122">Button</span></span>|<span data-ttu-id="73249-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="73249-123">CheckBox</span></span>|  
|<span data-ttu-id="73249-124">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-124">Button</span></span>|<span data-ttu-id="73249-125">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="73249-125">Hyperlink</span></span>|  
|<span data-ttu-id="73249-126">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-126">Button</span></span>|<span data-ttu-id="73249-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="73249-127">SplitButton</span></span>|  
|<span data-ttu-id="73249-128">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-128">Button</span></span>|<span data-ttu-id="73249-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="73249-129">CheckBox</span></span>|  
|<span data-ttu-id="73249-130">SeznamKrabičkaEx32</span><span class="sxs-lookup"><span data-stu-id="73249-130">ComboBoxEx32</span></span>|<span data-ttu-id="73249-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="73249-131">ComboBox</span></span>|  
|<span data-ttu-id="73249-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="73249-132">ComboBox</span></span>|<span data-ttu-id="73249-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="73249-133">ComboBox</span></span>|  
|<span data-ttu-id="73249-134">Upravit</span><span class="sxs-lookup"><span data-stu-id="73249-134">Edit</span></span>|<span data-ttu-id="73249-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="73249-135">Document</span></span>|  
|<span data-ttu-id="73249-136">Upravit</span><span class="sxs-lookup"><span data-stu-id="73249-136">Edit</span></span>|<span data-ttu-id="73249-137">Upravit</span><span class="sxs-lookup"><span data-stu-id="73249-137">Edit</span></span>|  
|<span data-ttu-id="73249-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="73249-138">SysLink</span></span>|<span data-ttu-id="73249-139">Hypertextový odkaz</span><span class="sxs-lookup"><span data-stu-id="73249-139">Hyperlink</span></span>|  
|<span data-ttu-id="73249-140">Statická</span><span class="sxs-lookup"><span data-stu-id="73249-140">Static</span></span>|<span data-ttu-id="73249-141">Text</span><span class="sxs-lookup"><span data-stu-id="73249-141">Text</span></span>|  
|<span data-ttu-id="73249-142">Statická</span><span class="sxs-lookup"><span data-stu-id="73249-142">Static</span></span>|<span data-ttu-id="73249-143">Image</span><span class="sxs-lookup"><span data-stu-id="73249-143">Image</span></span>|  
|<span data-ttu-id="73249-144">SysIPAdresa32</span><span class="sxs-lookup"><span data-stu-id="73249-144">SysIPAddress32</span></span>|<span data-ttu-id="73249-145">Vlastní</span><span class="sxs-lookup"><span data-stu-id="73249-145">Custom</span></span>|  
|<span data-ttu-id="73249-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="73249-146">SysHeader32</span></span>|<span data-ttu-id="73249-147">Položka záhlaví nebo záhlaví</span><span class="sxs-lookup"><span data-stu-id="73249-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="73249-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="73249-148">SysListView32</span></span>|<span data-ttu-id="73249-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="73249-149">DataGrid</span></span>|  
|<span data-ttu-id="73249-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="73249-150">SysListView32</span></span>|<span data-ttu-id="73249-151">Seznam</span><span class="sxs-lookup"><span data-stu-id="73249-151">List</span></span>|  
|<span data-ttu-id="73249-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="73249-152">ListBox</span></span>|<span data-ttu-id="73249-153">Seznam</span><span class="sxs-lookup"><span data-stu-id="73249-153">List</span></span>|  
|<span data-ttu-id="73249-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="73249-154">ListBox</span></span>|<span data-ttu-id="73249-155">Listitem</span><span class="sxs-lookup"><span data-stu-id="73249-155">ListItem</span></span>|  
|<span data-ttu-id="73249-156">#32768</span><span class="sxs-lookup"><span data-stu-id="73249-156">#32768</span></span>|<span data-ttu-id="73249-157">Nabídka</span><span class="sxs-lookup"><span data-stu-id="73249-157">Menu</span></span>|  
|<span data-ttu-id="73249-158">#32768</span><span class="sxs-lookup"><span data-stu-id="73249-158">#32768</span></span>|<span data-ttu-id="73249-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="73249-159">MenuItem</span></span>|  
|<span data-ttu-id="73249-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="73249-160">msctls_progress32</span></span>|<span data-ttu-id="73249-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="73249-161">ProgressBar</span></span>|  
|<span data-ttu-id="73249-162">Richedit</span><span class="sxs-lookup"><span data-stu-id="73249-162">RichEdit</span></span>|<span data-ttu-id="73249-163">Dokumentu.</span><span class="sxs-lookup"><span data-stu-id="73249-163">Document.</span></span> <span data-ttu-id="73249-164">Viz poznámka.</span><span class="sxs-lookup"><span data-stu-id="73249-164">See note.</span></span>|  
|<span data-ttu-id="73249-165">Richedit20A</span><span class="sxs-lookup"><span data-stu-id="73249-165">RichEdit20A</span></span>|<span data-ttu-id="73249-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="73249-166">Document</span></span>|  
|<span data-ttu-id="73249-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="73249-167">RichEdit20W</span></span>|<span data-ttu-id="73249-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="73249-168">Document</span></span>|  
|<span data-ttu-id="73249-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="73249-169">RichEdit50W</span></span>|<span data-ttu-id="73249-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="73249-170">Document</span></span>|  
|<span data-ttu-id="73249-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="73249-171">ScrollBar</span></span>|<span data-ttu-id="73249-172">Posuvník</span><span class="sxs-lookup"><span data-stu-id="73249-172">Slider</span></span>|  
|<span data-ttu-id="73249-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="73249-173">msctls_trackbar32</span></span>|<span data-ttu-id="73249-174">Posuvník</span><span class="sxs-lookup"><span data-stu-id="73249-174">Slider</span></span>|  
|<span data-ttu-id="73249-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="73249-175">msctls_updown32</span></span>|<span data-ttu-id="73249-176">Číselník</span><span class="sxs-lookup"><span data-stu-id="73249-176">Spinner</span></span>|  
|<span data-ttu-id="73249-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="73249-177">msctls_statusbar32</span></span>|<span data-ttu-id="73249-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="73249-178">StatusBar</span></span>|  
|<span data-ttu-id="73249-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="73249-179">SysTabControl32</span></span>|<span data-ttu-id="73249-180">Karta</span><span class="sxs-lookup"><span data-stu-id="73249-180">Tab</span></span>|  
|<span data-ttu-id="73249-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="73249-181">SysTabControl32</span></span>|<span data-ttu-id="73249-182">Tabitem</span><span class="sxs-lookup"><span data-stu-id="73249-182">TabItem</span></span>|  
|<span data-ttu-id="73249-183">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-183">ToolbarWindow32</span></span>|<span data-ttu-id="73249-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="73249-184">ToolBar</span></span>|  
|<span data-ttu-id="73249-185">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-185">ToolbarWindow32</span></span>|<span data-ttu-id="73249-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="73249-186">MenuItem</span></span>|  
|<span data-ttu-id="73249-187">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-187">ToolbarWindow32</span></span>|<span data-ttu-id="73249-188">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-188">Button</span></span>|  
|<span data-ttu-id="73249-189">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-189">ToolbarWindow32</span></span>|<span data-ttu-id="73249-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="73249-190">CheckBox</span></span>|  
|<span data-ttu-id="73249-191">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-191">ToolbarWindow32</span></span>|<span data-ttu-id="73249-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="73249-192">RadioButton</span></span>|  
|<span data-ttu-id="73249-193">Panel nástrojůOkno32</span><span class="sxs-lookup"><span data-stu-id="73249-193">ToolbarWindow32</span></span>|<span data-ttu-id="73249-194">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="73249-194">Separator</span></span>|  
|<span data-ttu-id="73249-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="73249-195">tooltips_class32</span></span>|<span data-ttu-id="73249-196">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="73249-196">ToolTip</span></span>|  
|<span data-ttu-id="73249-197">#32774</span><span class="sxs-lookup"><span data-stu-id="73249-197">#32774</span></span>|<span data-ttu-id="73249-198">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="73249-198">ToolTip</span></span>|  
|<span data-ttu-id="73249-199">Okno výztuže32</span><span class="sxs-lookup"><span data-stu-id="73249-199">ReBarWindow32</span></span>|<span data-ttu-id="73249-200">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="73249-200">Toolbar</span></span>|  
|<span data-ttu-id="73249-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="73249-201">SysTreeView32</span></span>|<span data-ttu-id="73249-202">Strom</span><span class="sxs-lookup"><span data-stu-id="73249-202">Tree</span></span>|  
|<span data-ttu-id="73249-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="73249-203">SysTreeView32</span></span>|<span data-ttu-id="73249-204">Treeitem</span><span class="sxs-lookup"><span data-stu-id="73249-204">TreeItem</span></span>|  
  
 <span data-ttu-id="73249-205">**Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v souboru RichEd20.dll verze 3.1 a novější a MsftEdit.dll verze 4.1 a novější).</span><span class="sxs-lookup"><span data-stu-id="73249-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="73249-206">Následující ovládací prvky nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="73249-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="73249-207">Název třídy</span><span class="sxs-lookup"><span data-stu-id="73249-207">Class name</span></span>|<span data-ttu-id="73249-208">Typ ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="73249-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="73249-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="73249-209">SysAnimate32</span></span>|<span data-ttu-id="73249-210">Image</span><span class="sxs-lookup"><span data-stu-id="73249-210">Image</span></span>|  
|<span data-ttu-id="73249-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="73249-211">SysPager</span></span>|<span data-ttu-id="73249-212">Číselník</span><span class="sxs-lookup"><span data-stu-id="73249-212">Spinner</span></span>|  
|<span data-ttu-id="73249-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="73249-213">SysDateTimePick32</span></span>|<span data-ttu-id="73249-214">Vlastní</span><span class="sxs-lookup"><span data-stu-id="73249-214">Custom</span></span>|  
|<span data-ttu-id="73249-215">SysMěsícCal32</span><span class="sxs-lookup"><span data-stu-id="73249-215">SysMonthCal32</span></span>|<span data-ttu-id="73249-216">Kalendář</span><span class="sxs-lookup"><span data-stu-id="73249-216">Calendar</span></span>|  
|<span data-ttu-id="73249-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="73249-217">MS_WINNOTE</span></span>|<span data-ttu-id="73249-218">Popis</span><span class="sxs-lookup"><span data-stu-id="73249-218">Tooltip</span></span>|  
|<span data-ttu-id="73249-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="73249-219">VBBubble</span></span>|<span data-ttu-id="73249-220">Popis</span><span class="sxs-lookup"><span data-stu-id="73249-220">Tooltip</span></span>|  
|<span data-ttu-id="73249-221">ScrollBar (při použití jako samostatný ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="73249-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="73249-222">Posuvník</span><span class="sxs-lookup"><span data-stu-id="73249-222">Slider</span></span>|  
|<span data-ttu-id="73249-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="73249-223">SuperGrid</span></span>|<span data-ttu-id="73249-224">Vlastní</span><span class="sxs-lookup"><span data-stu-id="73249-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="73249-225">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73249-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="73249-226">Ovládací prvky Windows [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Forms jsou vystaveny prostřednictvím zprostředkovatelů na straně klienta v uIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="73249-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="73249-227">Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi UI Automation.</span><span class="sxs-lookup"><span data-stu-id="73249-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="73249-228">Ovládací prvky windows forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]běžné ovládací prvky Win32 jsou podporovány .</span><span class="sxs-lookup"><span data-stu-id="73249-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="73249-229">Následující ovládací prvky jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="73249-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="73249-230">Název třídy</span><span class="sxs-lookup"><span data-stu-id="73249-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="73249-231">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="73249-231">Button</span></span>|  
|<span data-ttu-id="73249-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="73249-232">CheckBox</span></span>|  
|<span data-ttu-id="73249-233">Checkedlistbox</span><span class="sxs-lookup"><span data-stu-id="73249-233">CheckedListBox</span></span>|  
|<span data-ttu-id="73249-234">Colordialog</span><span class="sxs-lookup"><span data-stu-id="73249-234">ColorDialog</span></span>|  
|<span data-ttu-id="73249-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="73249-235">ComboBox</span></span>|  
|<span data-ttu-id="73249-236">Prohlížeč složek</span><span class="sxs-lookup"><span data-stu-id="73249-236">FolderBrowser</span></span>|  
|<span data-ttu-id="73249-237">Fontdialog</span><span class="sxs-lookup"><span data-stu-id="73249-237">FontDialog</span></span>|  
|<span data-ttu-id="73249-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="73249-238">GroupBox</span></span>|  
|<span data-ttu-id="73249-239">Hscrollbar</span><span class="sxs-lookup"><span data-stu-id="73249-239">HscrollBar</span></span>|  
|<span data-ttu-id="73249-240">Imagelist</span><span class="sxs-lookup"><span data-stu-id="73249-240">ImageList</span></span>|  
|<span data-ttu-id="73249-241">Popisek</span><span class="sxs-lookup"><span data-stu-id="73249-241">Label</span></span>|  
|<span data-ttu-id="73249-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="73249-242">ListBox</span></span>|  
|<span data-ttu-id="73249-243">ListView</span><span class="sxs-lookup"><span data-stu-id="73249-243">ListView</span></span>|  
|<span data-ttu-id="73249-244">Hlavní nabídka/kontextová nabídka</span><span class="sxs-lookup"><span data-stu-id="73249-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="73249-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="73249-245">MonthCalendar</span></span>|  
|<span data-ttu-id="73249-246">Notifyicon</span><span class="sxs-lookup"><span data-stu-id="73249-246">NotifyIcon</span></span>|  
|<span data-ttu-id="73249-247">Openfiledialog</span><span class="sxs-lookup"><span data-stu-id="73249-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="73249-248">Pagesetupdialog</span><span class="sxs-lookup"><span data-stu-id="73249-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="73249-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="73249-249">PrintDialog</span></span>|  
|<span data-ttu-id="73249-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="73249-250">ProgressBar</span></span>|  
|<span data-ttu-id="73249-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="73249-251">RadioButton</span></span>|  
|<span data-ttu-id="73249-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="73249-252">RichTextBox</span></span>|  
|<span data-ttu-id="73249-253">Savefiledialog</span><span class="sxs-lookup"><span data-stu-id="73249-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="73249-254">Scrollablecontrol</span><span class="sxs-lookup"><span data-stu-id="73249-254">ScrollableControl</span></span>|  
|<span data-ttu-id="73249-255">Soundplayer</span><span class="sxs-lookup"><span data-stu-id="73249-255">SoundPlayer</span></span>|  
|<span data-ttu-id="73249-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="73249-256">StatusBar</span></span>|  
|<span data-ttu-id="73249-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="73249-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="73249-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="73249-258">TextBox</span></span>|  
|<span data-ttu-id="73249-259">Časovač</span><span class="sxs-lookup"><span data-stu-id="73249-259">Timer</span></span>|  
|<span data-ttu-id="73249-260">Panel nástrojů</span><span class="sxs-lookup"><span data-stu-id="73249-260">Toolbar</span></span>|  
|<span data-ttu-id="73249-261">Popisy tlačítek</span><span class="sxs-lookup"><span data-stu-id="73249-261">ToolTip</span></span>|  
|<span data-ttu-id="73249-262">Trackbar</span><span class="sxs-lookup"><span data-stu-id="73249-262">TrackBar</span></span>|  
|<span data-ttu-id="73249-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="73249-263">TreeView</span></span>|  
|<span data-ttu-id="73249-264">Vscrollbar</span><span class="sxs-lookup"><span data-stu-id="73249-264">VscrollBar</span></span>|  
|<span data-ttu-id="73249-265">Webbrowser</span><span class="sxs-lookup"><span data-stu-id="73249-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="73249-266">Následující ovládací prvky [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jsou vystaveny pouze prostřednictvím jejich podpory pro microsoft active accessibility.</span><span class="sxs-lookup"><span data-stu-id="73249-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="73249-267">Některé funkce nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="73249-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="73249-268">Název ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="73249-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="73249-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="73249-269">BindingSource</span></span>|  
|<span data-ttu-id="73249-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="73249-270">DataGrid</span></span>|  
|<span data-ttu-id="73249-271">Datagridview</span><span class="sxs-lookup"><span data-stu-id="73249-271">DataGridView</span></span>|  
|<span data-ttu-id="73249-272">Datový navigační panel</span><span class="sxs-lookup"><span data-stu-id="73249-272">DataNavigator</span></span>|  
|<span data-ttu-id="73249-273">Domainupdown</span><span class="sxs-lookup"><span data-stu-id="73249-273">DomainUpDown</span></span>|  
|<span data-ttu-id="73249-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="73249-274">ErrorProvider</span></span>|  
|<span data-ttu-id="73249-275">Flowlayoutpanel</span><span class="sxs-lookup"><span data-stu-id="73249-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="73249-276">Formulář</span><span class="sxs-lookup"><span data-stu-id="73249-276">Form</span></span>|  
|<span data-ttu-id="73249-277">Linklabel</span><span class="sxs-lookup"><span data-stu-id="73249-277">LinkLabel</span></span>|  
|<span data-ttu-id="73249-278">Helpprovider</span><span class="sxs-lookup"><span data-stu-id="73249-278">HelpProvider</span></span>|  
|<span data-ttu-id="73249-279">Maskedtextbox</span><span class="sxs-lookup"><span data-stu-id="73249-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="73249-280">Panel Proužka/Kontextový panel MenuStrip</span><span class="sxs-lookup"><span data-stu-id="73249-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="73249-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="73249-281">NumericUpDown</span></span>|  
|<span data-ttu-id="73249-282">Panel</span><span class="sxs-lookup"><span data-stu-id="73249-282">Panel</span></span>|  
|<span data-ttu-id="73249-283">Picturebox</span><span class="sxs-lookup"><span data-stu-id="73249-283">PictureBox</span></span>|  
|<span data-ttu-id="73249-284">Printdocument</span><span class="sxs-lookup"><span data-stu-id="73249-284">PrintDocument</span></span>|  
|<span data-ttu-id="73249-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="73249-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="73249-286">Dialogové okno PrintPreview</span><span class="sxs-lookup"><span data-stu-id="73249-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="73249-287">Propertygrid</span><span class="sxs-lookup"><span data-stu-id="73249-287">PropertyGrid</span></span>|  
|<span data-ttu-id="73249-288">Usercontrol</span><span class="sxs-lookup"><span data-stu-id="73249-288">UserControl</span></span>|  
|<span data-ttu-id="73249-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="73249-289">ToolStrip</span></span>|  
|<span data-ttu-id="73249-290">Tablelayoutpanel</span><span class="sxs-lookup"><span data-stu-id="73249-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="73249-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="73249-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="73249-292">Rozdělovač</span><span class="sxs-lookup"><span data-stu-id="73249-292">Splitter</span></span>|  
|<span data-ttu-id="73249-293">RaftingKontejner</span><span class="sxs-lookup"><span data-stu-id="73249-293">RaftingContainer</span></span>|  
|<span data-ttu-id="73249-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="73249-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73249-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="73249-295">See also</span></span>

- [<span data-ttu-id="73249-296">Typy ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="73249-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
