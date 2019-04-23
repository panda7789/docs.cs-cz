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
ms.openlocfilehash: a89a7ef34418163d790fd055de681c1cdf989e57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226908"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="f4475-102">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4475-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="f4475-103">Poskytuje metody, které povolí hostitelské pracovat s common language runtime uvolňování paměti kolekce systému.</span><span class="sxs-lookup"><span data-stu-id="f4475-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4475-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f4475-104">Methods</span></span>  
  
|<span data-ttu-id="f4475-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f4475-105">Method</span></span>|<span data-ttu-id="f4475-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f4475-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4475-107">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f4475-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="f4475-108">Nastaví velikost segmentu kolekce uvolnění paměti a maximální velikost systému kolekce uvolnění paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="f4475-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="f4475-109">Umožňuje 0. generace a větší velikosti segmentů `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="f4475-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4475-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4475-110">Remarks</span></span>  
 <span data-ttu-id="f4475-111">Toto rozhraní se dědí z [iclrgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f4475-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="f4475-112">Modul CLR (CLR) implementuje mechanismus jeho uvolňování paměti kolekce s spravovanou <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="f4475-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="f4475-113">Další informace o systému uvolňování paměti kolekce najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4475-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4475-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4475-114">Requirements</span></span>  
 <span data-ttu-id="f4475-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4475-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4475-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4475-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4475-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4475-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4475-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4475-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4475-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4475-119">See also</span></span>

- [<span data-ttu-id="f4475-120">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="f4475-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="f4475-121">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="f4475-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="f4475-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4475-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f4475-123">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="f4475-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f4475-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f4475-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f4475-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="f4475-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
