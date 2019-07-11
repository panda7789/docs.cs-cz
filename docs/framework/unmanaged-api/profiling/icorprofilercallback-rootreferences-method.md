---
title: ICorProfilerCallback::RootReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a68ea07c40c966422be6ebb663e62508032c2610
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750445"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="b9877-102">ICorProfilerCallback::RootReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="b9877-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="b9877-103">Upozornění profileru s informacemi o odkazů na kořenový po uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b9877-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9877-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9877-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9877-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9877-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="b9877-106">[in] Počet odkazů v `rootRefIds` pole.</span><span class="sxs-lookup"><span data-stu-id="b9877-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="b9877-107">[in] Pole ID objektů, které odkazují na statický objekt nebo objekt v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b9877-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9877-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9877-108">Remarks</span></span>  
 <span data-ttu-id="b9877-109">Obě `RootReferences` a [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) jsou volány pro oznámení profileru.</span><span class="sxs-lookup"><span data-stu-id="b9877-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="b9877-110">Profilery obvykle implementuje jednu z nich, ale nikoli oba současně, protože předaným informace `RootReferences2` je nadstavbou jazyka, které předáno `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="b9877-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="b9877-111">Je možné, `rootRefIds` pole tak, aby obsahovala objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b9877-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="b9877-112">Například všechny odkazy na objekty deklarované v zásobníku jsou považovány za kořeny uvolnění paměti a vždy se ohlásí.</span><span class="sxs-lookup"><span data-stu-id="b9877-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="b9877-113">ID objektů vrácených `RootReferences` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré adresy k nové adresy.</span><span class="sxs-lookup"><span data-stu-id="b9877-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="b9877-114">Proto se nesmíte pokoušet profilery pro kontrolu objektů během `RootReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="b9877-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="b9877-115">Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty se přesunuly na jejich nových umístění a můžete ho bezpečně zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="b9877-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9877-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9877-116">Requirements</span></span>  
 <span data-ttu-id="b9877-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9877-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9877-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9877-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9877-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9877-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9877-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9877-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9877-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9877-121">See also</span></span>

- [<span data-ttu-id="b9877-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9877-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
