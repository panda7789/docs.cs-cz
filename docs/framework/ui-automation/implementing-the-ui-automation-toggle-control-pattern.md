---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: db468a72f4ee39a5c58e0c5620dc38c0cae14c75
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201079"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="66a65-102">Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="66a65-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="66a65-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="66a65-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="66a65-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="66a65-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider>, včetně informací o metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="66a65-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="66a65-106">Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="66a65-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="66a65-107"><xref:System.Windows.Automation.TogglePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které můžou cyklicky procházet sadu stavy a udržovat stavu po nastavení.</span><span class="sxs-lookup"><span data-stu-id="66a65-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="66a65-108">Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="66a65-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="66a65-109">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="66a65-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="66a65-110">Při implementaci vzoru ovládacích prvků přepínání, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="66a65-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="66a65-111">Ovládací prvky, které nemají stav při aktivaci, jako jsou tlačítka a tlačítka na panelu nástrojů, hypertextové odkazy, musí implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider> místo.</span><span class="sxs-lookup"><span data-stu-id="66a65-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="66a65-112">Ovládací prvek musí cyklicky procházet jeho <xref:System.Windows.Automation.ToggleState> v následujícím pořadí: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> a pokud se podporuje, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="66a65-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="66a65-113"><xref:System.Windows.Automation.TogglePattern> neposkytuje metodu SetState(newState) kvůli problémy kolem přímé nastavení tri stav zaškrtávacího políčka bez procházením jeho odpovídající <xref:System.Windows.Automation.ToggleState> pořadí.</span><span class="sxs-lookup"><span data-stu-id="66a65-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="66a65-114">Ovládací prvek RadioButton neimplementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, protože není schopné procházením jeho platných stavů.</span><span class="sxs-lookup"><span data-stu-id="66a65-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="66a65-115">Požadované členy pro IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="66a65-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="66a65-116">Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="66a65-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="66a65-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="66a65-117">Required member</span></span>|<span data-ttu-id="66a65-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="66a65-118">Member type</span></span>|<span data-ttu-id="66a65-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66a65-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="66a65-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="66a65-120">Method</span></span>|<span data-ttu-id="66a65-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="66a65-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="66a65-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="66a65-122">Property</span></span>|<span data-ttu-id="66a65-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="66a65-123">None</span></span>|  
  
 <span data-ttu-id="66a65-124">Tento model ovládací prvek nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="66a65-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="66a65-125">Výjimky</span><span class="sxs-lookup"><span data-stu-id="66a65-125">Exceptions</span></span>  
 <span data-ttu-id="66a65-126">Tento model ovládací prvek nemá žádné související výjimky.</span><span class="sxs-lookup"><span data-stu-id="66a65-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a65-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="66a65-127">See Also</span></span>  
 [<span data-ttu-id="66a65-128">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="66a65-129">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="66a65-130">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="66a65-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="66a65-131">Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="66a65-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="66a65-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66a65-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
