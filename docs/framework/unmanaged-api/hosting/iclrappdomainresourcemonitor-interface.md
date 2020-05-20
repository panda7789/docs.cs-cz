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
ms.openlocfilehash: 08dc0f0891d960cb7b402b30455e606aaff7bcea
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616005"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="883d7-102">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="883d7-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="883d7-103">Poskytuje metody, které kontrolují paměť a využití procesoru v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="883d7-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="883d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="883d7-104">Methods</span></span>  
  
|<span data-ttu-id="883d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="883d7-105">Method</span></span>|<span data-ttu-id="883d7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="883d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="883d7-107">GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="883d7-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="883d7-108">Získá celkovou velikost přidělení paměti (v bajtech), která byla vytvořena aplikační doménou od jejího vytvoření, bez odčítání paměti, která byla uvolněna do paměti.</span><span class="sxs-lookup"><span data-stu-id="883d7-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="883d7-109">GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="883d7-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="883d7-110">Vrátí počet bajtů, které byly zachovány při posledním plném, blokování uvolnění paměti a odkazují aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="883d7-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="883d7-111">GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="883d7-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="883d7-112">Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="883d7-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="883d7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="883d7-113">Remarks</span></span>  
 <span data-ttu-id="883d7-114">`ICLRAppDomainResourceMonitor`Rozhraní poskytuje funkce, které jsou podobné následujícím spravovaným vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="883d7-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="883d7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="883d7-115">Requirements</span></span>  
 <span data-ttu-id="883d7-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883d7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883d7-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="883d7-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="883d7-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="883d7-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="883d7-119">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883d7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883d7-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="883d7-120">See also</span></span>

- [<span data-ttu-id="883d7-121">\<appDomainResourceMonitoring – element></span><span class="sxs-lookup"><span data-stu-id="883d7-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="883d7-122">Monitorování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="883d7-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="883d7-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="883d7-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="883d7-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="883d7-124">Hosting</span></span>](index.md)
