---
title: "Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: df871c7f7214a6135db2493972dd76f41ce31aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="b3d17-102">Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3d17-102">Implementing the UI Automation Transform Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="b3d17-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b3d17-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b3d17-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b3d17-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b3d17-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITransformProvider>, včetně informací o události, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="b3d17-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b3d17-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="b3d17-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b3d17-107"><xref:System.Windows.Automation.TransformPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které můžete přesunout, po změně velikosti nebo otáčet v dvojrozměrném prostoru.</span><span class="sxs-lookup"><span data-stu-id="b3d17-107">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="b3d17-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b3d17-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b3d17-109">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="b3d17-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b3d17-110">Když implementace vzoru ovládacích prvků transformace, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="b3d17-110">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="b3d17-111">Podpora pro tento vzor ovládacích prvků není omezeno pouze na objekty na ploše.</span><span class="sxs-lookup"><span data-stu-id="b3d17-111">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="b3d17-112">Tento vzor ovládacích prvků musí také podporovat podřízené objekty daného objektu kontejneru Pokud podřízených objektů můžete přesunout, po změně velikosti nebo otáčet volně uvnitř kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b3d17-112">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
-   <span data-ttu-id="b3d17-113">Objekt nelze přesunout, po změně velikosti nebo otáčet tak, aby jeho výsledná umístění obrazovky by být zcela mimo souřadnice svého kontejneru a proto nejsou přístupné na klávesnici nebo myš (například když okno nejvyšší úrovně je přesunut mimo obrazovku a nebo podřízený objekt je přesunut mimo hranice kontejneru zobrazení).</span><span class="sxs-lookup"><span data-stu-id="b3d17-113">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="b3d17-114">V těchto případech je umístěna do objektu co nejblíže souřadnice požadovaný obrazovky nejdříve s horní a levé souřadnice přepsána uvnitř kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b3d17-114">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
-   <span data-ttu-id="b3d17-115">Pro systémy s více monitorování Pokud je přesunout objekt, změněnou nebo otočený zcela mimo souřadnice kombinované plochy obrazovky, objekt je umístěn na primárním monitoru co nejblíže požadovaný souřadnice míře.</span><span class="sxs-lookup"><span data-stu-id="b3d17-115">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
-   <span data-ttu-id="b3d17-116">Všechny parametry a hodnoty vlastností jsou absolutní a nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="b3d17-116">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="b3d17-117">Požadované členy pro ITransformProvider</span><span class="sxs-lookup"><span data-stu-id="b3d17-117">Required Members for ITransformProvider</span></span>  
 <span data-ttu-id="b3d17-118">Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.ITransformProvider>.</span><span class="sxs-lookup"><span data-stu-id="b3d17-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="b3d17-119">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="b3d17-119">Required members</span></span>|<span data-ttu-id="b3d17-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="b3d17-120">Member type</span></span>|<span data-ttu-id="b3d17-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3d17-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="b3d17-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b3d17-122">Property</span></span>|<span data-ttu-id="b3d17-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="b3d17-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b3d17-124">Property</span></span>|<span data-ttu-id="b3d17-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="b3d17-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b3d17-126">Property</span></span>|<span data-ttu-id="b3d17-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="b3d17-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3d17-128">Method</span></span>|<span data-ttu-id="b3d17-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="b3d17-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3d17-130">Method</span></span>|<span data-ttu-id="b3d17-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="b3d17-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3d17-132">Method</span></span>|<span data-ttu-id="b3d17-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3d17-133">None</span></span>|  
  
 <span data-ttu-id="b3d17-134">Tento vzor ovládacích prvků nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="b3d17-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b3d17-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b3d17-135">Exceptions</span></span>  
 <span data-ttu-id="b3d17-136">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="b3d17-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b3d17-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="b3d17-137">Exception Type</span></span>|<span data-ttu-id="b3d17-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="b3d17-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="b3d17-139">-Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> je false.</span><span class="sxs-lookup"><span data-stu-id="b3d17-139">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="b3d17-140">-Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> je false.</span><span class="sxs-lookup"><span data-stu-id="b3d17-140">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="b3d17-141">-Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> je false.</span><span class="sxs-lookup"><span data-stu-id="b3d17-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3d17-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3d17-142">See Also</span></span>  
 [<span data-ttu-id="b3d17-143">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3d17-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="b3d17-144">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3d17-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="b3d17-145">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="b3d17-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="b3d17-146">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3d17-146">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="b3d17-147">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3d17-147">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
