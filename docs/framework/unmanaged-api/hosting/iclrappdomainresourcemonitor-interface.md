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
ms.openlocfilehash: 15bdbc001838e3d13a9789c8f54daa80f3b6ef9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219821"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="9407f-102">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9407f-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="9407f-103">Poskytuje metody, které se kontrolovat využití procesoru a paměti doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9407f-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9407f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9407f-104">Methods</span></span>  
  
|<span data-ttu-id="9407f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9407f-105">Method</span></span>|<span data-ttu-id="9407f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9407f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9407f-107">GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="9407f-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="9407f-108">Získá celková velikost v bajtech, všechna přidělení paměti, které byly provedeny podle domény aplikace protože byl vytvořen bez odečtením paměti, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="9407f-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="9407f-109">GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="9407f-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="9407f-110">Získá počet bajtů, které zůstat naživu při poslední úplné blokující uvolňování paměti a, který je odkazováno dle aktuální domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9407f-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="9407f-111">GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="9407f-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="9407f-112">Získá celkový procesorový čas, který byl použit pro všemi vlákny při provádění v aktuální doméně aplikace, od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9407f-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9407f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9407f-113">Remarks</span></span>  
 <span data-ttu-id="9407f-114">`ICLRAppDomainResourceMonitor` Rozhraní poskytuje funkce, které se podobá následující spravované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9407f-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="9407f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9407f-115">Requirements</span></span>  
 <span data-ttu-id="9407f-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9407f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9407f-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9407f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9407f-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9407f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9407f-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9407f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9407f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9407f-120">See also</span></span>

- [<span data-ttu-id="9407f-121">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="9407f-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="9407f-122">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9407f-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="9407f-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9407f-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9407f-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="9407f-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
