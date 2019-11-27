---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435101"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="b535f-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b535f-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="b535f-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="b535f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b535f-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b535f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b535f-105">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>, včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="b535f-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="b535f-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="b535f-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b535f-107">Vzor ovládacího prvku <xref:System.Windows.Automation.RangeValuePattern> slouží k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b535f-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="b535f-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b535f-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b535f-109">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="b535f-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b535f-110">Při implementaci vzoru ovládacího prvku hodnota rozsahu si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="b535f-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b535f-111">Ovládací prvky umožňují rekalibraci podporovaných vlastností v závislosti na národním prostředí nebo uživatelské preference.</span><span class="sxs-lookup"><span data-stu-id="b535f-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="b535f-112">Příkladem je ovládací prvek teploměr, který lze nastavit tak, aby zobrazoval teplotu ve stupních Fahrenheita nebo Celsia.</span><span class="sxs-lookup"><span data-stu-id="b535f-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="b535f-113">Ovládací prvky, které mají dvojznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.</span><span class="sxs-lookup"><span data-stu-id="b535f-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="b535f-114">![Indikátor průběhu](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="b535f-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="b535f-115">Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b535f-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="b535f-116">Vyžadovaná členové pro IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="b535f-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="b535f-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="b535f-117">Required member</span></span>|<span data-ttu-id="b535f-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="b535f-118">Member type</span></span>|<span data-ttu-id="b535f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b535f-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="b535f-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-120">Property</span></span>|<span data-ttu-id="b535f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="b535f-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-122">Property</span></span>|<span data-ttu-id="b535f-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="b535f-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-124">Property</span></span>|<span data-ttu-id="b535f-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="b535f-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-126">Property</span></span>|<span data-ttu-id="b535f-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="b535f-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-128">Property</span></span>|<span data-ttu-id="b535f-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="b535f-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b535f-130">Property</span></span>|<span data-ttu-id="b535f-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="b535f-132">Metody</span><span class="sxs-lookup"><span data-stu-id="b535f-132">Methods</span></span>|<span data-ttu-id="b535f-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="b535f-133">None</span></span>|  
  
 <span data-ttu-id="b535f-134">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="b535f-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b535f-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b535f-135">Exceptions</span></span>  
 <span data-ttu-id="b535f-136">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="b535f-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b535f-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="b535f-137">Exception type</span></span>|<span data-ttu-id="b535f-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="b535f-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="b535f-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> je volána s hodnotou, která je buď větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="b535f-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b535f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b535f-140">See also</span></span>

- [<span data-ttu-id="b535f-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b535f-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b535f-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b535f-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b535f-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="b535f-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b535f-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b535f-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b535f-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b535f-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
