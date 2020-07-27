---
title: Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku TableItem v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní ITableItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163525"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="029ba-104">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-104">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="029ba-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="029ba-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="029ba-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="029ba-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="029ba-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableItemProvider> , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="029ba-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="029ba-108">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="029ba-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="029ba-109"><xref:System.Windows.Automation.TableItemPattern>Vzor ovládacího prvku slouží k podpoře podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.ITableProvider> .</span><span class="sxs-lookup"><span data-stu-id="029ba-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="029ba-110">Přístup k funkcím jednotlivých buněk je poskytován požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="029ba-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="029ba-111">Tento vzor ovládacího prvku je podobný <xref:System.Windows.Automation.Provider.IGridItemProvider> rozlišení, že implementující ovládací prvky <xref:System.Windows.Automation.Provider.ITableItemProvider> musí programově zveřejnit vztah mezi jednotlivou buňkou a informace o řádku a sloupci.</span><span class="sxs-lookup"><span data-stu-id="029ba-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="029ba-112">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="029ba-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="029ba-113">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="029ba-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="029ba-114">Pro související funkce položky mřížky si přečtěte téma [implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="029ba-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="029ba-115">Vyžadovaná členové pro ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="029ba-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="029ba-116">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="029ba-116">Required member</span></span>|<span data-ttu-id="029ba-117">Typ člena</span><span class="sxs-lookup"><span data-stu-id="029ba-117">Member type</span></span>|<span data-ttu-id="029ba-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="029ba-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="029ba-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="029ba-119">Method</span></span>|<span data-ttu-id="029ba-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="029ba-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="029ba-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="029ba-121">Method</span></span>|<span data-ttu-id="029ba-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="029ba-122">None</span></span>|  
  
 <span data-ttu-id="029ba-123">Tento model řízení nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="029ba-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="029ba-124">Výjimky</span><span class="sxs-lookup"><span data-stu-id="029ba-124">Exceptions</span></span>  
 <span data-ttu-id="029ba-125">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="029ba-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029ba-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="029ba-126">See also</span></span>

- [<span data-ttu-id="029ba-127">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="029ba-128">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="029ba-129">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="029ba-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="029ba-130">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="029ba-131">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="029ba-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="029ba-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="029ba-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
