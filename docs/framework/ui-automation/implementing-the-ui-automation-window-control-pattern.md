---
title: "Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e8d83c3ef40ccc6e97ba3128cab5d88a5af5305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="17a45-102">Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17a45-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="17a45-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="17a45-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="17a45-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="17a45-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="17a45-105">Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>, včetně informací o <xref:System.Windows.Automation.WindowPattern> vlastnosti, metod a události.</span><span class="sxs-lookup"><span data-stu-id="17a45-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="17a45-106">Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.</span><span class="sxs-lookup"><span data-stu-id="17a45-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="17a45-107"><xref:System.Windows.Automation.WindowPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které poskytují základní funkce se systémem Windows v rámci tradiční [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17a45-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="17a45-108">Příklady ovládacích prvků, které musí implementovat toto – vzor ovládacích prvků windows nejvyšší úrovně aplikace [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] podřízená okna, ovládací prvky umožňující změnu velikosti rozdělení podokně, modálních dialogových oken a bublinách pomohou systému windows.</span><span class="sxs-lookup"><span data-stu-id="17a45-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="17a45-109">Postup implementace a konvence</span><span class="sxs-lookup"><span data-stu-id="17a45-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="17a45-110">Když implementace vzoru ovládacích prvků okno, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="17a45-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="17a45-111">Pro podporu možnost Upravit velikost obě okna a obrazovky pozice pomocí automatizace uživatelského rozhraní, musí implementovat ovládacího prvku <xref:System.Windows.Automation.Provider.ITransformProvider> kromě <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="17a45-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="17a45-112">Ovládací prvky, které obsahují záhlaví a název panelu elementy, které povolte ovládacího prvku se přesune, po změně velikosti, Maximalizovaný, rychle minimalizovat nebo uzavřen se obvykle vyžadují k implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="17a45-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="17a45-113">Ovládací prvky, jako je například automaticky otevíraná okna popisek a pole se seznamem pole nebo nabídky rozevírací seznamy neimplementují obvykle <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="17a45-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="17a45-114">Bublině nápovědy systému windows jsou rozlišené ze základní popis automaticky otevíraná okna pomocí poskytování tlačítko Zavřít okno podobné.</span><span class="sxs-lookup"><span data-stu-id="17a45-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="17a45-115">Režim celé obrazovky není podporována IWindowProvider je specifické pro funkce k aplikaci a není chování typické okno.</span><span class="sxs-lookup"><span data-stu-id="17a45-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="17a45-116">Požadované členy pro IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="17a45-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="17a45-117">Následující vlastnosti, metod a události jsou požadovány pro rozhraní IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="17a45-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="17a45-118">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="17a45-118">Required member</span></span>|<span data-ttu-id="17a45-119">Typ člena</span><span class="sxs-lookup"><span data-stu-id="17a45-119">Member type</span></span>|<span data-ttu-id="17a45-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17a45-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="17a45-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-121">Property</span></span>|<span data-ttu-id="17a45-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="17a45-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-123">Property</span></span>|<span data-ttu-id="17a45-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="17a45-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-125">Property</span></span>|<span data-ttu-id="17a45-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="17a45-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-127">Property</span></span>|<span data-ttu-id="17a45-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="17a45-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-129">Property</span></span>|<span data-ttu-id="17a45-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="17a45-131">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="17a45-131">Property</span></span>|<span data-ttu-id="17a45-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="17a45-133">Metoda</span><span class="sxs-lookup"><span data-stu-id="17a45-133">Method</span></span>|<span data-ttu-id="17a45-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="17a45-135">Metoda</span><span class="sxs-lookup"><span data-stu-id="17a45-135">Method</span></span>|<span data-ttu-id="17a45-136">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="17a45-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="17a45-137">Method</span></span>|<span data-ttu-id="17a45-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="17a45-139">Událost</span><span class="sxs-lookup"><span data-stu-id="17a45-139">Event</span></span>|<span data-ttu-id="17a45-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="17a45-141">Událost</span><span class="sxs-lookup"><span data-stu-id="17a45-141">Event</span></span>|<span data-ttu-id="17a45-142">Žádné</span><span class="sxs-lookup"><span data-stu-id="17a45-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="17a45-143">Událost</span><span class="sxs-lookup"><span data-stu-id="17a45-143">Event</span></span>|<span data-ttu-id="17a45-144">Není zaručena bezpečnost pro přístup<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="17a45-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="17a45-145">Výjimky</span><span class="sxs-lookup"><span data-stu-id="17a45-145">Exceptions</span></span>  
 <span data-ttu-id="17a45-146">Zprostředkovatelé musí throw následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="17a45-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="17a45-147">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="17a45-147">Exception type</span></span>|<span data-ttu-id="17a45-148">Podmínka</span><span class="sxs-lookup"><span data-stu-id="17a45-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="17a45-149">– Když ovládacího prvku nepodporuje požadované chování.</span><span class="sxs-lookup"><span data-stu-id="17a45-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="17a45-150">– Když parametru není platné číslo.</span><span class="sxs-lookup"><span data-stu-id="17a45-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17a45-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="17a45-151">See Also</span></span>  
 [<span data-ttu-id="17a45-152">Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17a45-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="17a45-153">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17a45-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="17a45-154">Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="17a45-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="17a45-155">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17a45-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="17a45-156">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17a45-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
