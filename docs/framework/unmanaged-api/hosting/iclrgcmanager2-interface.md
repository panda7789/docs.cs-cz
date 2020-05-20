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
ms.openlocfilehash: 0f3ecc0d497eaee937647df47ba0956335a2fe41
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703945"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="f78b1-102">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f78b1-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="f78b1-103">Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f78b1-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f78b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f78b1-104">Methods</span></span>  
  
|<span data-ttu-id="f78b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f78b1-105">Method</span></span>|<span data-ttu-id="f78b1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f78b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f78b1-107">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f78b1-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="f78b1-108">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f78b1-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="f78b1-109">Povoluje generaci 0 a velikosti segmentů větší než `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="f78b1-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f78b1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f78b1-110">Remarks</span></span>  
 <span data-ttu-id="f78b1-111">Toto rozhraní dědí z [rozhraní ICLRGCManager](iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="f78b1-112">Modul CLR (Common Language Runtime) implementuje svůj mechanizmus uvolňování paměti se spravovaným <xref:System.GC> typem.</span><span class="sxs-lookup"><span data-stu-id="f78b1-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="f78b1-113">Další informace o systému uvolňování paměti naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f78b1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f78b1-114">Requirements</span></span>  
 <span data-ttu-id="f78b1-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f78b1-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f78b1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f78b1-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f78b1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f78b1-118">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f78b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78b1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f78b1-119">See also</span></span>

- [<span data-ttu-id="f78b1-120">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="f78b1-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="f78b1-121">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="f78b1-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="f78b1-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f78b1-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f78b1-123">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="f78b1-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f78b1-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f78b1-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f78b1-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="f78b1-125">Hosting</span></span>](index.md)
