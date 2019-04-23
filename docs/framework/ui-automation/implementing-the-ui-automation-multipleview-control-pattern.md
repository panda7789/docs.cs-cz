---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 74e5908dfcd42d031464ffccedb530be4a71a3f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125195"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="5f4f7-102">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f4f7-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5f4f7-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5f4f7-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5f4f7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5f4f7-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="5f4f7-106">Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5f4f7-107"><xref:System.Windows.Automation.MultipleViewPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které poskytují a je možné přepínat mezi více reprezentací stejnou sadu informace nebo podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="5f4f7-108">Příklady ovládacích prvků, které mohou představovat několik zobrazení (které můžete zobrazit jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti) zobrazení seznamu [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafy (výsečového, řádek, pruhový, hodnota buňky pomocí vzorce), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumenty (normální, rozložení webové stránky Tisk rozložení, rozložení pro čtení, osnovy), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendáře (roku, měsíce, týdne, dne), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skinů v šablonách.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="5f4f7-109">Podporované zobrazení jsou určeno vývojářem ovládacího prvku a jsou specifické pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5f4f7-110">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="5f4f7-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5f4f7-111">Při implementaci modelu řízení několika zobrazení, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="5f4f7-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="5f4f7-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> musí být provedeny také na kontejner, který spravuje aktuální zobrazení, pokud se liší od ovládací prvek, který poskytuje aktuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="5f4f7-113">Průzkumník Windows například obsahuje ovládací prvek seznamu pro aktuální obsah složky, zatímco zobrazení pro ovládací prvek spravuje se z aplikace Průzkumník Windows.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="5f4f7-114">Ovládací prvek, který je možné seřadit její obsah se nepovažuje za pro podporu více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="5f4f7-115">Kolekce prvků View musí být identické napříč instancemi.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="5f4f7-116">Zobrazit názvy musí být vhodný pro použití v textu na řeč, Brailleových a dalších běžně čitelné aplikací.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="5f4f7-117">Požadované členy pro IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="5f4f7-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="5f4f7-118">Následující vlastnosti a metody jsou požadovány pro implementaci IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="5f4f7-119">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="5f4f7-119">Required members</span></span>|<span data-ttu-id="5f4f7-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="5f4f7-120">Member type</span></span>|<span data-ttu-id="5f4f7-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f4f7-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="5f4f7-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5f4f7-122">Property</span></span>|<span data-ttu-id="5f4f7-123">Žádný</span><span class="sxs-lookup"><span data-stu-id="5f4f7-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="5f4f7-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f4f7-124">Method</span></span>|<span data-ttu-id="5f4f7-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="5f4f7-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="5f4f7-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f4f7-126">Method</span></span>|<span data-ttu-id="5f4f7-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f4f7-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="5f4f7-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f4f7-128">Method</span></span>|<span data-ttu-id="5f4f7-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f4f7-129">None</span></span>|  
  
 <span data-ttu-id="5f4f7-130">Nejsou žádné akce přidružené k této – vzor ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5f4f7-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5f4f7-131">Exceptions</span></span>  
 <span data-ttu-id="5f4f7-132">Poskytovatel musí vyvolání následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5f4f7-133">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5f4f7-133">Exception type</span></span>|<span data-ttu-id="5f4f7-134">Podmínka</span><span class="sxs-lookup"><span data-stu-id="5f4f7-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="5f4f7-135">Když buď <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> nebo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> je volána s parametrem, který není členem kolekce podporované zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f4f7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f4f7-136">See also</span></span>

- [<span data-ttu-id="5f4f7-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f4f7-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5f4f7-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f4f7-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5f4f7-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="5f4f7-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5f4f7-140">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f4f7-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="5f4f7-141">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f4f7-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
