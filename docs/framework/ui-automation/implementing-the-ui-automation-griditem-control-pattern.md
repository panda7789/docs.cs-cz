---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: fdaac3cad61f6047201587e48d4377fa61b868af
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043406"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="afcc4-102">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="afcc4-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="afcc4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="afcc4-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="afcc4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="afcc4-105">Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IGridItemProvider>implementaci, včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="afcc4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="afcc4-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="afcc4-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="afcc4-107">Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider>. <xref:System.Windows.Automation.GridItemPattern></span><span class="sxs-lookup"><span data-stu-id="afcc4-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="afcc4-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="afcc4-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="afcc4-109">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="afcc4-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="afcc4-110">Při implementaci <xref:System.Windows.Automation.Provider.IGridProvider>nástroje si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="afcc4-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="afcc4-111">Souřadnice mřížky jsou vypočítány od nuly s horní levou buňkou, která má souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="afcc4-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="afcc4-112">Sloučené buňky budou nahlásit <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> své <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti a vlastnostmi na základě jejich podkladové buňky ukotvení, jak jsou definovány zprostředkovatelem automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="afcc4-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="afcc4-113">Obvykle se jedná o horní a levý řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="afcc4-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="afcc4-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>neposkytuje aktivní manipulaci s mřížkou, jako je například sloučení nebo rozdělení buněk.</span><span class="sxs-lookup"><span data-stu-id="afcc4-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="afcc4-115">Ovládací prvky, <xref:System.Windows.Automation.Provider.IGridItemProvider> které implementují, je obvykle možné procházet (to znamená, že se klient automatizace uživatelského rozhraní může přesunout na sousedící ovládací prvky) pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="afcc4-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="afcc4-116">Vyžadovaná členové pro IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="afcc4-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="afcc4-117">Pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="afcc4-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="afcc4-118">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="afcc4-118">Required members</span></span>|<span data-ttu-id="afcc4-119">Typ člena</span><span class="sxs-lookup"><span data-stu-id="afcc4-119">Member type</span></span>|<span data-ttu-id="afcc4-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afcc4-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="afcc4-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="afcc4-121">Property</span></span>|<span data-ttu-id="afcc4-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="afcc4-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="afcc4-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="afcc4-123">Property</span></span>|<span data-ttu-id="afcc4-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="afcc4-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="afcc4-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="afcc4-125">Property</span></span>|<span data-ttu-id="afcc4-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="afcc4-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="afcc4-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="afcc4-127">Property</span></span>|<span data-ttu-id="afcc4-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="afcc4-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="afcc4-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="afcc4-129">Property</span></span>|<span data-ttu-id="afcc4-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="afcc4-130">None</span></span>|  
  
 <span data-ttu-id="afcc4-131">Tento model řízení nemá žádné přidružené metody nebo události.</span><span class="sxs-lookup"><span data-stu-id="afcc4-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="afcc4-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="afcc4-132">Exceptions</span></span>  
 <span data-ttu-id="afcc4-133">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="afcc4-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afcc4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afcc4-134">See also</span></span>

- [<span data-ttu-id="afcc4-135">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="afcc4-136">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="afcc4-137">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="afcc4-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="afcc4-138">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="afcc4-139">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="afcc4-140">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="afcc4-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
