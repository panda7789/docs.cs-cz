---
title: "Omezení rizik: Vykreslování oken ve WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 032d07b75b96809ff71c7735a267a7351ad25dda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="d862c-102">Omezení rizik: Vykreslování oken ve WPF</span><span class="sxs-lookup"><span data-stu-id="d862c-102">Mitigation: WPF Window Rendering</span></span>
<span data-ttu-id="d862c-103">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] systémem Windows 8 a vyšší, celé okno je vykreslen bez výstřižek, pokud ji rozšiřuje mimo jednoho zobrazení ve scénáři s více monitorování.</span><span class="sxs-lookup"><span data-stu-id="d862c-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d862c-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="d862c-104">Impact</span></span>  
 <span data-ttu-id="d862c-105">Obecně platí vykreslování celého okna víc monitorů bez výstřižek je očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="d862c-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="d862c-106">V systému Windows 7 a starší verze, jsou však WPF windows oříznut, pokud rozšířit nad rámec jednoho zobrazení protože vykreslování část okna na druhém monitoru má vliv významně zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="d862c-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>  
  
 <span data-ttu-id="d862c-107">Přesné dopad vykreslování WPF windows na monitory v systému Windows 8 a vyšší není přesně vyčíslitelný, protože závisí na velkého počtu faktorů.</span><span class="sxs-lookup"><span data-stu-id="d862c-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="d862c-108">V některých případech se může stále vytvořit nežádoucí vliv na výkon, hlavně pro uživatele, kteří spustit aplikace náročné na grafiky a windows tažných monitorování.</span><span class="sxs-lookup"><span data-stu-id="d862c-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="d862c-109">V ostatních případech jednoduše můžete konzistentní chování napříč verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d862c-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d862c-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="d862c-110">Mitigation</span></span>  
 <span data-ttu-id="d862c-111">Můžete zakázat tuto změnu a vrátit k předchozí chování výstřižek okno WPF při přesahoval jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d862c-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="d862c-112">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="d862c-112">There are two ways to do this:</span></span>  
  
-   <span data-ttu-id="d862c-113">Přidáním `<EnableMultiMonitorDisplayClipping>` elementu, který chcete `<appSettings>` oddíl v konfiguračním souboru aplikace, můžete zakázat nebo povolit toto chování na aplikace běžící v systému Windows 8 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d862c-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="d862c-114">Například následující konfigurační oddíl zakáže vykreslování bez výstřižek:</span><span class="sxs-lookup"><span data-stu-id="d862c-114">For example, the following configuration section disables rendering without clipping:</span></span>  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     <span data-ttu-id="d862c-115">`<EnableMultiMonitorDisplayClipping>` Nastavení konfigurace může mít buď ze dvou hodnot:</span><span class="sxs-lookup"><span data-stu-id="d862c-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>  
  
    -   <span data-ttu-id="d862c-116">`true`, chcete-li povolit výstřižek systému windows ke sledování hranice během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="d862c-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>  
  
    -   <span data-ttu-id="d862c-117">`false`, chcete-li zakázat výstřižek systému windows ke sledování hranice během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="d862c-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>  
  
-   <span data-ttu-id="d862c-118">Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnost `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d862c-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d862c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d862c-119">See Also</span></span>  
 [<span data-ttu-id="d862c-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d862c-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
