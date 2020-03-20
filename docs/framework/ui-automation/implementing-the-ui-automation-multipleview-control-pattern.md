---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180160"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="5bb56-102">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bb56-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="5bb56-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="5bb56-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5bb56-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5bb56-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5bb56-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IMultipleViewProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="5bb56-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="5bb56-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="5bb56-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5bb56-107">Vzor <xref:System.Windows.Automation.MultipleViewPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které poskytují a jsou schopny přepínat mezi více reprezentace stejné sady informací nebo podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5bb56-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="5bb56-108">Příklady ovládacích prvků, které mohou představovat více zobrazení, zahrnují zobrazení seznamu (které může zobrazovat jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti), grafy aplikace Microsoft Excel (výsečový, spojnicový, pruhový, hodnota buňky se vzorcem), dokumenty aplikace Microsoft Word (normální, rozložení webu, tisk rozložení, rozložení pro čtení, osnovu), kalendáře aplikace Microsoft Outlook (rok, měsíc, týden, den) a vzhledy programu Microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="5bb56-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="5bb56-109">Podporovaná zobrazení jsou určena vývojářem ovládacího prvku a jsou specifická pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5bb56-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5bb56-110">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="5bb56-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5bb56-111">Při implementaci vzor ovládacího prvku více zobrazení, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="5bb56-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5bb56-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>by měla být také implementována na kontejneru, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5bb56-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="5bb56-113">Průzkumník Windows například obsahuje ovládací prvek List pro aktuální obsah složky, zatímco zobrazení ovládacího prvku je spravováno z aplikace Průzkumník windows.</span><span class="sxs-lookup"><span data-stu-id="5bb56-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="5bb56-114">Ovládací prvek, který je schopen seřadit jeho obsah není považován za podporu více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5bb56-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="5bb56-115">Kolekce zobrazení musí být identické napříč instancemi.</span><span class="sxs-lookup"><span data-stu-id="5bb56-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="5bb56-116">Názvy zobrazení musí být vhodné pro použití v aplikacích Převod textu na řeč, Braillově písmu a dalších aplikacích čitelných pro člověka.</span><span class="sxs-lookup"><span data-stu-id="5bb56-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="5bb56-117">Požadované členy pro iMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="5bb56-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="5bb56-118">Následující vlastnosti a metody jsou vyžadovány pro implementaci IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="5bb56-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="5bb56-119">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="5bb56-119">Required members</span></span>|<span data-ttu-id="5bb56-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="5bb56-120">Member type</span></span>|<span data-ttu-id="5bb56-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bb56-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="5bb56-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5bb56-122">Property</span></span>|<span data-ttu-id="5bb56-123">Žádný</span><span class="sxs-lookup"><span data-stu-id="5bb56-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="5bb56-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="5bb56-124">Method</span></span>|<span data-ttu-id="5bb56-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="5bb56-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="5bb56-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="5bb56-126">Method</span></span>|<span data-ttu-id="5bb56-127">Žádný</span><span class="sxs-lookup"><span data-stu-id="5bb56-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="5bb56-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="5bb56-128">Method</span></span>|<span data-ttu-id="5bb56-129">Žádný</span><span class="sxs-lookup"><span data-stu-id="5bb56-129">None</span></span>|  
  
 <span data-ttu-id="5bb56-130">Neexistují žádné události spojené s tímto vzorem ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5bb56-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="5bb56-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5bb56-131">Exceptions</span></span>  
 <span data-ttu-id="5bb56-132">Zprostředkovatel musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="5bb56-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5bb56-133">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5bb56-133">Exception type</span></span>|<span data-ttu-id="5bb56-134">Podmínka</span><span class="sxs-lookup"><span data-stu-id="5bb56-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="5bb56-135">Při <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> volání <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> buď nebo je volána s parametrem, který není členem kolekce podporovaných zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5bb56-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bb56-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bb56-136">See also</span></span>

- [<span data-ttu-id="5bb56-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bb56-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5bb56-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bb56-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5bb56-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="5bb56-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5bb56-140">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bb56-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="5bb56-141">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bb56-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
