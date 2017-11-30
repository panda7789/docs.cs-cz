---
title: "Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: daaffd02eaaf7fcb0e64dbcda4bd2ee155163f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="0ecc3-102">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ecc3-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="0ecc3-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0ecc3-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="0ecc3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0ecc3-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>, včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="0ecc3-106">Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="0ecc3-107"><xref:System.Windows.Automation.GridItemPattern> – Vzor ovládacích prvků se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="0ecc3-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc3-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0ecc3-109">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="0ecc3-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0ecc3-110">Při implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="0ecc3-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="0ecc3-111">Souřadnice mřížky jsou od nuly s levé horní buňky s souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="0ecc3-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="0ecc3-112">Sloučené buňky oznámí jejich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> a <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastností na základě jejich základní ukotvení buňky podle definice zprostředkovatele automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="0ecc3-113">Obvykle bude sloupce či řádku nejhornější a nejvíce vlevo.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <span data-ttu-id="0ecc3-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>neposkytuje active manipulace s mřížky například slučování nebo rozdělení buňky.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="0ecc3-115">Určuje, které implementují <xref:System.Windows.Automation.Provider.IGridItemProvider> lze obvykle Procházet (automatizace uživatelského rozhraní klienta můžete přesunout k ovládacím prvkům přiléhající) pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="0ecc3-116">Požadované členy pro IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="0ecc3-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="0ecc3-117">Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="0ecc3-118">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="0ecc3-118">Required members</span></span>|<span data-ttu-id="0ecc3-119">Typ člena</span><span class="sxs-lookup"><span data-stu-id="0ecc3-119">Member type</span></span>|<span data-ttu-id="0ecc3-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ecc3-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="0ecc3-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ecc3-121">Property</span></span>|<span data-ttu-id="0ecc3-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ecc3-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="0ecc3-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ecc3-123">Property</span></span>|<span data-ttu-id="0ecc3-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ecc3-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="0ecc3-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ecc3-125">Property</span></span>|<span data-ttu-id="0ecc3-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ecc3-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="0ecc3-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ecc3-127">Property</span></span>|<span data-ttu-id="0ecc3-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ecc3-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="0ecc3-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ecc3-129">Property</span></span>|<span data-ttu-id="0ecc3-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ecc3-130">None</span></span>|  
  
 <span data-ttu-id="0ecc3-131">Tento vzor ovládacích prvků nemá žádný související metody nebo události.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="0ecc3-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0ecc3-132">Exceptions</span></span>  
 <span data-ttu-id="0ecc3-133">Tento vzor ovládacích prvků nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="0ecc3-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecc3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ecc3-134">See Also</span></span>  
 [<span data-ttu-id="0ecc3-135">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ecc3-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="0ecc3-136">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ecc3-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="0ecc3-137">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="0ecc3-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="0ecc3-138">Implementace vzoru ovládacích prvků uživatelského rozhraní automatizaci mřížky</span><span class="sxs-lookup"><span data-stu-id="0ecc3-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="0ecc3-139">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ecc3-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="0ecc3-140">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ecc3-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
