---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 4883184d75a21efbc08947008baddf31346d7951
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935759"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="b910b-102">Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b910b-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="b910b-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b910b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b910b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b910b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b910b-105">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IScrollItemProvider>nástroje, včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="b910b-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b910b-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="b910b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b910b-107">Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IScrollProvider>. <xref:System.Windows.Automation.ScrollItemPattern></span><span class="sxs-lookup"><span data-stu-id="b910b-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="b910b-108">Tento model ovládacího prvku funguje jako komunikační kanál mezi podřízeným ovládacím prvkem a jeho kontejnerem, aby bylo zajištěno, že kontejner může měnit aktuálně viditelný obsah (nebo oblast) v jeho zobrazení, aby zobrazil podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b910b-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="b910b-109">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b910b-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b910b-110">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="b910b-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b910b-111">Při implementaci vzoru ovládacího prvku položka posouvání si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="b910b-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b910b-112">K implementaci rozhraní IScrollItemProvider nejsou vyžadovány položky obsažené v ovládacím prvku okna nebo plátno.</span><span class="sxs-lookup"><span data-stu-id="b910b-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="b910b-113">Jako alternativu však musí zveřejnit platné umístění pro <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="b910b-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="b910b-114">Tím umožníte, aby klientská aplikace pro automatizaci <xref:System.Windows.Automation.ScrollPattern> uživatelského rozhraní používala metody vzoru ovládacího prvku na kontejneru, aby zobrazila podřízenou položku.</span><span class="sxs-lookup"><span data-stu-id="b910b-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="b910b-115">Vyžadovaná členové pro IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="b910b-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="b910b-116">Následující metoda je vyžadována pro implementaci rozhraní IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="b910b-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="b910b-117">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="b910b-117">Required members</span></span>|<span data-ttu-id="b910b-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="b910b-118">Member type</span></span>|<span data-ttu-id="b910b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b910b-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="b910b-120">-Method</span><span class="sxs-lookup"><span data-stu-id="b910b-120">-   Method</span></span>|<span data-ttu-id="b910b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b910b-121">None</span></span>|  
  
 <span data-ttu-id="b910b-122">Tento model řízení nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="b910b-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b910b-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b910b-123">Exceptions</span></span>  
 <span data-ttu-id="b910b-124">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="b910b-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b910b-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="b910b-125">Exception Type</span></span>|<span data-ttu-id="b910b-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="b910b-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="b910b-127">Pokud se položka nedá posunout do zobrazení:</span><span class="sxs-lookup"><span data-stu-id="b910b-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="b910b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b910b-128">See also</span></span>

- [<span data-ttu-id="b910b-129">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b910b-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b910b-130">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b910b-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b910b-131">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="b910b-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b910b-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b910b-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="b910b-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b910b-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
