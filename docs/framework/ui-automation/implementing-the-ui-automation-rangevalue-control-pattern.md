---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180184"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="2dbd5-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dbd5-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="2dbd5-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2dbd5-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2dbd5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2dbd5-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IRangeValueProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="2dbd5-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="2dbd5-107">Vzor <xref:System.Windows.Automation.RangeValuePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="2dbd5-108">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="2dbd5-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2dbd5-109">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="2dbd5-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="2dbd5-110">Při implementaci vzor ovládacího prvku hodnota rozsahu, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="2dbd5-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2dbd5-111">Ovládací prvky umožňují rekalibraci jejich podporovaných vlastností na základě národního prostředí nebo uživatelské předvolby.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="2dbd5-112">Příkladem je ovládání teploměru, které lze nastavit tak, aby zobrazovalo teplotu ve Stupních Fahrenheita nebo Celsia.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="2dbd5-113">Ovládací prvky, které mají nejednoznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="2dbd5-114">![Indikátor průběhu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="2dbd5-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="2dbd5-115">Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí</span><span class="sxs-lookup"><span data-stu-id="2dbd5-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="2dbd5-116">Povinné členy pro iRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="2dbd5-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="2dbd5-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="2dbd5-117">Required member</span></span>|<span data-ttu-id="2dbd5-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="2dbd5-118">Member type</span></span>|<span data-ttu-id="2dbd5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2dbd5-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="2dbd5-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-120">Property</span></span>|<span data-ttu-id="2dbd5-121">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="2dbd5-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-122">Property</span></span>|<span data-ttu-id="2dbd5-123">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="2dbd5-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-124">Property</span></span>|<span data-ttu-id="2dbd5-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="2dbd5-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-126">Property</span></span>|<span data-ttu-id="2dbd5-127">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="2dbd5-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-128">Property</span></span>|<span data-ttu-id="2dbd5-129">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="2dbd5-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2dbd5-130">Property</span></span>|<span data-ttu-id="2dbd5-131">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="2dbd5-132">Metody</span><span class="sxs-lookup"><span data-stu-id="2dbd5-132">Methods</span></span>|<span data-ttu-id="2dbd5-133">Žádný</span><span class="sxs-lookup"><span data-stu-id="2dbd5-133">None</span></span>|  
  
 <span data-ttu-id="2dbd5-134">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="2dbd5-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2dbd5-135">Exceptions</span></span>  
 <span data-ttu-id="2dbd5-136">Zprostředkovatelé musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="2dbd5-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="2dbd5-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="2dbd5-137">Exception type</span></span>|<span data-ttu-id="2dbd5-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="2dbd5-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="2dbd5-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotou, <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> která <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>je větší nebo menší než .</span><span class="sxs-lookup"><span data-stu-id="2dbd5-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2dbd5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dbd5-140">See also</span></span>

- [<span data-ttu-id="2dbd5-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dbd5-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2dbd5-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dbd5-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2dbd5-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="2dbd5-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2dbd5-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dbd5-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2dbd5-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dbd5-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
