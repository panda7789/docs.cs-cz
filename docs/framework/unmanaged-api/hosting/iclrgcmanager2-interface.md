---
title: "ICLRGCManager2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2
helpviewer_keywords: ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a8b51cf4297c1ccadbef8730c06148263d310e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="87d2f-102">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87d2f-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="87d2f-103">Poskytuje metody, které umožňují hostitele k interakci s systém kolekce paměti modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="87d2f-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87d2f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="87d2f-104">Methods</span></span>  
  
|<span data-ttu-id="87d2f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="87d2f-105">Method</span></span>|<span data-ttu-id="87d2f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="87d2f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87d2f-107">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="87d2f-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="87d2f-108">Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="87d2f-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="87d2f-109">Umožňuje 0. generace a velikost segmentu větší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="87d2f-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87d2f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87d2f-110">Remarks</span></span>  
 <span data-ttu-id="87d2f-111">Toto rozhraní dědí z [iclrgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="87d2f-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="87d2f-112">Modul CLR (CLR) implementuje mechanismus kolekce jeho paměti s spravovaný <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="87d2f-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="87d2f-113">Další informace o systém kolekce paměti najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="87d2f-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d2f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87d2f-114">Requirements</span></span>  
 <span data-ttu-id="87d2f-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d2f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d2f-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87d2f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87d2f-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87d2f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87d2f-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d2f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d2f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="87d2f-119">See Also</span></span>  
 [<span data-ttu-id="87d2f-120">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="87d2f-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="87d2f-121">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="87d2f-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="87d2f-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87d2f-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="87d2f-123">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="87d2f-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="87d2f-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="87d2f-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="87d2f-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="87d2f-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
