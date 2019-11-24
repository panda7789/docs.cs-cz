---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435249"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="e5745-102">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="e5745-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="e5745-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e5745-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e5745-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e5745-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span><span class="sxs-lookup"><span data-stu-id="e5745-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="e5745-106">Links to additional references are listed at the end of the overview.</span><span class="sxs-lookup"><span data-stu-id="e5745-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="e5745-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="e5745-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="e5745-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e5745-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e5745-109">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="e5745-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="e5745-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="e5745-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e5745-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span><span class="sxs-lookup"><span data-stu-id="e5745-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="e5745-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span><span class="sxs-lookup"><span data-stu-id="e5745-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="e5745-113">Typically, it will be the topmost and leftmost row or column.</span><span class="sxs-lookup"><span data-stu-id="e5745-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="e5745-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span><span class="sxs-lookup"><span data-stu-id="e5745-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="e5745-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span><span class="sxs-lookup"><span data-stu-id="e5745-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="e5745-116">Required Members for IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="e5745-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="e5745-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="e5745-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="e5745-118">Required members</span><span class="sxs-lookup"><span data-stu-id="e5745-118">Required members</span></span>|<span data-ttu-id="e5745-119">Member type</span><span class="sxs-lookup"><span data-stu-id="e5745-119">Member type</span></span>|<span data-ttu-id="e5745-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5745-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="e5745-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e5745-121">Property</span></span>|<span data-ttu-id="e5745-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5745-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="e5745-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e5745-123">Property</span></span>|<span data-ttu-id="e5745-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5745-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="e5745-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e5745-125">Property</span></span>|<span data-ttu-id="e5745-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5745-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="e5745-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e5745-127">Property</span></span>|<span data-ttu-id="e5745-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5745-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="e5745-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e5745-129">Property</span></span>|<span data-ttu-id="e5745-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5745-130">None</span></span>|  
  
 <span data-ttu-id="e5745-131">This control pattern has no associated methods or events.</span><span class="sxs-lookup"><span data-stu-id="e5745-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="e5745-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e5745-132">Exceptions</span></span>  
 <span data-ttu-id="e5745-133">This control pattern has no associated exceptions.</span><span class="sxs-lookup"><span data-stu-id="e5745-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5745-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5745-134">See also</span></span>

- [<span data-ttu-id="e5745-135">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e5745-136">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e5745-137">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="e5745-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e5745-138">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="e5745-139">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e5745-140">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5745-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
