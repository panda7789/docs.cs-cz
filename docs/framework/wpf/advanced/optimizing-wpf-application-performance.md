---
title: "Optimalizace výkonu aplikace WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9ea154bc7c7a20bcdd57e1f271a4010f50646de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="f79d2-102">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="f79d2-103">Tato část je určena jako odkaz pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace vývojáři, kteří hledají způsoby, jak zlepšit výkon svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="f79d2-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="f79d2-104">Pokud jste vývojář, který je novým [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], budete nejprve si měli přečíst obě platformy.</span><span class="sxs-lookup"><span data-stu-id="f79d2-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="f79d2-105">V této části předpokládá praktické znalosti obou a je napsán pro programátory, kteří již znáte k získání jejich aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="f79d2-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f79d2-106">Data výkonu poskytnutá v této části jsou založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací běžících na 2,8 GHz PC s 512 paměti RAM a ATI Radeon 9700 grafické karty.</span><span class="sxs-lookup"><span data-stu-id="f79d2-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f79d2-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f79d2-107">In This Section</span></span>  
 [<span data-ttu-id="f79d2-108">Plánování výkonu aplikace</span><span class="sxs-lookup"><span data-stu-id="f79d2-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="f79d2-109">Využití výhod hardwaru</span><span class="sxs-lookup"><span data-stu-id="f79d2-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="f79d2-110">Rozložení a návrh</span><span class="sxs-lookup"><span data-stu-id="f79d2-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="f79d2-111">2D grafika a vytvoření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="f79d2-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="f79d2-112">Chování objektů</span><span class="sxs-lookup"><span data-stu-id="f79d2-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="f79d2-113">Prostředky aplikace</span><span class="sxs-lookup"><span data-stu-id="f79d2-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="f79d2-114">Text</span><span class="sxs-lookup"><span data-stu-id="f79d2-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="f79d2-115">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="f79d2-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="f79d2-116">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f79d2-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="f79d2-117">Další doporučení výkonu</span><span class="sxs-lookup"><span data-stu-id="f79d2-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="f79d2-118">Doba spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="f79d2-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="f79d2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f79d2-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="f79d2-120">Grafika vykreslování vrstev</span><span class="sxs-lookup"><span data-stu-id="f79d2-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="f79d2-121">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="f79d2-122">Rozložení</span><span class="sxs-lookup"><span data-stu-id="f79d2-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="f79d2-123">Stromy v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="f79d2-124">Kreslení objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="f79d2-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="f79d2-125">Používání DrawingVisual objektů</span><span class="sxs-lookup"><span data-stu-id="f79d2-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="f79d2-126">Přehled vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="f79d2-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="f79d2-127">Zmrazitelné objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="f79d2-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="f79d2-128">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="f79d2-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="f79d2-129">Dokumenty v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="f79d2-130">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="f79d2-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="f79d2-131">Typografii v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="f79d2-132">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="f79d2-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f79d2-133">Navigace – přehled</span><span class="sxs-lookup"><span data-stu-id="f79d2-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="f79d2-134">Animace tipy a triky</span><span class="sxs-lookup"><span data-stu-id="f79d2-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="f79d2-135">Návod: Ukládání dat aplikací v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="f79d2-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
