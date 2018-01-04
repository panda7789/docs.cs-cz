---
title: "Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a53f5f802d451d7575188d4687b6d88f96ec64fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="fdeae-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdeae-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="fdeae-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdeae-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fdeae-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fdeae-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fdeae-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fdeae-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="fdeae-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="fdeae-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="fdeae-107"><xref:System.Windows.Automation.RangeValuePattern> – Vzor ovládacích prvků se používá pro podporu ovládací prvky, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fdeae-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="fdeae-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fdeae-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fdeae-109">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="fdeae-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="fdeae-110">Při implementaci hodnotu rozsahu – vzor ovládacích prvků, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="fdeae-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="fdeae-111">Ovládací prvky umožňují překalibrování jejich podporovaných vlastností na základě předvoleb národního prostředí nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="fdeae-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="fdeae-112">Příkladem je teploměru ovládací prvek, který lze nastavit pro zobrazení teploty v Fahrenheita nebo c.</span><span class="sxs-lookup"><span data-stu-id="fdeae-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="fdeae-113">Ovládací prvky, které mají nejednoznačný rozsah hodnot, například indikátory průběhu nebo posuvníky, by měl mít tyto hodnoty normalized.</span><span class="sxs-lookup"><span data-stu-id="fdeae-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="fdeae-114">![Indikátor průběhu. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="fdeae-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="fdeae-115">Příklad indikátor průběhu, kde hodnota je celé číslo typ a vlastnost minimální a maximální hodnoty jsou normalizovány na 0 a 100,</span><span class="sxs-lookup"><span data-stu-id="fdeae-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="fdeae-116">Požadované členy pro IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="fdeae-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="fdeae-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="fdeae-117">Required member</span></span>|<span data-ttu-id="fdeae-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="fdeae-118">Member type</span></span>|<span data-ttu-id="fdeae-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdeae-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="fdeae-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-120">Property</span></span>|<span data-ttu-id="fdeae-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="fdeae-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-122">Property</span></span>|<span data-ttu-id="fdeae-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="fdeae-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-124">Property</span></span>|<span data-ttu-id="fdeae-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="fdeae-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-126">Property</span></span>|<span data-ttu-id="fdeae-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="fdeae-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-128">Property</span></span>|<span data-ttu-id="fdeae-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="fdeae-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fdeae-130">Property</span></span>|<span data-ttu-id="fdeae-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="fdeae-132">Metody</span><span class="sxs-lookup"><span data-stu-id="fdeae-132">Methods</span></span>|<span data-ttu-id="fdeae-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdeae-133">None</span></span>|  
  
 <span data-ttu-id="fdeae-134">Tento vzor ovládacích prvků nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="fdeae-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fdeae-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="fdeae-135">Exceptions</span></span>  
 <span data-ttu-id="fdeae-136">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="fdeae-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="fdeae-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="fdeae-137">Exception type</span></span>|<span data-ttu-id="fdeae-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="fdeae-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="fdeae-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotu, která je větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="fdeae-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdeae-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdeae-140">See Also</span></span>  
 [<span data-ttu-id="fdeae-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdeae-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="fdeae-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdeae-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="fdeae-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="fdeae-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="fdeae-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdeae-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="fdeae-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdeae-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
