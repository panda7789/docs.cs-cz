---
title: 'Omezení rizik: Vykreslování oken ve WPF'
description: Přečtěte si o dopadu a zmírnění vykreslování oken WPF v .NET Framework 4,6, které běží v systému Windows 8 nebo novějším.
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475330"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="77d7a-103">Omezení rizik: Vykreslování oken ve WPF</span><span class="sxs-lookup"><span data-stu-id="77d7a-103">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="77d7a-104">V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.</span><span class="sxs-lookup"><span data-stu-id="77d7a-104">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="77d7a-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="77d7a-105">Impact</span></span>

<span data-ttu-id="77d7a-106">Obecně platí, že vykreslování celého okna napříč několika monitory bez oříznutí je očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="77d7a-106">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="77d7a-107">V systému Windows 7 a starších verzích se však okna WPF zobrazují, když přesahují rámec jednoho zobrazení, protože vykreslování části okna na druhém monitoru má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="77d7a-107">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="77d7a-108">Přesný dopad vykreslování oken WPF napříč monitory ve Windows 8 a novějším není přesně kvantifikovaný, protože závisí na velkém počtu faktorů.</span><span class="sxs-lookup"><span data-stu-id="77d7a-108">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="77d7a-109">V některých případech může stále dodávat nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají monitory s podporou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="77d7a-109">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="77d7a-110">V jiných případech může být jednoduché chování v různých .NET Framework verzích.</span><span class="sxs-lookup"><span data-stu-id="77d7a-110">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="77d7a-111">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="77d7a-111">Mitigation</span></span>

<span data-ttu-id="77d7a-112">Tuto změnu můžete zakázat a vrátit se k předchozímu chování při vystřihování okna WPF, když se rozšíří nad rámec jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="77d7a-112">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="77d7a-113">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="77d7a-113">There are two ways to do this:</span></span>

- <span data-ttu-id="77d7a-114">Přidáním `<EnableMultiMonitorDisplayClipping>` elementu do `<appSettings>` oddílu konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit pro aplikace spuštěné v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="77d7a-114">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="77d7a-115">Například následující konfigurační oddíl zakáže vykreslování bez omezení:</span><span class="sxs-lookup"><span data-stu-id="77d7a-115">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="77d7a-116">`<EnableMultiMonitorDisplayClipping>`Nastavení konfigurace může mít jednu ze dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="77d7a-116">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="77d7a-117">`true`, aby při vykreslování bylo umožněno oříznutí oken sledovat hranice.</span><span class="sxs-lookup"><span data-stu-id="77d7a-117">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="77d7a-118">`false`, chcete-li zakázat oříznutí oken ke sledování hranic během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="77d7a-118">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="77d7a-119">Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnosti na `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="77d7a-119">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="77d7a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="77d7a-120">See also</span></span>

- [<span data-ttu-id="77d7a-121">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="77d7a-121">Application compatibility</span></span>](application-compatibility.md)
