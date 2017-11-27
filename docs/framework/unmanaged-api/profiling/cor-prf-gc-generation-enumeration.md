---
title: "COR_PRF_GC_GENERATION – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION
helpviewer_keywords: COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a296dd333579f9d0e734b7c00a8adb648605295d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="5b163-102">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="5b163-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="5b163-103">Identifikuje generace kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="5b163-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b163-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="5b163-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5b163-105">Members</span></span>  
  
|<span data-ttu-id="5b163-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5b163-106">Member</span></span>|<span data-ttu-id="5b163-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5b163-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="5b163-108">Objekt se uloží jako 0. generace.</span><span class="sxs-lookup"><span data-stu-id="5b163-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="5b163-109">Objekt se uloží jako generace 1.</span><span class="sxs-lookup"><span data-stu-id="5b163-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="5b163-110">Objekt se uloží jako generace 2.</span><span class="sxs-lookup"><span data-stu-id="5b163-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="5b163-111">Objekt se uloží v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="5b163-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b163-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b163-112">Remarks</span></span>  
 <span data-ttu-id="5b163-113">Uvolňování paměti zlepšuje výkon správy paměti dělicí objekty do generace podle stáří.</span><span class="sxs-lookup"><span data-stu-id="5b163-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="5b163-114">Garbage collector v současné době používá tři generace, číslované 0, 1 a 2 a speciální haldy segment, který se používá pro velké objekty.</span><span class="sxs-lookup"><span data-stu-id="5b163-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="5b163-115">Objekty, jejichž velikost je větší než určitou hodnotu jsou uloženy v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="5b163-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="5b163-116">Další přidělené objekty spustí patřící do generace 0.</span><span class="sxs-lookup"><span data-stu-id="5b163-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="5b163-117">Všechny objekty, které existují po dojde k uvolnění paměti v generaci 0 povýšené na 1. generace.</span><span class="sxs-lookup"><span data-stu-id="5b163-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="5b163-118">Objekty, které existují po dojde k uvolnění paměti v generaci 1, přesuňte do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="5b163-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="5b163-119">Použití generace znamená, že má kolekce uvolňování paměti pro práci s jenom podmnožinu přidělené objekty v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="5b163-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="5b163-120">`COR_PRF_GC_GENERATION` Výčet je používán [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktura.</span><span class="sxs-lookup"><span data-stu-id="5b163-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b163-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b163-121">Requirements</span></span>  
 <span data-ttu-id="5b163-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b163-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b163-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b163-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b163-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b163-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b163-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b163-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b163-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b163-126">See Also</span></span>  
 [<span data-ttu-id="5b163-127">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="5b163-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
