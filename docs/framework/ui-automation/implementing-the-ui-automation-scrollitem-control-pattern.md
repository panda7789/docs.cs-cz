---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 1e33a64e66bc084e8cc5f75ece2ac2a4d7ea85aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447135"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="ca9a8-102">Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca9a8-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="ca9a8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ca9a8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="ca9a8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ca9a8-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="ca9a8-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="ca9a8-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="ca9a8-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="ca9a8-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ca9a8-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ca9a8-110">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="ca9a8-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ca9a8-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="ca9a8-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="ca9a8-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="ca9a8-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="ca9a8-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="ca9a8-115">Required Members for IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="ca9a8-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="ca9a8-116">The following method is required for implementing the IScrollProvider interface.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="ca9a8-117">Required members</span><span class="sxs-lookup"><span data-stu-id="ca9a8-117">Required members</span></span>|<span data-ttu-id="ca9a8-118">Member type</span><span class="sxs-lookup"><span data-stu-id="ca9a8-118">Member type</span></span>|<span data-ttu-id="ca9a8-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca9a8-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="ca9a8-120">-   Method</span><span class="sxs-lookup"><span data-stu-id="ca9a8-120">-   Method</span></span>|<span data-ttu-id="ca9a8-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca9a8-121">None</span></span>|  
  
 <span data-ttu-id="ca9a8-122">This control pattern has no associated properties or events.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ca9a8-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ca9a8-123">Exceptions</span></span>  
 <span data-ttu-id="ca9a8-124">Providers must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="ca9a8-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ca9a8-125">Exception Type</span><span class="sxs-lookup"><span data-stu-id="ca9a8-125">Exception Type</span></span>|<span data-ttu-id="ca9a8-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="ca9a8-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="ca9a8-127">If an item cannot be scrolled into view:</span><span class="sxs-lookup"><span data-stu-id="ca9a8-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="ca9a8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca9a8-128">See also</span></span>

- [<span data-ttu-id="ca9a8-129">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca9a8-129">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ca9a8-130">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca9a8-130">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="ca9a8-131">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="ca9a8-131">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ca9a8-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca9a8-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="ca9a8-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca9a8-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
