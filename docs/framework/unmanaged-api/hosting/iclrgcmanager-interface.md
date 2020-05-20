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
ms.openlocfilehash: 76a50be6da790ed7bd193c489d36e2823cdbe587
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616955"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="568a3-102">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="568a3-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="568a3-103">Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="568a3-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="568a3-104">Počínaje .NET Framework 4,5 lze pomocí metody [ICLRGCManager2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší, než je `DWORD` limit, který je určen metodou [SetGCStartupLimits –](iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="568a3-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="568a3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="568a3-105">Methods</span></span>  
  
|<span data-ttu-id="568a3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="568a3-106">Method</span></span>|<span data-ttu-id="568a3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="568a3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="568a3-108">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="568a3-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="568a3-109">Vynutí uvolňování paměti pro určenou generaci.</span><span class="sxs-lookup"><span data-stu-id="568a3-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="568a3-110">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="568a3-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="568a3-111">Získá sadu aktuálních statistik o systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="568a3-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="568a3-112">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="568a3-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="568a3-113">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="568a3-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="568a3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="568a3-114">Remarks</span></span>  
 <span data-ttu-id="568a3-115">Modul CLR (Common Language Runtime) implementuje svůj mechanizmus uvolňování paměti se spravovaným <xref:System.GC> typem.</span><span class="sxs-lookup"><span data-stu-id="568a3-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="568a3-116">Další informace o systému uvolňování paměti naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="568a3-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="568a3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="568a3-117">Requirements</span></span>  
 <span data-ttu-id="568a3-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="568a3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="568a3-119">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="568a3-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="568a3-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="568a3-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="568a3-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="568a3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568a3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="568a3-122">See also</span></span>

- [<span data-ttu-id="568a3-123">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="568a3-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="568a3-124">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="568a3-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="568a3-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="568a3-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="568a3-126">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="568a3-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="568a3-127">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="568a3-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="568a3-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="568a3-128">Hosting</span></span>](index.md)
