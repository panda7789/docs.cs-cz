---
title: ICLRGCManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27899994a048c7000746a2e92516776fd23f8e2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624389"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="4fc1b-102">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fc1b-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="4fc1b-103">Poskytuje metody, které povolí hostitelské pracovat s common language runtime uvolňování paměti kolekce systému.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fc1b-104">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete použít [iclrgcmanager2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metody nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost 0. generace kolekce systému uvolňování paměti na hodnoty vyšší než `DWORD` limit, který je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fc1b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4fc1b-105">Methods</span></span>  
  
|<span data-ttu-id="4fc1b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4fc1b-106">Method</span></span>|<span data-ttu-id="4fc1b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4fc1b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fc1b-108">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="4fc1b-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="4fc1b-109">Vynutí uvolnění pro zadané generace.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="4fc1b-110">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="4fc1b-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="4fc1b-111">Získá sadu aktuální statistické údaje o systému uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="4fc1b-112">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="4fc1b-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="4fc1b-113">Nastaví velikost segmentu kolekce uvolnění paměti a maximální velikost systému kolekce uvolnění paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fc1b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fc1b-114">Remarks</span></span>  
 <span data-ttu-id="4fc1b-115">Modul CLR (CLR) implementuje mechanismus jeho uvolňování paměti kolekce s spravovanou <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="4fc1b-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="4fc1b-116">Další informace o systému uvolňování paměti kolekce najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fc1b-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc1b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fc1b-117">Requirements</span></span>  
 <span data-ttu-id="4fc1b-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc1b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc1b-119">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4fc1b-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fc1b-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fc1b-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fc1b-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc1b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc1b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fc1b-122">See also</span></span>
- [<span data-ttu-id="4fc1b-123">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="4fc1b-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="4fc1b-124">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="4fc1b-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="4fc1b-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fc1b-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4fc1b-126">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="4fc1b-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="4fc1b-127">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4fc1b-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4fc1b-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="4fc1b-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
