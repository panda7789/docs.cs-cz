---
title: 'Omezení rizik: Vykreslování oken ve WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e1829716e0a9d5fc63692ca84c8bfefe4cefef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663463"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="cf63e-102">Omezení rizik: Vykreslování oken ve WPF</span><span class="sxs-lookup"><span data-stu-id="cf63e-102">Mitigation: WPF Window Rendering</span></span>
<span data-ttu-id="cf63e-103">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] běžící na Windows 8 a novějším, celé okno je vykreslen bez oříznutí, pokud přesahuje hranice jedné zobrazovaný v případě více monitorů.</span><span class="sxs-lookup"><span data-stu-id="cf63e-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="cf63e-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="cf63e-104">Impact</span></span>  
 <span data-ttu-id="cf63e-105">Obecně platí vykreslování celé okno bez oříznutí víc monitorů je očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="cf63e-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="cf63e-106">Ve Windows 7 a starších verzích se ale WPF windows oříznut, pokud rozšířit nad rámec jednoho zobrazení protože vykreslování část okna na druhém monitoru mají dopad výkonu.</span><span class="sxs-lookup"><span data-stu-id="cf63e-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>  
  
 <span data-ttu-id="cf63e-107">Přesné dopadu vykreslování WPF windows na monitorech v systému Windows 8 a vyšším není přesně vyčíslitelný, protože závisí na velký počet faktorů.</span><span class="sxs-lookup"><span data-stu-id="cf63e-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="cf63e-108">V některých případech ji stále může způsobit nežádoucí vliv na výkon, hlavně pro uživatele, kteří spouštět aplikace náročné na grafiku a mít tažných monitorování systému windows.</span><span class="sxs-lookup"><span data-stu-id="cf63e-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="cf63e-109">V ostatních případech můžete jednoduše chtít konzistentní chování ve verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf63e-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="cf63e-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="cf63e-110">Mitigation</span></span>  
 <span data-ttu-id="cf63e-111">Můžete zakázat tuto změnu a vrátit k předchozí chování při přesahoval jednotné zobrazení oříznutí okno WPF.</span><span class="sxs-lookup"><span data-stu-id="cf63e-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="cf63e-112">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="cf63e-112">There are two ways to do this:</span></span>  
  
-   <span data-ttu-id="cf63e-113">Přidáním `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` oddílu konfiguračního souboru aplikace, můžete zakázat nebo povolit toto chování na aplikace, které běží v systému Windows 8 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="cf63e-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="cf63e-114">Například následující konfigurační oddíl zakáže vykreslování bez omezení:</span><span class="sxs-lookup"><span data-stu-id="cf63e-114">For example, the following configuration section disables rendering without clipping:</span></span>  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     <span data-ttu-id="cf63e-115">`<EnableMultiMonitorDisplayClipping>` Nastavení konfigurace může mít jednu ze dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="cf63e-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>  
  
    -   <span data-ttu-id="cf63e-116">`true`, chcete povolit oříznutí systému windows ke sledování hranice během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="cf63e-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>  
  
    -   <span data-ttu-id="cf63e-117">`false`, chcete-li zakázat systému windows ke sledování hranice během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="cf63e-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>  
  
-   <span data-ttu-id="cf63e-118">Tím, že nastavíte <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnost `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf63e-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf63e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf63e-119">See also</span></span>
- [<span data-ttu-id="cf63e-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="cf63e-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
