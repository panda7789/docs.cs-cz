---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180186"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="21dd9-102">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="21dd9-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="21dd9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="21dd9-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="21dd9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="21dd9-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IGridItemProvider>konvence pro implementaci , včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="21dd9-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="21dd9-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="21dd9-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="21dd9-107">Vzor <xref:System.Windows.Automation.GridItemPattern> ovládacího prvku se používá k podpoře <xref:System.Windows.Automation.Provider.IGridProvider>jednotlivých podřízených ovládacích prvků kontejnerů, které implementují .</span><span class="sxs-lookup"><span data-stu-id="21dd9-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="21dd9-108">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="21dd9-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="21dd9-109">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="21dd9-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="21dd9-110">Při provádění <xref:System.Windows.Automation.Provider.IGridProvider>si poznamenejte následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="21dd9-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="21dd9-111">Souřadnice mřížky jsou založeny na nule, přičemž levá horní buňka má souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="21dd9-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="21dd9-112">Sloučené buňky <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> budou vykazovat jejich a vlastnosti na základě jejich základní kotevní buňky definované zprostředkovatelem automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="21dd9-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="21dd9-113">Obvykle se bude jedná o nejvyšší a levý řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="21dd9-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="21dd9-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>nezajišťuje aktivní manipulaci s mřížkou, jako je slučování nebo dělení buněk.</span><span class="sxs-lookup"><span data-stu-id="21dd9-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="21dd9-115">Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IGridItemProvider> lze obvykle procházet (to znamená, že klient automatizace uživatelského rozhraní můžete přesunout do sousedních ovládacích prvků) pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="21dd9-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="21dd9-116">Povinné členy pro IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="21dd9-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="21dd9-117">Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IGridItemProvider>vyžadovány pro implementaci .</span><span class="sxs-lookup"><span data-stu-id="21dd9-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="21dd9-118">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="21dd9-118">Required members</span></span>|<span data-ttu-id="21dd9-119">Typ člena</span><span class="sxs-lookup"><span data-stu-id="21dd9-119">Member type</span></span>|<span data-ttu-id="21dd9-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21dd9-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="21dd9-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="21dd9-121">Property</span></span>|<span data-ttu-id="21dd9-122">Žádný</span><span class="sxs-lookup"><span data-stu-id="21dd9-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="21dd9-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="21dd9-123">Property</span></span>|<span data-ttu-id="21dd9-124">Žádný</span><span class="sxs-lookup"><span data-stu-id="21dd9-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="21dd9-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="21dd9-125">Property</span></span>|<span data-ttu-id="21dd9-126">Žádný</span><span class="sxs-lookup"><span data-stu-id="21dd9-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="21dd9-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="21dd9-127">Property</span></span>|<span data-ttu-id="21dd9-128">Žádný</span><span class="sxs-lookup"><span data-stu-id="21dd9-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="21dd9-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="21dd9-129">Property</span></span>|<span data-ttu-id="21dd9-130">Žádný</span><span class="sxs-lookup"><span data-stu-id="21dd9-130">None</span></span>|  
  
 <span data-ttu-id="21dd9-131">Tento vzor ovládacího prvku nemá žádné přidružené metody nebo události.</span><span class="sxs-lookup"><span data-stu-id="21dd9-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="21dd9-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="21dd9-132">Exceptions</span></span>  
 <span data-ttu-id="21dd9-133">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="21dd9-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dd9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="21dd9-134">See also</span></span>

- [<span data-ttu-id="21dd9-135">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="21dd9-136">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="21dd9-137">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="21dd9-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="21dd9-138">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="21dd9-139">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="21dd9-140">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="21dd9-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
