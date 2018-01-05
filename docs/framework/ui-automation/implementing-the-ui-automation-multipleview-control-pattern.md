---
title: "Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ff185ddb145d51fe8bc32ac10f3a45b57ec954c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="5c3a1-102">Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c3a1-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5c3a1-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5c3a1-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5c3a1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5c3a1-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="5c3a1-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5c3a1-107"><xref:System.Windows.Automation.MultipleViewPattern> – Vzor ovládacích prvků se používá pro podporu ovládací prvky, které poskytují a jsou moct přepínat mezi více reprezentace stejnou sadu informace nebo podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="5c3a1-108">Příklady ovládacích prvků, které může být více zobrazení zobrazení seznamu (která můžete zobrazit jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafy (kruhový, řádku, řádku, hodnotu buňky vzorec), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentů (normální, rozložení webové stránky Tisk rozložení, rozložení pro čtení, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendáře (rok, měsíc, týden, den), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] vzhledy.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="5c3a1-109">Podporované zobrazení určuje vývojář ovládacího prvku a jsou specifické pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5c3a1-110">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="5c3a1-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5c3a1-111">Při implementaci vzoru více zobrazení ovládacích prvků, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="5c3a1-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="5c3a1-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>by měla být implementována také na kontejner, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="5c3a1-113">Například Průzkumník Windows obsahuje ovládací prvek seznamu pro aktuální obsah složky při zobrazení pro ovládací prvek je spravovat z aplikace v Průzkumníku Windows.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="5c3a1-114">Ovládací prvek, který je možné seřadit její obsah se nepovažuje pro podporu více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="5c3a1-115">Kolekce zobrazení musí být identické napříč instancemi.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="5c3a1-116">Názvy zobrazení musí být vhodné pro použití v převod textu na řeč, Braillovo písmo a dalších aplikacích čitelná pro člověka.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="5c3a1-117">Požadované členy pro IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="5c3a1-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="5c3a1-118">Následující vlastnosti a metody jsou požadovány pro implementaci IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="5c3a1-119">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="5c3a1-119">Required members</span></span>|<span data-ttu-id="5c3a1-120">Typ člena</span><span class="sxs-lookup"><span data-stu-id="5c3a1-120">Member type</span></span>|<span data-ttu-id="5c3a1-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c3a1-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="5c3a1-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5c3a1-122">Property</span></span>|<span data-ttu-id="5c3a1-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c3a1-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="5c3a1-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c3a1-124">Method</span></span>|<span data-ttu-id="5c3a1-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c3a1-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="5c3a1-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c3a1-126">Method</span></span>|<span data-ttu-id="5c3a1-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c3a1-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="5c3a1-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c3a1-128">Method</span></span>|<span data-ttu-id="5c3a1-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c3a1-129">None</span></span>|  
  
 <span data-ttu-id="5c3a1-130">Nejsou k dispozici žádné události přidružené k této – vzor ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5c3a1-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5c3a1-131">Exceptions</span></span>  
 <span data-ttu-id="5c3a1-132">Zprostředkovatel musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5c3a1-133">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5c3a1-133">Exception type</span></span>|<span data-ttu-id="5c3a1-134">Podmínka</span><span class="sxs-lookup"><span data-stu-id="5c3a1-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="5c3a1-135">Když buď <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> nebo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> je volán s parametr, který není členem kolekce podporované zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5c3a1-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c3a1-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c3a1-136">See Also</span></span>  
 [<span data-ttu-id="5c3a1-137">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c3a1-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="5c3a1-138">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c3a1-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="5c3a1-139">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="5c3a1-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="5c3a1-140">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c3a1-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="5c3a1-141">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c3a1-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
