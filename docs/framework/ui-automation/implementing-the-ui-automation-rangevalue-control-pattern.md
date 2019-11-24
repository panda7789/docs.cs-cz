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
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="65898-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="65898-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="65898-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="65898-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="65898-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="65898-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="65898-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span><span class="sxs-lookup"><span data-stu-id="65898-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="65898-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="65898-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="65898-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span><span class="sxs-lookup"><span data-stu-id="65898-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="65898-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="65898-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="65898-109">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="65898-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="65898-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="65898-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="65898-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span><span class="sxs-lookup"><span data-stu-id="65898-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="65898-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span><span class="sxs-lookup"><span data-stu-id="65898-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="65898-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span><span class="sxs-lookup"><span data-stu-id="65898-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="65898-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="65898-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="65898-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span><span class="sxs-lookup"><span data-stu-id="65898-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="65898-116">Required Members for IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="65898-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="65898-117">Required member</span><span class="sxs-lookup"><span data-stu-id="65898-117">Required member</span></span>|<span data-ttu-id="65898-118">Member type</span><span class="sxs-lookup"><span data-stu-id="65898-118">Member type</span></span>|<span data-ttu-id="65898-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65898-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="65898-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-120">Property</span></span>|<span data-ttu-id="65898-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="65898-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-122">Property</span></span>|<span data-ttu-id="65898-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="65898-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-124">Property</span></span>|<span data-ttu-id="65898-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="65898-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-126">Property</span></span>|<span data-ttu-id="65898-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="65898-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-128">Property</span></span>|<span data-ttu-id="65898-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="65898-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="65898-130">Property</span></span>|<span data-ttu-id="65898-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="65898-132">Metody</span><span class="sxs-lookup"><span data-stu-id="65898-132">Methods</span></span>|<span data-ttu-id="65898-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="65898-133">None</span></span>|  
  
 <span data-ttu-id="65898-134">This control pattern has no associated events.</span><span class="sxs-lookup"><span data-stu-id="65898-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="65898-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="65898-135">Exceptions</span></span>  
 <span data-ttu-id="65898-136">Providers must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="65898-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="65898-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="65898-137">Exception type</span></span>|<span data-ttu-id="65898-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="65898-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="65898-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="65898-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65898-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65898-140">See also</span></span>

- [<span data-ttu-id="65898-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="65898-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="65898-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="65898-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="65898-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="65898-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="65898-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="65898-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="65898-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="65898-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
