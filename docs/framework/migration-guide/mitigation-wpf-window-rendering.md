---
title: Zmírnění Vykreslování oken WPF
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789789"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="c3d52-102">Zmírnění Vykreslování oken WPF</span><span class="sxs-lookup"><span data-stu-id="c3d52-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="c3d52-103">V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.</span><span class="sxs-lookup"><span data-stu-id="c3d52-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="c3d52-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="c3d52-104">Impact</span></span>

<span data-ttu-id="c3d52-105">Obecně platí, že vykreslování celého okna napříč několika monitory bez oříznutí je očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="c3d52-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="c3d52-106">V systému Windows 7 a starších verzích se však okna WPF zobrazují, když přesahují rámec jednoho zobrazení, protože vykreslování části okna na druhém monitoru má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="c3d52-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="c3d52-107">Přesný dopad vykreslování oken WPF napříč monitory ve Windows 8 a novějším není přesně kvantifikovaný, protože závisí na velkém počtu faktorů.</span><span class="sxs-lookup"><span data-stu-id="c3d52-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="c3d52-108">V některých případech může stále dodávat nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají monitory s podporou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c3d52-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="c3d52-109">V jiných případech může být jednoduché chování v různých .NET Framework verzích.</span><span class="sxs-lookup"><span data-stu-id="c3d52-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="c3d52-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="c3d52-110">Mitigation</span></span>

<span data-ttu-id="c3d52-111">Tuto změnu můžete zakázat a vrátit se k předchozímu chování při vystřihování okna WPF, když se rozšíří nad rámec jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c3d52-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="c3d52-112">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="c3d52-112">There are two ways to do this:</span></span>

- <span data-ttu-id="c3d52-113">Přidáním `<EnableMultiMonitorDisplayClipping>` elementu`<appSettings>` do oddílu konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit pro aplikace spuštěné v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="c3d52-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="c3d52-114">Například následující konfigurační oddíl zakáže vykreslování bez omezení:</span><span class="sxs-lookup"><span data-stu-id="c3d52-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="c3d52-115">Nastavení `<EnableMultiMonitorDisplayClipping>` konfigurace může mít jednu ze dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="c3d52-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="c3d52-116">`true`, aby při vykreslování bylo umožněno oříznutí oken sledovat hranice.</span><span class="sxs-lookup"><span data-stu-id="c3d52-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="c3d52-117">`false`, chcete-li zakázat oříznutí oken ke sledování hranic během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="c3d52-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="c3d52-118">Nastavením vlastnosti na `true` při spuštění aplikace. <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A></span><span class="sxs-lookup"><span data-stu-id="c3d52-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3d52-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3d52-119">See also</span></span>

- [<span data-ttu-id="c3d52-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="c3d52-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
