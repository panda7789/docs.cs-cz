---
title: ICorProfilerCallback2::GarbageCollectionStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c610445d5467a49b8a50b279d8f7fe706e21f73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555658"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="dab01-102">ICorProfilerCallback2::GarbageCollectionStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="dab01-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="dab01-103">Upozornění profileru kódu, uvolňování paměti byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="dab01-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dab01-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dab01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dab01-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="dab01-106">[in] Celkový počet položek v `generationCollected` pole.</span><span class="sxs-lookup"><span data-stu-id="dab01-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="dab01-107">[in] Pole logické hodnoty, které jsou `true` jestli ke generaci, kterou odpovídá index pole je shromážděných v této kolekci uvolňování paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="dab01-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="dab01-108">Pole je indexované podle hodnoty [cor_prf_gc_generation –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčet, který označuje jeho generaci.</span><span class="sxs-lookup"><span data-stu-id="dab01-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="dab01-109">[in] Hodnota [cor_prf_gc_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) bylo získáno výčet, který označuje důvod kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dab01-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab01-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dab01-110">Remarks</span></span>  
 <span data-ttu-id="dab01-111">Všechny zpětná volání, které se týkají této kolekce uvolnění paměti dojde mezi `GarbageCollectionStarted` zpětného volání a odpovídající [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dab01-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="dab01-112">Tato zpětná volání nemusí dojít k ve stejném vlákně.</span><span class="sxs-lookup"><span data-stu-id="dab01-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="dab01-113">Je bezpečný pro profiler pro kontrolu objektů v jejich původním umístění během `GarbageCollectionStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dab01-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="dab01-114">Uvolňování paměti se začne pohybujících se objektů po návrat z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="dab01-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="dab01-115">Po profiler vrátil z této zpětné volání, profiler zvažte všechna ID objektu není platný až do obdržení `ICorProfilerCallback2::GarbageCollectionFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dab01-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab01-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dab01-116">Requirements</span></span>  
 <span data-ttu-id="dab01-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dab01-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab01-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dab01-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dab01-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dab01-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dab01-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab01-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab01-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab01-121">See also</span></span>
- [<span data-ttu-id="dab01-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dab01-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="dab01-123">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dab01-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
