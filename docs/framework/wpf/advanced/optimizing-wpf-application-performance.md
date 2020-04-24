---
title: Optimalizace výkonu aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 54d69e87ef2a9c5318e394422e3bcfcabcc76210
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646252"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="7d16f-102">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="7d16f-103">Tato část je určena [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jako odkaz pro vývojáře aplikací, kteří hledají způsoby, jak zlepšit výkon svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="7d16f-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="7d16f-104">Pokud jste vývojář, který je v rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Microsoft .NET Framework nováčkem a měli byste se nejprve seznámit s oběma platformami.</span><span class="sxs-lookup"><span data-stu-id="7d16f-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="7d16f-105">Tato část předpokládá pracovní znalosti obou a je napsána pro programátory, kteří již vědí dost, aby své aplikace zprovoznili.</span><span class="sxs-lookup"><span data-stu-id="7d16f-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d16f-106">Údaje o výkonu uvedené v této [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] části jsou založeny na aplikacích běžících na počítači s frekvencí 2,8 GHz s 512 RAM a grafickou kartou ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="7d16f-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d16f-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7d16f-107">In This Section</span></span>  
 [<span data-ttu-id="7d16f-108">Plánování výkonu aplikace</span><span class="sxs-lookup"><span data-stu-id="7d16f-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="7d16f-109">Využití výhod hardwaru</span><span class="sxs-lookup"><span data-stu-id="7d16f-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="7d16f-110">Rozložení a návrh</span><span class="sxs-lookup"><span data-stu-id="7d16f-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="7d16f-111">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="7d16f-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="7d16f-112">Chování objektu</span><span class="sxs-lookup"><span data-stu-id="7d16f-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="7d16f-113">Prostředky aplikace</span><span class="sxs-lookup"><span data-stu-id="7d16f-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="7d16f-114">Text</span><span class="sxs-lookup"><span data-stu-id="7d16f-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="7d16f-115">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="7d16f-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="7d16f-116">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7d16f-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="7d16f-117">Další doporučení k optimalizaci výkonu</span><span class="sxs-lookup"><span data-stu-id="7d16f-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="7d16f-118">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="7d16f-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d16f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d16f-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="7d16f-120">Vrstvy vykreslování grafiky</span><span class="sxs-lookup"><span data-stu-id="7d16f-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="7d16f-121">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="7d16f-122">Rozložení</span><span class="sxs-lookup"><span data-stu-id="7d16f-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="7d16f-123">Stromy v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="7d16f-124">Přehled vykreslovaných objektů</span><span class="sxs-lookup"><span data-stu-id="7d16f-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="7d16f-125">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="7d16f-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="7d16f-126">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="7d16f-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="7d16f-127">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="7d16f-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="7d16f-128">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="7d16f-128">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="7d16f-129">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="7d16f-130">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="7d16f-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="7d16f-131">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="7d16f-132">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="7d16f-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7d16f-133">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="7d16f-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="7d16f-134">Tipy a triky animace</span><span class="sxs-lookup"><span data-stu-id="7d16f-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="7d16f-135">Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="7d16f-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
