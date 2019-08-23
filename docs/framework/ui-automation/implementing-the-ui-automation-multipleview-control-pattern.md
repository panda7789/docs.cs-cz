---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 6a77b81cab34b1824b23b1e3e050ecf034ab7700
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932160"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="e82d3-102">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e82d3-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="e82d3-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e82d3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e82d3-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e82d3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e82d3-105">Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IMultipleViewProvider>implementaci, včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="e82d3-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="e82d3-106">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="e82d3-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="e82d3-107">Vzor <xref:System.Windows.Automation.MultipleViewPattern> ovládacího prvku slouží k podpoře ovládacích prvků, které poskytují a jsou schopny přepínat mezi různými reprezentacemi stejné sady informací nebo podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e82d3-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="e82d3-108">Příklady ovládacích prvků, které mohou prezentovat více zobrazení, zahrnují zobrazení seznamu (které může zobrazit jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti) [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] , grafy (výsečové, spojnicové, pruhové, sloupcové hodnoty se [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] vzorci), dokumenty (normální, rozložení na webu, rozložení pro tisk, rozložení pro čtení, osnova), kalendář Microsoft Outlook (rok, měsíc, týden, den [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] ) a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="e82d3-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="e82d3-109">Podporovaná zobrazení jsou určena vývojářem ovládacího prvku a jsou specifická pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e82d3-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e82d3-110">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="e82d3-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="e82d3-111">Při implementaci modelu více ovládacích prvků zobrazení si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="e82d3-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e82d3-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>měla by být také implementována na kontejneru, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e82d3-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="e82d3-113">Například Průzkumník Windows obsahuje ovládací prvek seznamu pro aktuální obsah složky, zatímco zobrazení pro ovládací prvek je spravováno z aplikace Průzkumník Windows.</span><span class="sxs-lookup"><span data-stu-id="e82d3-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="e82d3-114">Ovládací prvek, který je schopný seřadit jeho obsah, není považován za podporu více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e82d3-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="e82d3-115">Kolekce zobrazení musí být identická mezi instancemi.</span><span class="sxs-lookup"><span data-stu-id="e82d3-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="e82d3-116">Názvy zobrazení musí být vhodné pro použití v Převod textu na řeč, Braillova písma a dalších aplikacích čitelných lidmi.</span><span class="sxs-lookup"><span data-stu-id="e82d3-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="e82d3-117">Vyžadovaná členové pro IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="e82d3-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="e82d3-118">Pro implementaci IMultipleViewProvider jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="e82d3-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="e82d3-119">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="e82d3-119">Required members</span></span>|<span data-ttu-id="e82d3-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="e82d3-120">Member type</span></span>|<span data-ttu-id="e82d3-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e82d3-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="e82d3-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e82d3-122">Property</span></span>|<span data-ttu-id="e82d3-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="e82d3-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="e82d3-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="e82d3-124">Method</span></span>|<span data-ttu-id="e82d3-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="e82d3-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="e82d3-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="e82d3-126">Method</span></span>|<span data-ttu-id="e82d3-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="e82d3-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="e82d3-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="e82d3-128">Method</span></span>|<span data-ttu-id="e82d3-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="e82d3-129">None</span></span>|  
  
 <span data-ttu-id="e82d3-130">K tomuto vzoru ovládacích prvků nejsou přidruženy žádné události.</span><span class="sxs-lookup"><span data-stu-id="e82d3-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="e82d3-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e82d3-131">Exceptions</span></span>  
 <span data-ttu-id="e82d3-132">Zprostředkovatel musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="e82d3-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e82d3-133">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="e82d3-133">Exception type</span></span>|<span data-ttu-id="e82d3-134">Podmínka</span><span class="sxs-lookup"><span data-stu-id="e82d3-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="e82d3-135">Když je <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> nebo je volána s parametrem, který není členem podporované kolekce zobrazení. <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A></span><span class="sxs-lookup"><span data-stu-id="e82d3-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e82d3-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e82d3-136">See also</span></span>

- [<span data-ttu-id="e82d3-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e82d3-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e82d3-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e82d3-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e82d3-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="e82d3-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e82d3-140">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e82d3-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="e82d3-141">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e82d3-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
