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
ms.openlocfilehash: 167e2477e5185112408793e145bc5a4fabea7fc8
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377620"
---
# <a name="igchost-interface"></a><span data-ttu-id="ae227-102">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae227-102">IGCHost Interface</span></span>
<span data-ttu-id="ae227-103">Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae227-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae227-104">Od verze rozhraní .NET Framework 4.5, můžete použít [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metoda nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost 0. generace kolekce systému uvolňování paměti na hodnoty vyšší než `DWORD` limit, který je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ae227-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae227-105">Toto rozhraní je jenom na expertní použití.</span><span class="sxs-lookup"><span data-stu-id="ae227-105">This interface is for expert usage only.</span></span> <span data-ttu-id="ae227-106">Pokud použili nesprávně může ovlivnit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae227-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae227-107">Metody</span><span class="sxs-lookup"><span data-stu-id="ae227-107">Methods</span></span>  
  
|<span data-ttu-id="ae227-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-108">Method</span></span>|<span data-ttu-id="ae227-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ae227-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae227-110">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="ae227-111">Vynutí kolekce vyskytují pro danou generaci bez ohledu na stav v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae227-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="ae227-112">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="ae227-113">Získá statistiku pro aktuální stav systému uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="ae227-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="ae227-114">GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="ae227-115">Získá statistiku vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae227-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="ae227-116">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="ae227-117">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="ae227-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="ae227-118">SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="ae227-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="ae227-119">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ae227-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae227-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae227-120">Requirements</span></span>  
 <span data-ttu-id="ae227-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae227-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae227-122">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ae227-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ae227-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae227-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae227-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae227-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae227-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae227-125">See also</span></span>

- [<span data-ttu-id="ae227-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ae227-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ae227-127">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="ae227-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
