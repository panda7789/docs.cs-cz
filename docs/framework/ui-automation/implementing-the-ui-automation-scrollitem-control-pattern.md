---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku ovládacích prvků ScrollItem v automatizaci uživatelského rozhraní. Viz povinné členy pro rozhraní IScrollItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163576"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="8bec2-104">Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bec2-104">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8bec2-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8bec2-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8bec2-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8bec2-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8bec2-107">Toto téma obsahuje pokyny a konvence pro implementaci nástroje <xref:System.Windows.Automation.Provider.IScrollItemProvider> , včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="8bec2-107">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="8bec2-108">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="8bec2-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8bec2-109"><xref:System.Windows.Automation.ScrollItemPattern>Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IScrollProvider> .</span><span class="sxs-lookup"><span data-stu-id="8bec2-109">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="8bec2-110">Tento model ovládacího prvku funguje jako komunikační kanál mezi podřízeným ovládacím prvkem a jeho kontejnerem, aby bylo zajištěno, že kontejner může měnit aktuálně viditelný obsah (nebo oblast) v jeho zobrazení, aby zobrazil podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8bec2-110">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="8bec2-111">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8bec2-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8bec2-112">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="8bec2-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8bec2-113">Při implementaci vzoru ovládacího prvku položka posouvání si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="8bec2-113">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8bec2-114">K implementaci rozhraní IScrollItemProvider nejsou vyžadovány položky obsažené v ovládacím prvku okna nebo plátno.</span><span class="sxs-lookup"><span data-stu-id="8bec2-114">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="8bec2-115">Jako alternativu však musí zveřejnit platné umístění pro <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .</span><span class="sxs-lookup"><span data-stu-id="8bec2-115">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="8bec2-116">Tím umožníte, aby klientská aplikace pro automatizaci uživatelského rozhraní používala <xref:System.Windows.Automation.ScrollPattern> metody vzoru ovládacího prvku na kontejneru, aby zobrazila podřízenou položku.</span><span class="sxs-lookup"><span data-stu-id="8bec2-116">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="8bec2-117">Vyžadovaná členové pro IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="8bec2-117">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="8bec2-118">Následující metoda je vyžadována pro implementaci rozhraní IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="8bec2-118">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="8bec2-119">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="8bec2-119">Required members</span></span>|<span data-ttu-id="8bec2-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="8bec2-120">Member type</span></span>|<span data-ttu-id="8bec2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bec2-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="8bec2-122">-Method</span><span class="sxs-lookup"><span data-stu-id="8bec2-122">-   Method</span></span>|<span data-ttu-id="8bec2-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="8bec2-123">None</span></span>|  
  
 <span data-ttu-id="8bec2-124">Tento model řízení nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="8bec2-124">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="8bec2-125">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8bec2-125">Exceptions</span></span>  
 <span data-ttu-id="8bec2-126">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="8bec2-126">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8bec2-127">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="8bec2-127">Exception Type</span></span>|<span data-ttu-id="8bec2-128">Podmínka</span><span class="sxs-lookup"><span data-stu-id="8bec2-128">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="8bec2-129">Pokud se položka nedá posunout do zobrazení:</span><span class="sxs-lookup"><span data-stu-id="8bec2-129">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="8bec2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bec2-130">See also</span></span>

- [<span data-ttu-id="8bec2-131">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bec2-131">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8bec2-132">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bec2-132">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8bec2-133">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="8bec2-133">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8bec2-134">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bec2-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8bec2-135">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bec2-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
