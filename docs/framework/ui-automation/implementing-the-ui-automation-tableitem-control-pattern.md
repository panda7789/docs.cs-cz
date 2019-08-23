---
title: Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 8f368fee6df6ebe5455f2029670e90f036d3d89a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932096"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="9a3dd-102">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9a3dd-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9a3dd-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9a3dd-105">Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.ITableItemProvider>implementaci, včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="9a3dd-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9a3dd-107">Vzor ovládacího prvku slouží k podpoře podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.ITableProvider>. <xref:System.Windows.Automation.TableItemPattern></span><span class="sxs-lookup"><span data-stu-id="9a3dd-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="9a3dd-108">Přístup k funkcím jednotlivých buněk je poskytován požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="9a3dd-109">Tento vzor ovládacího prvku je podobný <xref:System.Windows.Automation.Provider.IGridItemProvider> rozlišení, že implementující <xref:System.Windows.Automation.Provider.ITableItemProvider> ovládací prvky musí programově zveřejnit vztah mezi jednotlivou buňkou a informace o řádku a sloupci.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="9a3dd-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9a3dd-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9a3dd-111">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="9a3dd-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="9a3dd-112">Pro související funkce položky mřížky si přečtěte téma [implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9a3dd-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="9a3dd-113">Vyžadovaná členové pro ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="9a3dd-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="9a3dd-114">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="9a3dd-114">Required member</span></span>|<span data-ttu-id="9a3dd-115">Typ člena</span><span class="sxs-lookup"><span data-stu-id="9a3dd-115">Member type</span></span>|<span data-ttu-id="9a3dd-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a3dd-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="9a3dd-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a3dd-117">Method</span></span>|<span data-ttu-id="9a3dd-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="9a3dd-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="9a3dd-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a3dd-119">Method</span></span>|<span data-ttu-id="9a3dd-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="9a3dd-120">None</span></span>|  
  
 <span data-ttu-id="9a3dd-121">Tento model řízení nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9a3dd-122">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9a3dd-122">Exceptions</span></span>  
 <span data-ttu-id="9a3dd-123">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="9a3dd-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3dd-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a3dd-124">See also</span></span>

- [<span data-ttu-id="9a3dd-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9a3dd-126">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9a3dd-127">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="9a3dd-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9a3dd-128">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="9a3dd-129">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="9a3dd-130">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="9a3dd-131">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a3dd-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
