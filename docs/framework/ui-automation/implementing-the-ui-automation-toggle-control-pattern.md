---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447072"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="c2839-102">Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="c2839-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c2839-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c2839-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c2839-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c2839-105">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider>, včetně informací o metodách a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="c2839-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="c2839-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="c2839-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c2839-107">Vzor ovládacího prvku <xref:System.Windows.Automation.TogglePattern> slouží k podpoře ovládacích prvků, které mohou procyklovat sadu stavů a udržovat stav po jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="c2839-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="c2839-108">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c2839-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c2839-109">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="c2839-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c2839-110">Při implementaci vzoru ovládacího prvku přepínací tlačítko si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="c2839-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="c2839-111">Ovládací prvky, které neudržují stav při aktivaci, jako jsou tlačítka, tlačítka panelu nástrojů a hypertextové odkazy, musí místo toho implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span><span class="sxs-lookup"><span data-stu-id="c2839-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="c2839-112">Ovládací prvek musí procyklovat svou <xref:System.Windows.Automation.ToggleState> v následujícím pořadí: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> a, pokud jsou podporovány <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="c2839-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="c2839-113"><xref:System.Windows.Automation.TogglePattern> neposkytuje metodu SetState (newState), protože došlo k problémům s přímým nastavením zaškrtávacího políčka se stavem Tri, aniž by došlo k jeho příslušnému <xref:System.Windows.Automation.ToggleState> sekvenci.</span><span class="sxs-lookup"><span data-stu-id="c2839-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="c2839-114">Ovládací prvek RadioButton neimplementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, protože není schopen cyklicky předávat své platné stavy.</span><span class="sxs-lookup"><span data-stu-id="c2839-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="c2839-115">Vyžadovaná členové pro IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="c2839-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="c2839-116">Pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider>jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="c2839-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="c2839-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="c2839-117">Required member</span></span>|<span data-ttu-id="c2839-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="c2839-118">Member type</span></span>|<span data-ttu-id="c2839-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2839-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="c2839-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2839-120">Method</span></span>|<span data-ttu-id="c2839-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2839-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="c2839-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c2839-122">Property</span></span>|<span data-ttu-id="c2839-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2839-123">None</span></span>|  
  
 <span data-ttu-id="c2839-124">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="c2839-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c2839-125">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c2839-125">Exceptions</span></span>  
 <span data-ttu-id="c2839-126">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="c2839-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2839-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2839-127">See also</span></span>

- [<span data-ttu-id="c2839-128">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c2839-129">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c2839-130">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="c2839-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c2839-131">Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="c2839-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="c2839-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2839-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
