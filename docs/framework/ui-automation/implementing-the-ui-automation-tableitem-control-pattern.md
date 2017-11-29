---
title: "Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="83a4e-102">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="83a4e-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83a4e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="83a4e-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="83a4e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="83a4e-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableItemProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83a4e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="83a4e-106">Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="83a4e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="83a4e-107"><xref:System.Windows.Automation.TableItemPattern> – Vzor ovládacích prvků se používá pro podporu podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="83a4e-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="83a4e-108">Požadované souběžná implementace poskytuje přístup k funkcím jednotlivých buněk <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="83a4e-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="83a4e-109">Tento vzor ovládacích prvků je podobná <xref:System.Windows.Automation.Provider.IGridItemProvider> s rozdíl, že všechny řídí, implementace <xref:System.Windows.Automation.Provider.ITableItemProvider> musí prostřednictvím kódu programu vystavit vztah mezi jednotlivých buněk a jeho informace řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="83a4e-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="83a4e-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="83a4e-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="83a4e-111">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="83a4e-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="83a4e-112">Funkce související mřížky položky, naleznete v části [implementace vzoru ovládacích prvků uživatelského rozhraní automatizaci GridItem](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="83a4e-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="83a4e-113">Požadované členy pro ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="83a4e-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="83a4e-114">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="83a4e-114">Required member</span></span>|<span data-ttu-id="83a4e-115">Typ člena</span><span class="sxs-lookup"><span data-stu-id="83a4e-115">Member type</span></span>|<span data-ttu-id="83a4e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83a4e-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="83a4e-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="83a4e-117">Method</span></span>|<span data-ttu-id="83a4e-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="83a4e-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="83a4e-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="83a4e-119">Method</span></span>|<span data-ttu-id="83a4e-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="83a4e-120">None</span></span>|  
  
 <span data-ttu-id="83a4e-121">Tento vzor ovládacích prvků nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="83a4e-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="83a4e-122">Výjimky</span><span class="sxs-lookup"><span data-stu-id="83a4e-122">Exceptions</span></span>  
 <span data-ttu-id="83a4e-123">Tento vzor ovládacích prvků nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="83a4e-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a4e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="83a4e-124">See Also</span></span>  
 [<span data-ttu-id="83a4e-125">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="83a4e-126">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="83a4e-127">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="83a4e-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="83a4e-128">Implementace vzoru ovládacích prvků uživatelského rozhraní automatizace tabulka</span><span class="sxs-lookup"><span data-stu-id="83a4e-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="83a4e-129">Implementace vzoru GridItem ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="83a4e-130">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="83a4e-131">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="83a4e-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
