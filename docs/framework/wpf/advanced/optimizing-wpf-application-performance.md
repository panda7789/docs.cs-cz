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
ms.workload: dotnet
ms.openlocfilehash: 385bcb8678b11e1cb8f84ae509b1f1b6777665d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="52a4f-102">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="52a4f-103">Tato část je určena jako odkaz pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace vývojáři, kteří hledají způsoby, jak zlepšit výkon svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="52a4f-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="52a4f-104">Pokud jste vývojář, který je novým [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], budete nejprve si měli přečíst obě platformy.</span><span class="sxs-lookup"><span data-stu-id="52a4f-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="52a4f-105">V této části předpokládá praktické znalosti obou a je napsán pro programátory, kteří již znáte k získání jejich aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="52a4f-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52a4f-106">Data výkonu poskytnutá v této části jsou založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací běžících na 2,8 GHz PC s 512 paměti RAM a ATI Radeon 9700 grafické karty.</span><span class="sxs-lookup"><span data-stu-id="52a4f-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52a4f-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52a4f-107">In This Section</span></span>  
 [<span data-ttu-id="52a4f-108">Plánování výkonu aplikace</span><span class="sxs-lookup"><span data-stu-id="52a4f-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="52a4f-109">Využití výhod hardwaru</span><span class="sxs-lookup"><span data-stu-id="52a4f-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="52a4f-110">Rozložení a návrh</span><span class="sxs-lookup"><span data-stu-id="52a4f-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="52a4f-111">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="52a4f-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="52a4f-112">Chování objektu</span><span class="sxs-lookup"><span data-stu-id="52a4f-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="52a4f-113">Prostředky aplikace</span><span class="sxs-lookup"><span data-stu-id="52a4f-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="52a4f-114">Text</span><span class="sxs-lookup"><span data-stu-id="52a4f-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="52a4f-115">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="52a4f-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="52a4f-116">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="52a4f-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="52a4f-117">Další výkonnostní doporučení</span><span class="sxs-lookup"><span data-stu-id="52a4f-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="52a4f-118">Doba spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="52a4f-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="52a4f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="52a4f-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="52a4f-120">Vrstvy vykreslování grafiky</span><span class="sxs-lookup"><span data-stu-id="52a4f-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="52a4f-121">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="52a4f-122">Rozložení</span><span class="sxs-lookup"><span data-stu-id="52a4f-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="52a4f-123">Stromy v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="52a4f-124">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="52a4f-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="52a4f-125">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="52a4f-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="52a4f-126">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="52a4f-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="52a4f-127">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="52a4f-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="52a4f-128">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="52a4f-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="52a4f-129">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="52a4f-130">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="52a4f-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="52a4f-131">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="52a4f-132">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="52a4f-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="52a4f-133">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="52a4f-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="52a4f-134">Tipy a triky animace</span><span class="sxs-lookup"><span data-stu-id="52a4f-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="52a4f-135">Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="52a4f-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
