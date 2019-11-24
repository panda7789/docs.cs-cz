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
ms.openlocfilehash: 9c96cacf508ef5c056a1ff4469247393fdfb9e9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444470"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="79888-102">ICorProfilerCallback::RootReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="79888-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="79888-103">Notifies the profiler with information about root references after garbage collection.</span><span class="sxs-lookup"><span data-stu-id="79888-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79888-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79888-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="79888-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79888-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="79888-106">[in] The number of references in the `rootRefIds` array.</span><span class="sxs-lookup"><span data-stu-id="79888-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="79888-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span><span class="sxs-lookup"><span data-stu-id="79888-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79888-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79888-108">Remarks</span></span>  
 <span data-ttu-id="79888-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span><span class="sxs-lookup"><span data-stu-id="79888-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="79888-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="79888-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="79888-111">It is possible for the `rootRefIds` array to contain a null object.</span><span class="sxs-lookup"><span data-stu-id="79888-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="79888-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span><span class="sxs-lookup"><span data-stu-id="79888-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="79888-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span><span class="sxs-lookup"><span data-stu-id="79888-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="79888-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span><span class="sxs-lookup"><span data-stu-id="79888-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="79888-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span><span class="sxs-lookup"><span data-stu-id="79888-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79888-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79888-116">Requirements</span></span>  
 <span data-ttu-id="79888-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79888-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79888-118">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79888-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79888-119">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79888-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79888-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79888-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79888-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79888-121">See also</span></span>

- [<span data-ttu-id="79888-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79888-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
