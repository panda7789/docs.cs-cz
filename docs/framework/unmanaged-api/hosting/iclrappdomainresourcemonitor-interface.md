---
title: "ICLRAppDomainResourceMonitor – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor
helpviewer_keywords: ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2cb7fd41e3f5b192974d61ddd9cf2b5845690ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="f3dfd-102">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3dfd-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="f3dfd-103">Poskytuje metody, které zkontrolovat doménu aplikace využití paměti a procesoru.</span><span class="sxs-lookup"><span data-stu-id="f3dfd-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3dfd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f3dfd-104">Methods</span></span>  
  
|<span data-ttu-id="f3dfd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3dfd-105">Method</span></span>|<span data-ttu-id="f3dfd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f3dfd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3dfd-107">Getcurrentallocated – metoda</span><span class="sxs-lookup"><span data-stu-id="f3dfd-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="f3dfd-108">Získá celková velikost v bajtech přidělených paměti, které jste provedli pro doménu aplikace, protože byl vytvořen bez odečtením paměti, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f3dfd-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="f3dfd-109">Getcurrentsurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="f3dfd-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="f3dfd-110">Získá počet bajtů, který zůstal naživu poslední úplné, blokování uvolňování paměti a který se odkazuje aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3dfd-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="f3dfd-111">Getcurrentcputime – metoda</span><span class="sxs-lookup"><span data-stu-id="f3dfd-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="f3dfd-112">Získá celkový procesorového času, který byl použit pro všechna vlákna při provádění v aktuální doméně aplikace, že se od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3dfd-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3dfd-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3dfd-113">Remarks</span></span>  
 <span data-ttu-id="f3dfd-114">`ICLRAppDomainResourceMonitor` Rozhraní poskytuje funkce, které je podobná následující spravované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f3dfd-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="f3dfd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3dfd-115">Requirements</span></span>  
 <span data-ttu-id="f3dfd-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3dfd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3dfd-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f3dfd-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f3dfd-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3dfd-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3dfd-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3dfd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dfd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3dfd-120">See Also</span></span>  
 [<span data-ttu-id="f3dfd-121">\<appdomainresourcemonitoring – > elementu</span><span class="sxs-lookup"><span data-stu-id="f3dfd-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="f3dfd-122">Prostředků domény aplikace monitorování</span><span class="sxs-lookup"><span data-stu-id="f3dfd-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="f3dfd-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="f3dfd-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f3dfd-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="f3dfd-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
