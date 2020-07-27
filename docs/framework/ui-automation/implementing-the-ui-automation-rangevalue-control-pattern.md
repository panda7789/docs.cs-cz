---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku ovládacích RangeValue v automatizaci uživatelského rozhraní. Viz povinné členy pro rozhraní IRangeValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: ccb6aeb5f8451975d7e2e9649bbb82c0c3ae23d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164084"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="38e0c-104">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e0c-104">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="38e0c-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="38e0c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="38e0c-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="38e0c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="38e0c-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider> , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="38e0c-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="38e0c-108">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="38e0c-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="38e0c-109"><xref:System.Windows.Automation.RangeValuePattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="38e0c-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="38e0c-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="38e0c-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="38e0c-111">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="38e0c-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="38e0c-112">Při implementaci vzoru ovládacího prvku hodnota rozsahu si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="38e0c-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="38e0c-113">Ovládací prvky umožňují rekalibraci podporovaných vlastností v závislosti na národním prostředí nebo uživatelské preference.</span><span class="sxs-lookup"><span data-stu-id="38e0c-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="38e0c-114">Příkladem je ovládací prvek teploměr, který lze nastavit tak, aby zobrazoval teplotu ve stupních Fahrenheita nebo Celsia.</span><span class="sxs-lookup"><span data-stu-id="38e0c-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="38e0c-115">Ovládací prvky, které mají dvojznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.</span><span class="sxs-lookup"><span data-stu-id="38e0c-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="38e0c-116">![Indikátor průběhu](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="38e0c-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="38e0c-117">Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="38e0c-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="38e0c-118">Vyžadovaná členové pro IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="38e0c-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="38e0c-119">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="38e0c-119">Required member</span></span>|<span data-ttu-id="38e0c-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="38e0c-120">Member type</span></span>|<span data-ttu-id="38e0c-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38e0c-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="38e0c-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-122">Property</span></span>|<span data-ttu-id="38e0c-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="38e0c-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-124">Property</span></span>|<span data-ttu-id="38e0c-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="38e0c-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-126">Property</span></span>|<span data-ttu-id="38e0c-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="38e0c-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-128">Property</span></span>|<span data-ttu-id="38e0c-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="38e0c-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-130">Property</span></span>|<span data-ttu-id="38e0c-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="38e0c-132">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="38e0c-132">Property</span></span>|<span data-ttu-id="38e0c-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="38e0c-134">Metody</span><span class="sxs-lookup"><span data-stu-id="38e0c-134">Methods</span></span>|<span data-ttu-id="38e0c-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="38e0c-135">None</span></span>|  
  
 <span data-ttu-id="38e0c-136">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="38e0c-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="38e0c-137">Výjimky</span><span class="sxs-lookup"><span data-stu-id="38e0c-137">Exceptions</span></span>  
 <span data-ttu-id="38e0c-138">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="38e0c-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="38e0c-139">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="38e0c-139">Exception type</span></span>|<span data-ttu-id="38e0c-140">Podmínka</span><span class="sxs-lookup"><span data-stu-id="38e0c-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="38e0c-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotou, která je buď větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty> .</span><span class="sxs-lookup"><span data-stu-id="38e0c-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38e0c-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="38e0c-142">See also</span></span>

- [<span data-ttu-id="38e0c-143">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e0c-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="38e0c-144">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e0c-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="38e0c-145">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="38e0c-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="38e0c-146">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e0c-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="38e0c-147">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e0c-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
