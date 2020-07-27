---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku ovládacích prvků MultipleView v automatizaci uživatelského rozhraní. Viz povinné členy pro rozhraní IMultipleViewProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 0d65d57637891fcb1307f5ee83a417941ff323fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168221"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="8b485-104">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b485-104">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8b485-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8b485-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8b485-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8b485-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8b485-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IMultipleViewProvider> , včetně informací o událostech a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="8b485-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="8b485-108">Odkazy na další odkazy jsou uvedeny na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="8b485-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8b485-109"><xref:System.Windows.Automation.MultipleViewPattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které poskytují a jsou schopny přepínat mezi různými reprezentacemi stejné sady informací nebo podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="8b485-109">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="8b485-110">Příklady ovládacích prvků, které mohou prezentovat více zobrazení, zahrnují zobrazení seznamu (které může zobrazit jeho obsah jako miniatury). dlaždice, ikony nebo podrobnosti), grafy Microsoft Excelu (výsečové, spojnicové, pruhové, sloupcové hodnoty se vzorcem), Microsoft Word (normální, rozložení pro tisk, rozložení pro čtení, rozložení pro čtení, osnova), Microsoft Outlook – kalendářní data (rok, měsíc, týden, den) a Microsoft Windows Media Player skiny.</span><span class="sxs-lookup"><span data-stu-id="8b485-110">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="8b485-111">Podporovaná zobrazení jsou určena vývojářem ovládacího prvku a jsou specifická pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8b485-111">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8b485-112">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="8b485-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8b485-113">Při implementaci modelu více ovládacích prvků zobrazení si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="8b485-113">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8b485-114"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>měla by být také implementována na kontejneru, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="8b485-114"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="8b485-115">Například Průzkumník Windows obsahuje ovládací prvek seznamu pro aktuální obsah složky, zatímco zobrazení pro ovládací prvek je spravováno z aplikace Průzkumník Windows.</span><span class="sxs-lookup"><span data-stu-id="8b485-115">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="8b485-116">Ovládací prvek, který je schopný seřadit jeho obsah, není považován za podporu více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="8b485-116">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="8b485-117">Kolekce zobrazení musí být identická mezi instancemi.</span><span class="sxs-lookup"><span data-stu-id="8b485-117">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="8b485-118">Názvy zobrazení musí být vhodné pro použití v Převod textu na řeč, Braillova písma a dalších aplikacích čitelných lidmi.</span><span class="sxs-lookup"><span data-stu-id="8b485-118">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="8b485-119">Vyžadovaná členové pro IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="8b485-119">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="8b485-120">Pro implementaci IMultipleViewProvider jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="8b485-120">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="8b485-121">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="8b485-121">Required members</span></span>|<span data-ttu-id="8b485-122">Typ člena</span><span class="sxs-lookup"><span data-stu-id="8b485-122">Member type</span></span>|<span data-ttu-id="8b485-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b485-123">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="8b485-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8b485-124">Property</span></span>|<span data-ttu-id="8b485-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b485-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="8b485-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b485-126">Method</span></span>|<span data-ttu-id="8b485-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b485-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="8b485-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b485-128">Method</span></span>|<span data-ttu-id="8b485-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b485-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="8b485-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b485-130">Method</span></span>|<span data-ttu-id="8b485-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b485-131">None</span></span>|  
  
 <span data-ttu-id="8b485-132">K tomuto vzoru ovládacích prvků nejsou přidruženy žádné události.</span><span class="sxs-lookup"><span data-stu-id="8b485-132">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="8b485-133">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8b485-133">Exceptions</span></span>  
 <span data-ttu-id="8b485-134">Zprostředkovatel musí vyvolat následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="8b485-134">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8b485-135">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="8b485-135">Exception type</span></span>|<span data-ttu-id="8b485-136">Podmínka</span><span class="sxs-lookup"><span data-stu-id="8b485-136">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="8b485-137">Když <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> je nebo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> je volána s parametrem, který není členem podporované kolekce zobrazení.</span><span class="sxs-lookup"><span data-stu-id="8b485-137">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b485-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b485-138">See also</span></span>

- [<span data-ttu-id="8b485-139">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b485-139">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8b485-140">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b485-140">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8b485-141">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="8b485-141">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8b485-142">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b485-142">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8b485-143">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b485-143">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
