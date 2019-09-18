---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 57986fa28a7a1bb7f70409b332147ff5b9615ec0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043412"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="3291a-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3291a-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="3291a-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3291a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3291a-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3291a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3291a-105">Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IRangeValueProvider>implementaci, včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="3291a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="3291a-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="3291a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="3291a-107">Vzor <xref:System.Windows.Automation.RangeValuePattern> ovládacího prvku slouží k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="3291a-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="3291a-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3291a-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3291a-109">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="3291a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="3291a-110">Při implementaci vzoru ovládacího prvku hodnota rozsahu si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="3291a-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="3291a-111">Ovládací prvky umožňují rekalibraci podporovaných vlastností v závislosti na národním prostředí nebo uživatelské preference.</span><span class="sxs-lookup"><span data-stu-id="3291a-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="3291a-112">Příkladem je ovládací prvek teploměr, který lze nastavit tak, aby zobrazoval teplotu ve stupních Fahrenheita nebo Celsia.</span><span class="sxs-lookup"><span data-stu-id="3291a-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="3291a-113">Ovládací prvky, které mají dvojznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.</span><span class="sxs-lookup"><span data-stu-id="3291a-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="3291a-114">Indikátor ![průběhu](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="3291a-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="3291a-115">Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3291a-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="3291a-116">Vyžadovaná členové pro IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="3291a-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="3291a-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="3291a-117">Required member</span></span>|<span data-ttu-id="3291a-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="3291a-118">Member type</span></span>|<span data-ttu-id="3291a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3291a-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="3291a-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-120">Property</span></span>|<span data-ttu-id="3291a-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="3291a-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-122">Property</span></span>|<span data-ttu-id="3291a-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="3291a-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-124">Property</span></span>|<span data-ttu-id="3291a-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="3291a-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-126">Property</span></span>|<span data-ttu-id="3291a-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="3291a-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-128">Property</span></span>|<span data-ttu-id="3291a-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="3291a-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3291a-130">Property</span></span>|<span data-ttu-id="3291a-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="3291a-132">Metody</span><span class="sxs-lookup"><span data-stu-id="3291a-132">Methods</span></span>|<span data-ttu-id="3291a-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="3291a-133">None</span></span>|  
  
 <span data-ttu-id="3291a-134">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="3291a-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="3291a-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="3291a-135">Exceptions</span></span>  
 <span data-ttu-id="3291a-136">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="3291a-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="3291a-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="3291a-137">Exception type</span></span>|<span data-ttu-id="3291a-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="3291a-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="3291a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotou, která je buď větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="3291a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3291a-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3291a-140">See also</span></span>

- [<span data-ttu-id="3291a-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3291a-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3291a-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3291a-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3291a-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="3291a-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3291a-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3291a-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="3291a-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3291a-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
