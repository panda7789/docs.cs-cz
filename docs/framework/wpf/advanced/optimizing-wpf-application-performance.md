---
title: Optimalizace výkonu aplikace
description: Pomocí těchto zdrojů můžete zlepšit výkon aplikací Windows Presentation Foundation, jako je plánování výkonu a využití hardwaru.
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166324"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="9edfd-103">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="9edfd-104">Tato část je určena jako reference pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojáře aplikací, kteří hledají způsoby, jak vylepšit výkon svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="9edfd-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="9edfd-105">Pokud jste vývojář, který je od Microsoftu .NET Framework a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , měli byste se nejdřív seznámit s oběma platformami.</span><span class="sxs-lookup"><span data-stu-id="9edfd-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="9edfd-106">Tato část předpokládá praktickou znalost obou a je určena pro programátory, kteří již znají dostatek, aby mohli své aplikace začít používat.</span><span class="sxs-lookup"><span data-stu-id="9edfd-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9edfd-107">Údaje o výkonu uvedené v této části jsou založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacích, které běží na počítači 2,8 GHz s 512 paměti RAM a na grafické kartě ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="9edfd-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9edfd-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9edfd-108">In This Section</span></span>  
 [<span data-ttu-id="9edfd-109">Plánování výkonu aplikace</span><span class="sxs-lookup"><span data-stu-id="9edfd-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="9edfd-110">Využití výhod hardwaru</span><span class="sxs-lookup"><span data-stu-id="9edfd-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="9edfd-111">Rozložení a návrh</span><span class="sxs-lookup"><span data-stu-id="9edfd-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="9edfd-112">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="9edfd-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="9edfd-113">Chování objektu</span><span class="sxs-lookup"><span data-stu-id="9edfd-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="9edfd-114">Prostředky aplikace</span><span class="sxs-lookup"><span data-stu-id="9edfd-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="9edfd-115">Text</span><span class="sxs-lookup"><span data-stu-id="9edfd-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="9edfd-116">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="9edfd-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="9edfd-117">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9edfd-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="9edfd-118">Další doporučení k optimalizaci výkonu</span><span class="sxs-lookup"><span data-stu-id="9edfd-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="9edfd-119">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9edfd-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="9edfd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9edfd-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="9edfd-121">Vrstvy vykreslování grafiky</span><span class="sxs-lookup"><span data-stu-id="9edfd-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="9edfd-122">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="9edfd-123">Rozložení</span><span class="sxs-lookup"><span data-stu-id="9edfd-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="9edfd-124">Stromy v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="9edfd-125">Přehled vykreslovaných objektů</span><span class="sxs-lookup"><span data-stu-id="9edfd-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="9edfd-126">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="9edfd-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="9edfd-127">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="9edfd-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="9edfd-128">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="9edfd-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="9edfd-129">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="9edfd-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="9edfd-130">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="9edfd-131">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="9edfd-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="9edfd-132">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="9edfd-133">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="9edfd-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9edfd-134">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="9edfd-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="9edfd-135">Tipy a triky animace</span><span class="sxs-lookup"><span data-stu-id="9edfd-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="9edfd-136">Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="9edfd-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
