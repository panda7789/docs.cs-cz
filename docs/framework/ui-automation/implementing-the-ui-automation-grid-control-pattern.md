---
title: "Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
caps.latest.revision: "27"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 123bc1454a58391bc6503fd3f60d477fd5498306
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="eab28-102">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="eab28-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="eab28-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="eab28-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="eab28-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="eab28-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, včetně informací o události, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="eab28-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="eab28-106">Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="eab28-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="eab28-107"><xref:System.Windows.Automation.GridPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="eab28-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="eab28-108">Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.IGridItemProvider> a být uspořádány do dvourozměrná logické systém souřadnic, který lze procházet podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="eab28-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="eab28-109">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="eab28-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="eab28-110">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="eab28-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="eab28-111">Když implementace vzoru ovládacích prvků mřížka, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="eab28-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="eab28-112">Souřadnice mřížky jsou od nuly s horní levý (nebo horní pravé buňky v závislosti na národní prostředí) s souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="eab28-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="eab28-113">Pokud buňku je prázdná, prvku automatizace uživatelského rozhraní musí být vrácen stále za účelem podpory <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> vlastnost pro dané buňky.</span><span class="sxs-lookup"><span data-stu-id="eab28-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="eab28-114">To je možné, pokud je podobná nepravidelné pole rozložení podřízených elementů v mřížce (viz následující příklad).</span><span class="sxs-lookup"><span data-stu-id="eab28-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="eab28-115">![Průzkumník Windows zobrazení zobrazující nepravidelné rozložení. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="eab28-115">![Windows Explorer view showing ragged layout.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="eab28-116">Příklad ovládacího prvku mřížky s prázdnou souřadnice</span><span class="sxs-lookup"><span data-stu-id="eab28-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
-   <span data-ttu-id="eab28-117">Mřížka s jednou položkou je stále vyžadují k implementaci <xref:System.Windows.Automation.Provider.IGridProvider> Pokud logicky se považuje za mřížka.</span><span class="sxs-lookup"><span data-stu-id="eab28-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="eab28-118">Počet podřízené položky v mřížce je důležité.</span><span class="sxs-lookup"><span data-stu-id="eab28-118">The number of child items in the grid is immaterial.</span></span>  
  
-   <span data-ttu-id="eab28-119">Skryté řádky a sloupce, v závislosti na implementaci zprostředkovatele, mohou být načteny v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a proto budou promítnuta <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> a <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eab28-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="eab28-120">Pokud dosud nebyly byl načteny skryté řádky a sloupce, by neměly být započítány.</span><span class="sxs-lookup"><span data-stu-id="eab28-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
-   <span data-ttu-id="eab28-121"><xref:System.Windows.Automation.Provider.IGridProvider>neumožňuje active zpracování mřížka; <xref:System.Windows.Automation.Provider.ITransformProvider> Pokud chcete tuto funkci povolit, musí být implementována.</span><span class="sxs-lookup"><span data-stu-id="eab28-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
-   <span data-ttu-id="eab28-122">Použití <xref:System.Windows.Automation.StructureChangedEventHandler> naslouchat strukturálních nebo rozložení mřížky například buněk, které jste přidali, odebrat nebo sloučit změny.</span><span class="sxs-lookup"><span data-stu-id="eab28-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
-   <span data-ttu-id="eab28-123">Použití <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> sledovat traversal prostřednictvím položky nebo buněk mřížka.</span><span class="sxs-lookup"><span data-stu-id="eab28-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="eab28-124">Požadované členy pro IGridProvider</span><span class="sxs-lookup"><span data-stu-id="eab28-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="eab28-125">Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="eab28-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="eab28-126">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="eab28-126">Required members</span></span>|<span data-ttu-id="eab28-127">Typ</span><span class="sxs-lookup"><span data-stu-id="eab28-127">Type</span></span>|<span data-ttu-id="eab28-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eab28-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="eab28-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="eab28-129">Property</span></span>|<span data-ttu-id="eab28-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="eab28-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="eab28-131">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="eab28-131">Property</span></span>|<span data-ttu-id="eab28-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="eab28-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="eab28-133">Metoda</span><span class="sxs-lookup"><span data-stu-id="eab28-133">Method</span></span>|<span data-ttu-id="eab28-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="eab28-134">None</span></span>|  
  
 <span data-ttu-id="eab28-135">Tento vzor ovládacích prvků nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="eab28-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="eab28-136">Výjimky</span><span class="sxs-lookup"><span data-stu-id="eab28-136">Exceptions</span></span>  
 <span data-ttu-id="eab28-137">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="eab28-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="eab28-138">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="eab28-138">Exception type</span></span>|<span data-ttu-id="eab28-139">Podmínka</span><span class="sxs-lookup"><span data-stu-id="eab28-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="eab28-140">– Pokud souřadnice požadovaný řádek je větší než <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> nebo souřadnici sloupec je větší než <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span><span class="sxs-lookup"><span data-stu-id="eab28-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="eab28-141">– Pokud některý z požadovaný řádek nebo sloupec souřadnice je menší než nula.</span><span class="sxs-lookup"><span data-stu-id="eab28-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eab28-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="eab28-142">See Also</span></span>  
 [<span data-ttu-id="eab28-143">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="eab28-144">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="eab28-145">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="eab28-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="eab28-146">Implementace vzoru GridItem ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-146">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="eab28-147">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-147">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="eab28-148">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab28-148">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
