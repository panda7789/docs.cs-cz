---
title: COR_PRF_GC_ROOT_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 174486a88192bd5ff11074930d5ad3375603f8a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449469"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="a6c12-102">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="a6c12-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="a6c12-103">Označuje vlastnost kořenu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a6c12-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c12-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6c12-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="a6c12-105">Members</span><span class="sxs-lookup"><span data-stu-id="a6c12-105">Members</span></span>  
  
|<span data-ttu-id="a6c12-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a6c12-106">Member</span></span>|<span data-ttu-id="a6c12-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a6c12-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="a6c12-108">Kořen zabraňuje uvolňování paměti v přesunutí objektu.</span><span class="sxs-lookup"><span data-stu-id="a6c12-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="a6c12-109">Kořen nebrání v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a6c12-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="a6c12-110">Kořen odkazuje na pole objektu, nikoli na samotný objekt.</span><span class="sxs-lookup"><span data-stu-id="a6c12-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="a6c12-111">Kořen zabraňuje uvolňování paměti, pokud je počet odkazů objektu určitou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a6c12-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6c12-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6c12-112">Remarks</span></span>  
 <span data-ttu-id="a6c12-113">`COR_PRF_GC_ROOT_FLAGS` je Bitová maska, která poskytuje další informace o speciálních kořenech.</span><span class="sxs-lookup"><span data-stu-id="a6c12-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="a6c12-114">Ale ne všechny kořeny jsou speciální.</span><span class="sxs-lookup"><span data-stu-id="a6c12-114">However, not all roots are special.</span></span> <span data-ttu-id="a6c12-115">Například některé kořeny neobsahují slabé odkazy, vnitřní ukazatele, připnuté nebo odpočítané odkazy.</span><span class="sxs-lookup"><span data-stu-id="a6c12-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="a6c12-116">Pro tyto kořeny neexistují žádné příznaky k vyjádření.</span><span class="sxs-lookup"><span data-stu-id="a6c12-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="a6c12-117">Proto metody, které používají tento výčet, jako je například metoda [ICorProfilerCallback2:: RootReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) , odesílají 0 pro bitovou masku příznaků, což značí, že jsou všechny příznaky vypnuty.</span><span class="sxs-lookup"><span data-stu-id="a6c12-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6c12-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6c12-118">Requirements</span></span>  
 <span data-ttu-id="a6c12-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6c12-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6c12-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a6c12-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6c12-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6c12-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6c12-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6c12-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c12-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6c12-123">See also</span></span>

- [<span data-ttu-id="a6c12-124">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a6c12-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
