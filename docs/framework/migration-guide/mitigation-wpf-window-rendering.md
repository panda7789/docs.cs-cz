---
title: 'Omezení rizik: Vykreslování oken ve WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457765"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="cce52-102">Omezení rizik: Vykreslování oken ve WPF</span><span class="sxs-lookup"><span data-stu-id="cce52-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="cce52-103">V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšší, celé okno je vykreslen bez oříznutí, když rozšiřuje mimo jeden displej ve scénáři více monitorů.</span><span class="sxs-lookup"><span data-stu-id="cce52-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="cce52-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="cce52-104">Impact</span></span>

<span data-ttu-id="cce52-105">Obecně platí vykreslování celé okno přes více monitorů bez oříznutí je očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="cce52-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="cce52-106">Však v systému Windows 7 a starší verze WPF okna jsou oříznuty, pokud přesahují jeden displej, protože vykreslování část okna na druhém monitoru má významný vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="cce52-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="cce52-107">Přesný dopad vykreslování wpf oken napříč monitory v systému Windows 8 a vyšším není přesně kvantifikovatelný, protože závisí na velkém počtu faktorů.</span><span class="sxs-lookup"><span data-stu-id="cce52-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="cce52-108">V některých případech může stále mít nežádoucí dopad na výkon, zejména pro uživatele, kteří spouštějí aplikace náročné na grafiku a mají windows tažné monitory.</span><span class="sxs-lookup"><span data-stu-id="cce52-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="cce52-109">V ostatních případech můžete jednoduše chtít konzistentní chování napříč verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cce52-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="cce52-110">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="cce52-110">Mitigation</span></span>

<span data-ttu-id="cce52-111">Tuto změnu můžete zakázat a vrátit se k předchozímu chování oříznutí okna WPF, pokud přesahuje jedno zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cce52-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="cce52-112">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="cce52-112">There are two ways to do this:</span></span>

- <span data-ttu-id="cce52-113">Přidáním `<EnableMultiMonitorDisplayClipping>` prvku do `<appSettings>` části konfiguračního souboru aplikace můžete toto chování zakázat nebo povolit v aplikacích spuštěných ve Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="cce52-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="cce52-114">Například následující konfigurační část zakáže vykreslování bez oříznutí:</span><span class="sxs-lookup"><span data-stu-id="cce52-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="cce52-115">Nastavení `<EnableMultiMonitorDisplayClipping>` konfigurace může mít jednu ze dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="cce52-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="cce52-116">`true`, aby oříznutí oken monitorovalo hranice během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="cce52-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="cce52-117">`false`, chcete-li zakázat oříznutí oken pro sledování hranic během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="cce52-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="cce52-118">Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnosti `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cce52-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="cce52-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cce52-119">See also</span></span>

- [<span data-ttu-id="cce52-120">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="cce52-120">Application compatibility</span></span>](application-compatibility.md)
