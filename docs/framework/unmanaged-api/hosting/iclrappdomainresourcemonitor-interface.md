---
title: ICLRAppDomainResourceMonitor – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 597381c8ab31e86a02f870a24f165676d200b66e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965016"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="1eb7a-102">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1eb7a-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="1eb7a-103">Poskytuje metody, které kontrolují paměť a využití procesoru v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eb7a-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1eb7a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1eb7a-104">Methods</span></span>  
  
|<span data-ttu-id="1eb7a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1eb7a-105">Method</span></span>|<span data-ttu-id="1eb7a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1eb7a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1eb7a-107">GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="1eb7a-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="1eb7a-108">Získá celkovou velikost přidělení paměti (v bajtech), která byla vytvořena aplikační doménou od jejího vytvoření, bez odčítání paměti, která byla uvolněna do paměti.</span><span class="sxs-lookup"><span data-stu-id="1eb7a-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="1eb7a-109">GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="1eb7a-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="1eb7a-110">Vrátí počet bajtů, které byly zachovány při posledním plném, blokování uvolnění paměti a odkazují aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eb7a-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="1eb7a-111">GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="1eb7a-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="1eb7a-112">Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eb7a-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eb7a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1eb7a-113">Remarks</span></span>  
 <span data-ttu-id="1eb7a-114">`ICLRAppDomainResourceMonitor` Rozhraní poskytuje funkce, které jsou podobné následujícím spravovaným vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="1eb7a-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="1eb7a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1eb7a-115">Requirements</span></span>  
 <span data-ttu-id="1eb7a-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb7a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb7a-117">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1eb7a-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1eb7a-118">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1eb7a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1eb7a-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb7a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb7a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1eb7a-120">See also</span></span>

- [<span data-ttu-id="1eb7a-121">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="1eb7a-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="1eb7a-122">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1eb7a-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1eb7a-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1eb7a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1eb7a-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="1eb7a-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
