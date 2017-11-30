---
title: "Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 68c3dcdb1d8f15f312dea40ae59a3b1a4736c484
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="5d71c-102">Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d71c-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5d71c-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d71c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5d71c-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5d71c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5d71c-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IDockProvider>, včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="5d71c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="5d71c-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="5d71c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5d71c-107"><xref:System.Windows.Automation.DockPattern> – Vzor ovládacích prvků se používá k vystavení vlastností ukotvení ovládacího prvku do kontejneru, ukotvení.</span><span class="sxs-lookup"><span data-stu-id="5d71c-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="5d71c-108">Ukotvení kontejner je ovládací prvek, který umožňuje uspořádat podřízené elementy vodorovně a svisle, relativně k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="5d71c-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="5d71c-109">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5d71c-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="5d71c-110">![Ukotvení kontejner s dvěma ukotveného podřízené objekty. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="5d71c-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="5d71c-111">Ukotvení příklad ze sady Visual Studio, kde je okno "Zobrazení tříd" DockPosition.Right a v okně "Seznam chyb" je DockPosition.Bottom</span><span class="sxs-lookup"><span data-stu-id="5d71c-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5d71c-112">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="5d71c-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5d71c-113">Když implementace vzoru ovládacích prvků ukotvení, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="5d71c-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="5d71c-114"><xref:System.Windows.Automation.Provider.IDockProvider>nevystavuje žádné vlastnosti ukotvení kontejneru nebo vlastnosti ovládacích prvků, které jsou ukotven přiléhající k aktuální ovládací prvek v rámci kontejneru ukotvení.</span><span class="sxs-lookup"><span data-stu-id="5d71c-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="5d71c-115">Ovládací prvky jsou ukotven relativně k sobě navzájem podle jejich aktuálního pořadí z-order; vyšší jejich pořadí z-order umístění dále jsou umístěny z zadaný okraj ukotvení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5d71c-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="5d71c-116">Pokud se změnila velikost ukotvení kontejneru, všechny ukotvených ovládacích prvků v kontejneru přemístí vyprázdnit na stejnou hranici, do které byly původně ukotven.</span><span class="sxs-lookup"><span data-stu-id="5d71c-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="5d71c-117">Ukotvených ovládacích prvků bude taky změnit velikost, aby vyplnilo veškeré místo v kontejneru podle ukotvení chování jejich <xref:System.Windows.Automation.DockPosition>.</span><span class="sxs-lookup"><span data-stu-id="5d71c-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="5d71c-118">Například pokud <xref:System.Windows.Automation.DockPosition.Top> není zadaný, aby vyplnilo veškeré dostupné místo bude rozšiřovat levé a pravé straně ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d71c-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="5d71c-119">Pokud <xref:System.Windows.Automation.DockPosition.Fill> není zadaný, aby vyplnilo veškeré dostupné místo se rozbalí všechny čtyři strany ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d71c-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="5d71c-120">V několika monitorování systému by měl ovládacích prvků ukotvení levé nebo pravé straně aktuálního monitorování.</span><span class="sxs-lookup"><span data-stu-id="5d71c-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="5d71c-121">Pokud tento způsob není možný, že by měl ukotvení na levé straně krajní levé monitorování nebo pravé straně úplně vpravo monitorování.</span><span class="sxs-lookup"><span data-stu-id="5d71c-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="5d71c-122">Požadované členy pro IDockProvider</span><span class="sxs-lookup"><span data-stu-id="5d71c-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="5d71c-123">Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IDockProvider.</span><span class="sxs-lookup"><span data-stu-id="5d71c-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="5d71c-124">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="5d71c-124">Required members</span></span>|<span data-ttu-id="5d71c-125">Typ člena</span><span class="sxs-lookup"><span data-stu-id="5d71c-125">Member type</span></span>|<span data-ttu-id="5d71c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d71c-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="5d71c-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5d71c-127">Property</span></span>|<span data-ttu-id="5d71c-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="5d71c-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="5d71c-129">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d71c-129">Method</span></span>|<span data-ttu-id="5d71c-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="5d71c-130">None</span></span>|  
  
 <span data-ttu-id="5d71c-131">Tento vzor ovládacích prvků nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="5d71c-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5d71c-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5d71c-132">Exceptions</span></span>  
 <span data-ttu-id="5d71c-133">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="5d71c-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5d71c-134">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5d71c-134">Exception type</span></span>|<span data-ttu-id="5d71c-135">Podmínka</span><span class="sxs-lookup"><span data-stu-id="5d71c-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="5d71c-136">– Když není provést styl ukotvení požadovaný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5d71c-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d71c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d71c-137">See Also</span></span>  
 [<span data-ttu-id="5d71c-138">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d71c-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="5d71c-139">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d71c-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="5d71c-140">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="5d71c-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="5d71c-141">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d71c-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="5d71c-142">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d71c-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
