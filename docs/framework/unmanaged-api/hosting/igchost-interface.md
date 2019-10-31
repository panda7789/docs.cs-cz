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
ms.openlocfilehash: 91483d5bdf1eb8e6b03d7691e2a95074e3789317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134880"
---
# <a name="igchost-interface"></a><span data-ttu-id="f9a3b-102">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9a3b-102">IGCHost Interface</span></span>
<span data-ttu-id="f9a3b-103">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9a3b-104">Počínaje .NET Framework 4,5 lze pomocí metody [IGCHost2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty vyšší než omezení `DWORD`. který je uložen metodou [SetGCStartupLimits –](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f9a3b-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9a3b-105">Toto rozhraní je jenom pro odborné použití.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-105">This interface is for expert usage only.</span></span> <span data-ttu-id="f9a3b-106">Může ovlivnit výkon aplikace, pokud se používá nesprávně.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9a3b-107">Metody</span><span class="sxs-lookup"><span data-stu-id="f9a3b-107">Methods</span></span>  
  
|<span data-ttu-id="f9a3b-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-108">Method</span></span>|<span data-ttu-id="f9a3b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f9a3b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9a3b-110">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="f9a3b-111">Vynutí, aby se kolekce stala pro danou generaci, bez ohledu na stav aktuálního uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="f9a3b-112">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="f9a3b-113">Získá statistiku pro aktuální stav systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="f9a3b-114">GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="f9a3b-115">Načte statistiku jednotlivých vláken pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="f9a3b-116">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="f9a3b-117">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="f9a3b-118">SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a3b-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="f9a3b-119">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f9a3b-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9a3b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9a3b-120">Requirements</span></span>  
 <span data-ttu-id="f9a3b-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a3b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a3b-122">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="f9a3b-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f9a3b-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9a3b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9a3b-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a3b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a3b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9a3b-125">See also</span></span>

- [<span data-ttu-id="f9a3b-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f9a3b-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f9a3b-127">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="f9a3b-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
