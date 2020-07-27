---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
description: Pokyny a konvence pro implementaci vzoru ovládacích prvků GridItemPattern pro položky mřížky v automatizaci uživatelského rozhraní. Viz povinné členy pro IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165818"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="cf16e-104">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="cf16e-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cf16e-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cf16e-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cf16e-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cf16e-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider> , včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="cf16e-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="cf16e-108">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="cf16e-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="cf16e-109"><xref:System.Windows.Automation.GridItemPattern>Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="cf16e-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="cf16e-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cf16e-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cf16e-111">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="cf16e-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cf16e-112">Při implementaci nástroje <xref:System.Windows.Automation.Provider.IGridProvider> si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="cf16e-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="cf16e-113">Souřadnice mřížky jsou vypočítány od nuly s horní levou buňkou, která má souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="cf16e-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="cf16e-114">Sloučené buňky budou nahlásit <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> své <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti a vlastnostmi na základě jejich podkladové buňky ukotvení, jak jsou definovány zprostředkovatelem automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf16e-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="cf16e-115">Obvykle se jedná o horní a levý řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="cf16e-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="cf16e-116"><xref:System.Windows.Automation.Provider.IGridItemProvider>neposkytuje aktivní manipulaci s mřížkou, jako je například sloučení nebo rozdělení buněk.</span><span class="sxs-lookup"><span data-stu-id="cf16e-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="cf16e-117">Ovládací prvky, které implementují, <xref:System.Windows.Automation.Provider.IGridItemProvider> je obvykle možné procházet (to znamená, že se klient automatizace uživatelského rozhraní může přesunout na sousedící ovládací prvky) pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="cf16e-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="cf16e-118">Vyžadovaná členové pro IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="cf16e-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="cf16e-119">Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="cf16e-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="cf16e-120">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="cf16e-120">Required members</span></span>|<span data-ttu-id="cf16e-121">Typ člena</span><span class="sxs-lookup"><span data-stu-id="cf16e-121">Member type</span></span>|<span data-ttu-id="cf16e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf16e-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="cf16e-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cf16e-123">Property</span></span>|<span data-ttu-id="cf16e-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf16e-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="cf16e-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cf16e-125">Property</span></span>|<span data-ttu-id="cf16e-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf16e-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="cf16e-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cf16e-127">Property</span></span>|<span data-ttu-id="cf16e-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf16e-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="cf16e-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cf16e-129">Property</span></span>|<span data-ttu-id="cf16e-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf16e-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="cf16e-131">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cf16e-131">Property</span></span>|<span data-ttu-id="cf16e-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf16e-132">None</span></span>|  
  
 <span data-ttu-id="cf16e-133">Tento model řízení nemá žádné přidružené metody nebo události.</span><span class="sxs-lookup"><span data-stu-id="cf16e-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="cf16e-134">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cf16e-134">Exceptions</span></span>  
 <span data-ttu-id="cf16e-135">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="cf16e-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf16e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf16e-136">See also</span></span>

- [<span data-ttu-id="cf16e-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cf16e-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="cf16e-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="cf16e-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cf16e-140">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="cf16e-141">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="cf16e-142">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf16e-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
