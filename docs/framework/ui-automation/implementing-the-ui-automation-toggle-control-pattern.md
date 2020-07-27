---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku přepínání v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní IToggleProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: f9ae850a560101582b5f1a461de19f260ef59798
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168036"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="7458d-104">Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-104">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="7458d-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7458d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7458d-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7458d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7458d-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider> , včetně informací o metodách a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="7458d-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="7458d-108">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="7458d-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="7458d-109"><xref:System.Windows.Automation.TogglePattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které mohou procyklovat sadu stavů a udržovat stav po jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="7458d-109">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="7458d-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7458d-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7458d-111">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="7458d-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7458d-112">Při implementaci vzoru ovládacího prvku přepínací tlačítko si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="7458d-112">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="7458d-113">Ovládací prvky, které neudržují stav při aktivaci, jako jsou tlačítka, tlačítka panelu nástrojů a hypertextové odkazy, musí implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider> místo toho.</span><span class="sxs-lookup"><span data-stu-id="7458d-113">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="7458d-114">Ovládací prvek musí procyklovat <xref:System.Windows.Automation.ToggleState> v následujícím pořadí: <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> a, je-li to podporováno, <xref:System.Windows.Automation.ToggleState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="7458d-114">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="7458d-115"><xref:System.Windows.Automation.TogglePattern>neposkytuje metodu SetState (newState), protože došlo k problémům s přímým nastavením zaškrtávacího políčka se stavem Tri bez nutnosti absolvovat příslušné <xref:System.Windows.Automation.ToggleState> pořadí.</span><span class="sxs-lookup"><span data-stu-id="7458d-115"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="7458d-116">Ovládací prvek RadioButton neimplementuje <xref:System.Windows.Automation.Provider.IToggleProvider> , protože není schopen cyklicky předávat své platné stavy.</span><span class="sxs-lookup"><span data-stu-id="7458d-116">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="7458d-117">Vyžadovaná členové pro IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="7458d-117">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="7458d-118">Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.IToggleProvider> .</span><span class="sxs-lookup"><span data-stu-id="7458d-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="7458d-119">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="7458d-119">Required member</span></span>|<span data-ttu-id="7458d-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="7458d-120">Member type</span></span>|<span data-ttu-id="7458d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7458d-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="7458d-122">Metoda</span><span class="sxs-lookup"><span data-stu-id="7458d-122">Method</span></span>|<span data-ttu-id="7458d-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="7458d-123">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="7458d-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="7458d-124">Property</span></span>|<span data-ttu-id="7458d-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="7458d-125">None</span></span>|  
  
 <span data-ttu-id="7458d-126">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="7458d-126">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="7458d-127">Výjimky</span><span class="sxs-lookup"><span data-stu-id="7458d-127">Exceptions</span></span>  
 <span data-ttu-id="7458d-128">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="7458d-128">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7458d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7458d-129">See also</span></span>

- [<span data-ttu-id="7458d-130">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-130">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7458d-131">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-131">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="7458d-132">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="7458d-132">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7458d-133">Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-133">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="7458d-134">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="7458d-135">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7458d-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
