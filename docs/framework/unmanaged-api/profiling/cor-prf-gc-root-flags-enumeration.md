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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f179e3b01d6c3b34dfa765565a0fc38d0ba867c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753694"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="6d4a1-102">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="6d4a1-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="6d4a1-103">Označuje vlastnost kořenové kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d4a1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6d4a1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6d4a1-105">Members</span></span>  
  
|<span data-ttu-id="6d4a1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6d4a1-106">Member</span></span>|<span data-ttu-id="6d4a1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6d4a1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="6d4a1-108">Kořen brání uvolňování získat přechodem na objekt.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="6d4a1-109">Kořen nebrání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="6d4a1-110">Kořenovém adresáři odkazuje na pole objektu, nikoli samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="6d4a1-111">Kořen zabrání uvolňování paměti, pokud je počet odkazů na objekt je určitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d4a1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d4a1-112">Remarks</span></span>  
 <span data-ttu-id="6d4a1-113">`COR_PRF_GC_ROOT_FLAGS` je bitová maska, která poskytuje další informace o speciální kořenové adresáře.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="6d4a1-114">Ale ne všechny kořeny jsou speciální.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-114">However, not all roots are special.</span></span> <span data-ttu-id="6d4a1-115">Například některé kořeny nejsou slabé odkazy, vnitřních ukazatelů, připnuté nebo referenčně započítaný.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="6d4a1-116">Pro takové kořeny nejsou žádné příznaky vyjádřit.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="6d4a1-117">Proto metody, které používají tento výčet, jako [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody send 0 bitové masky příznaky, která udává, že všechny příznaky jsou vypnuté.</span><span class="sxs-lookup"><span data-stu-id="6d4a1-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4a1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d4a1-118">Requirements</span></span>  
 <span data-ttu-id="6d4a1-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4a1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4a1-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d4a1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d4a1-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d4a1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d4a1-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d4a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4a1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d4a1-123">See also</span></span>

- [<span data-ttu-id="6d4a1-124">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6d4a1-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
