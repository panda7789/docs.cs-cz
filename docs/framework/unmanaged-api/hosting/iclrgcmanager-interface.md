---
title: "ICLRGCManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7215ce1423e8541b23daae7b9e051ade6e25f1b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="1c046-102">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c046-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="1c046-103">Poskytuje metody, které umožňují hostitele k interakci s systém kolekce paměti modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1c046-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c046-104">Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete použít [iclrgcmanager2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodu a nastavit velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD` omezení, která je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="1c046-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c046-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1c046-105">Methods</span></span>  
  
|<span data-ttu-id="1c046-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c046-106">Method</span></span>|<span data-ttu-id="1c046-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1c046-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c046-108">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="1c046-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="1c046-109">Vynutí uvolnění paměti pro zadané generaci.</span><span class="sxs-lookup"><span data-stu-id="1c046-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="1c046-110">Getstats – metoda</span><span class="sxs-lookup"><span data-stu-id="1c046-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="1c046-111">Získá sadu aktuální statistické údaje o kolekci systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1c046-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="1c046-112">Setgcstartuplimits – metoda</span><span class="sxs-lookup"><span data-stu-id="1c046-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="1c046-113">Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="1c046-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c046-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c046-114">Remarks</span></span>  
 <span data-ttu-id="1c046-115">Modul CLR (CLR) implementuje mechanismus kolekce jeho paměti s spravovaný <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="1c046-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="1c046-116">Další informace o systém kolekce paměti najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="1c046-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c046-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c046-117">Requirements</span></span>  
 <span data-ttu-id="1c046-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c046-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c046-119">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1c046-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c046-120">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c046-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c046-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c046-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c046-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c046-122">See Also</span></span>  
 [<span data-ttu-id="1c046-123">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="1c046-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="1c046-124">Cor_gc_stats – struktura</span><span class="sxs-lookup"><span data-stu-id="1c046-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="1c046-125">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c046-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="1c046-126">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1c046-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="1c046-127">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="1c046-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1c046-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="1c046-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
