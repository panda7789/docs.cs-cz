---
title: Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: db94a1a4588c2f889da8adb1cb3e47e208ce1211
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393714"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="11028-102">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="11028-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11028-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="11028-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="11028-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="11028-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.ITableItemProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="11028-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="11028-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="11028-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="11028-107"><xref:System.Windows.Automation.TableItemPattern> – Vzor ovládacích prvků slouží k podpoře podřízené ovládací prvky kontejnerů, které implementují <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="11028-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="11028-108">Poskytuje přístup k funkcím jednotlivé buňky vyžaduje souběžné provádění <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="11028-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="11028-109">Tento vzor ovládacích prvků je obdobou <xref:System.Windows.Automation.Provider.IGridItemProvider> s rozlišovat, že žádné řídicí implementace <xref:System.Windows.Automation.Provider.ITableItemProvider> musí zveřejnit prostřednictvím kódu programu vztah mezi jednotlivé buňky a její informace řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="11028-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="11028-110">Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="11028-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="11028-111">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="11028-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="11028-112">Funkci související mřížce položky, naleznete v tématu [implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="11028-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="11028-113">Požadované členy pro ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="11028-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="11028-114">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="11028-114">Required member</span></span>|<span data-ttu-id="11028-115">Typ člena</span><span class="sxs-lookup"><span data-stu-id="11028-115">Member type</span></span>|<span data-ttu-id="11028-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11028-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="11028-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="11028-117">Method</span></span>|<span data-ttu-id="11028-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="11028-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="11028-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="11028-119">Method</span></span>|<span data-ttu-id="11028-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="11028-120">None</span></span>|  
  
 <span data-ttu-id="11028-121">Tento model ovládací prvek nemá žádné přidružené vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="11028-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="11028-122">Výjimky</span><span class="sxs-lookup"><span data-stu-id="11028-122">Exceptions</span></span>  
 <span data-ttu-id="11028-123">Tento model ovládací prvek nemá žádné související výjimky.</span><span class="sxs-lookup"><span data-stu-id="11028-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11028-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="11028-124">See Also</span></span>  
 [<span data-ttu-id="11028-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="11028-126">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="11028-127">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="11028-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="11028-128">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="11028-129">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="11028-130">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="11028-131">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="11028-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
