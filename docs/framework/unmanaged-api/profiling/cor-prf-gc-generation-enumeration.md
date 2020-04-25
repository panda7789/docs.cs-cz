---
title: COR_PRF_GC_GENERATION – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: 0eb1f57e3505f9ce5bb8b831d30c3891e51097c3
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158564"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="1af21-102">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="1af21-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="1af21-103">Identifikuje generování kolekce uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1af21-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1af21-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="1af21-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1af21-105">Members</span></span>  
  
|<span data-ttu-id="1af21-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1af21-106">Member</span></span>|<span data-ttu-id="1af21-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1af21-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="1af21-108">Objekt je uložen jako generace 0.</span><span class="sxs-lookup"><span data-stu-id="1af21-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="1af21-109">Objekt je uložen jako generace 1.</span><span class="sxs-lookup"><span data-stu-id="1af21-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="1af21-110">Objekt je uložen jako generace 2.</span><span class="sxs-lookup"><span data-stu-id="1af21-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="1af21-111">Objekt je uložen v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="1af21-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="1af21-112">Objekt je uložen v haldě připnutých objektů.</span><span class="sxs-lookup"><span data-stu-id="1af21-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1af21-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1af21-113">Remarks</span></span>  
 <span data-ttu-id="1af21-114">Systém uvolňování paměti vylepšuje výkon správy paměti vydělením objektů do generací na základě stáří.</span><span class="sxs-lookup"><span data-stu-id="1af21-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="1af21-115">Systém uvolňování paměti aktuálně používá tři generace, očíslované 0, 1 a 2 a dva speciální segmenty haldy, jeden pro velké objekty a jeden pro připnuté objekty.</span><span class="sxs-lookup"><span data-stu-id="1af21-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="1af21-116">Objekty, jejichž velikost je větší než prahová hodnota, jsou uloženy v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="1af21-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="1af21-117">Připnuté objekty lze přidělit haldě připnutých objektů, aby se zabránilo nákladům na výkon při jejich přidělování na normální haldy.</span><span class="sxs-lookup"><span data-stu-id="1af21-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="1af21-118">Ostatní přidělené objekty začínají mimo generaci 0.</span><span class="sxs-lookup"><span data-stu-id="1af21-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="1af21-119">Všechny objekty, které existují po uvolnění paměti, jsou v generaci 0 povýšeny na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="1af21-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="1af21-120">Objekty, které existují po uvolnění paměti, dojde v 1. generaci do generace 2.</span><span class="sxs-lookup"><span data-stu-id="1af21-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="1af21-121">Použití generací znamená, že systém uvolňování paměti musí v jednom okamžiku pracovat pouze s podmnožinou přidělených objektů.</span><span class="sxs-lookup"><span data-stu-id="1af21-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="1af21-122">`COR_PRF_GC_GENERATION` Výčet je používán strukturou [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1af21-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af21-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1af21-123">Requirements</span></span>  
 <span data-ttu-id="1af21-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af21-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af21-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1af21-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1af21-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1af21-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1af21-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af21-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af21-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1af21-128">See also</span></span>

- [<span data-ttu-id="1af21-129">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1af21-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
