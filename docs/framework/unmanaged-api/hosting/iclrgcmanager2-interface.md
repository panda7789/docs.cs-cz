---
title: ICLRGCManager2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54707d4c767fbb644ed892767be8351d2fd95b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966191"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="2cd00-102">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cd00-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="2cd00-103">Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2cd00-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cd00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2cd00-104">Methods</span></span>  
  
|<span data-ttu-id="2cd00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2cd00-105">Method</span></span>|<span data-ttu-id="2cd00-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2cd00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cd00-107">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="2cd00-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="2cd00-108">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2cd00-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="2cd00-109">Povoluje generaci 0 a velikosti segmentů větší `DWORD`než.</span><span class="sxs-lookup"><span data-stu-id="2cd00-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd00-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cd00-110">Remarks</span></span>  
 <span data-ttu-id="2cd00-111">Toto rozhraní dědí z [rozhraní ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2cd00-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="2cd00-112">Modul CLR (Common Language Runtime) implementuje svůj mechanizmus uvolňování paměti se <xref:System.GC> spravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="2cd00-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="2cd00-113">Další informace o systému uvolňování paměti naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="2cd00-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd00-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cd00-114">Requirements</span></span>  
 <span data-ttu-id="2cd00-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd00-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd00-116">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2cd00-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cd00-117">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2cd00-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cd00-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd00-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd00-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cd00-119">See also</span></span>

- [<span data-ttu-id="2cd00-120">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="2cd00-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="2cd00-121">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="2cd00-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="2cd00-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cd00-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2cd00-123">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="2cd00-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2cd00-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2cd00-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2cd00-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="2cd00-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
