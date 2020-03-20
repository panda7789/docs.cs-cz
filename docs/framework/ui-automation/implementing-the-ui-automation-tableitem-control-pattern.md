---
title: Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f35b491c31e8725eac0025dfd6815079d0ea9b79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180081"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="9a081-102">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9a081-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="9a081-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9a081-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9a081-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9a081-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ITableItemProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="9a081-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="9a081-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="9a081-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9a081-107">Vzor <xref:System.Windows.Automation.TableItemPattern> ovládacího prvku se používá k <xref:System.Windows.Automation.Provider.ITableProvider>podpoře podřízené ovládací prvky kontejnerů, které implementují .</span><span class="sxs-lookup"><span data-stu-id="9a081-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="9a081-108">Přístup k funkcím jednotlivých buněk je zajištěn <xref:System.Windows.Automation.Provider.IGridItemProvider>požadovanou souběžnou implementací aplikace .</span><span class="sxs-lookup"><span data-stu-id="9a081-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="9a081-109">Tento vzor ovládacího prvku <xref:System.Windows.Automation.Provider.IGridItemProvider> je obdobou s <xref:System.Windows.Automation.Provider.ITableItemProvider> rozdílem, že každý ovládací prvek provádění musí programově vystavit vztah mezi jednotlivé buňky a její řádek a sloupec informace.</span><span class="sxs-lookup"><span data-stu-id="9a081-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="9a081-110">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9a081-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9a081-111">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="9a081-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="9a081-112">Související funkce položky mřížky naleznete [v tématu Implementace řídicího vzoru gridpoložky automatizace uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9a081-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="9a081-113">Povinné členy pro ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="9a081-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="9a081-114">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="9a081-114">Required member</span></span>|<span data-ttu-id="9a081-115">Typ člena</span><span class="sxs-lookup"><span data-stu-id="9a081-115">Member type</span></span>|<span data-ttu-id="9a081-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a081-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="9a081-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a081-117">Method</span></span>|<span data-ttu-id="9a081-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="9a081-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="9a081-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a081-119">Method</span></span>|<span data-ttu-id="9a081-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="9a081-120">None</span></span>|  
  
 <span data-ttu-id="9a081-121">Tento vzor ovládacího prvku nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="9a081-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="9a081-122">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9a081-122">Exceptions</span></span>  
 <span data-ttu-id="9a081-123">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="9a081-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a081-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a081-124">See also</span></span>

- [<span data-ttu-id="9a081-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9a081-126">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9a081-127">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="9a081-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9a081-128">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="9a081-129">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="9a081-130">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9a081-131">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a081-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
