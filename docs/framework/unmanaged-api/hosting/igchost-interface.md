---
title: IGCHost – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a77cd85c0fafd9994418693c8d3c4b148c34dbe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437661"
---
# <a name="igchost-interface"></a><span data-ttu-id="eaea1-102">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaea1-102">IGCHost Interface</span></span>
<span data-ttu-id="eaea1-103">Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eaea1-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaea1-104">Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete použít [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodu a nastavit velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD` omezení, která je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="eaea1-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaea1-105">Toto rozhraní je pouze odborné využití.</span><span class="sxs-lookup"><span data-stu-id="eaea1-105">This interface is for expert usage only.</span></span> <span data-ttu-id="eaea1-106">Pokud použili nesprávně může ovlivnit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaea1-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaea1-107">Metody</span><span class="sxs-lookup"><span data-stu-id="eaea1-107">Methods</span></span>  
  
|<span data-ttu-id="eaea1-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-108">Method</span></span>|<span data-ttu-id="eaea1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="eaea1-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaea1-110">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="eaea1-111">Vynutí kolekci vyskytují pro danou generaci, bez ohledu na stav v aktuální kolekci paměti.</span><span class="sxs-lookup"><span data-stu-id="eaea1-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="eaea1-112">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="eaea1-113">Získá statistiku pro aktuální stav kolekce systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eaea1-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="eaea1-114">GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="eaea1-115">Získá statistiku objektů vlákno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eaea1-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="eaea1-116">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="eaea1-117">Nastaví velikost segmentu a maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="eaea1-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="eaea1-118">SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="eaea1-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="eaea1-119">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="eaea1-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eaea1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaea1-120">Requirements</span></span>  
 <span data-ttu-id="eaea1-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaea1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaea1-122">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="eaea1-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="eaea1-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eaea1-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaea1-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaea1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaea1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaea1-125">See Also</span></span>  
 [<span data-ttu-id="eaea1-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eaea1-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="eaea1-127">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="eaea1-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
