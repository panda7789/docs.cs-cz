---
title: ICorProfilerCallback2::SurvivingReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
ms.openlocfilehash: a83f8566dfe8e1b612f67d95a0e69947b72704ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439607"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="844ae-102">ICorProfilerCallback2::SurvivingReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="844ae-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="844ae-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span><span class="sxs-lookup"><span data-stu-id="844ae-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="844ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="844ae-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="844ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="844ae-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="844ae-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span><span class="sxs-lookup"><span data-stu-id="844ae-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="844ae-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span><span class="sxs-lookup"><span data-stu-id="844ae-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="844ae-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span><span class="sxs-lookup"><span data-stu-id="844ae-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="844ae-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span><span class="sxs-lookup"><span data-stu-id="844ae-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="844ae-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span><span class="sxs-lookup"><span data-stu-id="844ae-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="844ae-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span><span class="sxs-lookup"><span data-stu-id="844ae-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="844ae-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span><span class="sxs-lookup"><span data-stu-id="844ae-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="844ae-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="844ae-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="844ae-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span><span class="sxs-lookup"><span data-stu-id="844ae-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="844ae-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span><span class="sxs-lookup"><span data-stu-id="844ae-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="844ae-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span><span class="sxs-lookup"><span data-stu-id="844ae-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="844ae-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span><span class="sxs-lookup"><span data-stu-id="844ae-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="844ae-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span><span class="sxs-lookup"><span data-stu-id="844ae-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="844ae-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="844ae-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="844ae-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span><span class="sxs-lookup"><span data-stu-id="844ae-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="844ae-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span><span class="sxs-lookup"><span data-stu-id="844ae-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="844ae-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span><span class="sxs-lookup"><span data-stu-id="844ae-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="844ae-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span><span class="sxs-lookup"><span data-stu-id="844ae-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="844ae-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span><span class="sxs-lookup"><span data-stu-id="844ae-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="844ae-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span><span class="sxs-lookup"><span data-stu-id="844ae-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="844ae-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span><span class="sxs-lookup"><span data-stu-id="844ae-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="844ae-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span><span class="sxs-lookup"><span data-stu-id="844ae-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="844ae-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="844ae-128">Requirements</span></span>  
 <span data-ttu-id="844ae-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="844ae-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="844ae-130">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="844ae-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="844ae-131">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="844ae-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="844ae-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="844ae-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844ae-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="844ae-133">See also</span></span>

- [<span data-ttu-id="844ae-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="844ae-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="844ae-135">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="844ae-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="844ae-136">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="844ae-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
