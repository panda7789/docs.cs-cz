---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180065"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="cfaa9-102">Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="cfaa9-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cfaa9-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cfaa9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cfaa9-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IToggleProvider>konvence pro implementaci , včetně informací o metodách a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="cfaa9-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="cfaa9-107">Vzor <xref:System.Windows.Automation.TogglePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které lze cykonoběh přes sadu stavů a udržovat stav po nastavení.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="cfaa9-108">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cfaa9-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cfaa9-109">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="cfaa9-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cfaa9-110">Při implementaci přepnout ovládací prvek vzor, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="cfaa9-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="cfaa9-111">Ovládací prvky, které při aktivaci neudržují stav, například tlačítka, tlačítka panelu nástrojů a hypertextové odkazy, musí být implementovány. <xref:System.Windows.Automation.Provider.IInvokeProvider></span><span class="sxs-lookup"><span data-stu-id="cfaa9-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="cfaa9-112">Ovládací prvek musí <xref:System.Windows.Automation.ToggleState> cykinožní <xref:System.Windows.Automation.ToggleState.Off> cyklus v <xref:System.Windows.Automation.ToggleState.Indeterminate>následujícím pořadí: <xref:System.Windows.Automation.ToggleState.On>a, pokud je podporován, .</span><span class="sxs-lookup"><span data-stu-id="cfaa9-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="cfaa9-113"><xref:System.Windows.Automation.TogglePattern>neposkytuje SetState(newState) metoda z důvodu problémů obklopujících přímé nastavení tri-state CheckBox bez cyklické prostřednictvím jeho příslušné <xref:System.Windows.Automation.ToggleState> pořadí.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="cfaa9-114">Ovládací prvek RadioButton <xref:System.Windows.Automation.Provider.IToggleProvider>se neimplementuje , protože není schopen cykinovat přes své platné stavy.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="cfaa9-115">Povinné členy pro IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="cfaa9-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="cfaa9-116">Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IToggleProvider>vyžadovány pro implementaci .</span><span class="sxs-lookup"><span data-stu-id="cfaa9-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="cfaa9-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="cfaa9-117">Required member</span></span>|<span data-ttu-id="cfaa9-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="cfaa9-118">Member type</span></span>|<span data-ttu-id="cfaa9-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfaa9-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="cfaa9-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="cfaa9-120">Method</span></span>|<span data-ttu-id="cfaa9-121">Žádný</span><span class="sxs-lookup"><span data-stu-id="cfaa9-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="cfaa9-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cfaa9-122">Property</span></span>|<span data-ttu-id="cfaa9-123">Žádný</span><span class="sxs-lookup"><span data-stu-id="cfaa9-123">None</span></span>|  
  
 <span data-ttu-id="cfaa9-124">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="cfaa9-125">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cfaa9-125">Exceptions</span></span>  
 <span data-ttu-id="cfaa9-126">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="cfaa9-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaa9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfaa9-127">See also</span></span>

- [<span data-ttu-id="cfaa9-128">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cfaa9-129">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="cfaa9-130">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="cfaa9-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cfaa9-131">Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="cfaa9-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="cfaa9-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaa9-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
