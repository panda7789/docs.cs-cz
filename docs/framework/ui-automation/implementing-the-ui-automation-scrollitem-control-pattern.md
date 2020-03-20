---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 3a0647ab98dcb86306573a0e9826fa7232fa9ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180141"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="198cc-102">Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="198cc-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="198cc-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="198cc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="198cc-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="198cc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="198cc-105">Toto téma představuje pokyny a konvence <xref:System.Windows.Automation.Provider.IScrollItemProvider>pro implementaci , včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="198cc-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="198cc-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="198cc-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="198cc-107">Vzor <xref:System.Windows.Automation.ScrollItemPattern> ovládacího prvku se používá k podpoře <xref:System.Windows.Automation.Provider.IScrollProvider>jednotlivých podřízených ovládacích prvků kontejnerů, které implementují .</span><span class="sxs-lookup"><span data-stu-id="198cc-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="198cc-108">Tento vzor ovládacího prvku funguje jako komunikační kanál mezi podřízeným ovládacím prvkem a jeho kontejnerem, aby bylo zajištěno, že kontejner může změnit aktuálně viditelný obsah (nebo oblast) v rámci svého výřezu a zobrazit podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="198cc-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="198cc-109">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="198cc-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="198cc-110">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="198cc-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="198cc-111">Při implementaci vzor ovládacího prvku Scroll Item si poznamenejte následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="198cc-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="198cc-112">Položky obsažené v ovládacím prvku Window nebo Canvas nejsou nutné k implementaci rozhraní IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="198cc-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="198cc-113">Jako alternativu však musí vystavit platné <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>umístění pro .</span><span class="sxs-lookup"><span data-stu-id="198cc-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="198cc-114">To umožní klientské aplikaci Automatizace <xref:System.Windows.Automation.ScrollPattern> uživatelského rozhraní používat metody vzor ovládacího prvku v kontejneru k zobrazení podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="198cc-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="198cc-115">Povinné členy pro iScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="198cc-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="198cc-116">Pro implementaci rozhraní IScrollProvider je vyžadována následující metoda.</span><span class="sxs-lookup"><span data-stu-id="198cc-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="198cc-117">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="198cc-117">Required members</span></span>|<span data-ttu-id="198cc-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="198cc-118">Member type</span></span>|<span data-ttu-id="198cc-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="198cc-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="198cc-120">- Metoda</span><span class="sxs-lookup"><span data-stu-id="198cc-120">-   Method</span></span>|<span data-ttu-id="198cc-121">Žádný</span><span class="sxs-lookup"><span data-stu-id="198cc-121">None</span></span>|  
  
 <span data-ttu-id="198cc-122">Tento vzor ovládacího prvku nemá žádné přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="198cc-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="198cc-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="198cc-123">Exceptions</span></span>  
 <span data-ttu-id="198cc-124">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="198cc-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="198cc-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="198cc-125">Exception Type</span></span>|<span data-ttu-id="198cc-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="198cc-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="198cc-127">Pokud položku nelze posouvat do zobrazení:</span><span class="sxs-lookup"><span data-stu-id="198cc-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="198cc-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="198cc-128">See also</span></span>

- [<span data-ttu-id="198cc-129">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="198cc-129">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="198cc-130">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="198cc-130">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="198cc-131">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="198cc-131">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="198cc-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="198cc-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="198cc-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="198cc-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
