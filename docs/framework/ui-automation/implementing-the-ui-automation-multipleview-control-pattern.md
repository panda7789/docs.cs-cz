---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: c9199e0ea1971c22bfc1f6334b9d2d9d73bb048c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435053"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="74c94-102">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c94-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="74c94-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="74c94-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="74c94-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="74c94-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="74c94-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span><span class="sxs-lookup"><span data-stu-id="74c94-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="74c94-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="74c94-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="74c94-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span><span class="sxs-lookup"><span data-stu-id="74c94-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="74c94-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span><span class="sxs-lookup"><span data-stu-id="74c94-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="74c94-109">The supported views are determined by the control developer and are specific to each control.</span><span class="sxs-lookup"><span data-stu-id="74c94-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="74c94-110">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="74c94-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="74c94-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="74c94-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="74c94-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span><span class="sxs-lookup"><span data-stu-id="74c94-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="74c94-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span><span class="sxs-lookup"><span data-stu-id="74c94-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="74c94-114">A control that is able to sort its content is not considered to support multiple views.</span><span class="sxs-lookup"><span data-stu-id="74c94-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="74c94-115">The collection of views must be identical across instances.</span><span class="sxs-lookup"><span data-stu-id="74c94-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="74c94-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span><span class="sxs-lookup"><span data-stu-id="74c94-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="74c94-117">Required Members for IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="74c94-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="74c94-118">The following properties and methods are required for implementing IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="74c94-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="74c94-119">Required members</span><span class="sxs-lookup"><span data-stu-id="74c94-119">Required members</span></span>|<span data-ttu-id="74c94-120">Member type</span><span class="sxs-lookup"><span data-stu-id="74c94-120">Member type</span></span>|<span data-ttu-id="74c94-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74c94-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="74c94-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="74c94-122">Property</span></span>|<span data-ttu-id="74c94-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="74c94-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="74c94-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="74c94-124">Method</span></span>|<span data-ttu-id="74c94-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="74c94-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="74c94-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="74c94-126">Method</span></span>|<span data-ttu-id="74c94-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="74c94-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="74c94-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="74c94-128">Method</span></span>|<span data-ttu-id="74c94-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="74c94-129">None</span></span>|  
  
 <span data-ttu-id="74c94-130">There are no events associated with this control pattern.</span><span class="sxs-lookup"><span data-stu-id="74c94-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="74c94-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="74c94-131">Exceptions</span></span>  
 <span data-ttu-id="74c94-132">Provider must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="74c94-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="74c94-133">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="74c94-133">Exception type</span></span>|<span data-ttu-id="74c94-134">Podmínka</span><span class="sxs-lookup"><span data-stu-id="74c94-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="74c94-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span><span class="sxs-lookup"><span data-stu-id="74c94-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74c94-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74c94-136">See also</span></span>

- [<span data-ttu-id="74c94-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c94-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="74c94-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c94-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="74c94-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="74c94-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="74c94-140">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c94-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="74c94-141">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c94-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
