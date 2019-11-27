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
ms.openlocfilehash: ed2553f2d971deefd85f731dd39f383cd096c5b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439812"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="4e3d8-102">ICorProfilerCallback2::GarbageCollectionStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="4e3d8-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="4e3d8-103">Oznamuje profileru kódu, že se spustilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e3d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e3d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e3d8-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="4e3d8-106">pro Celkový počet položek v poli `generationCollected`.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="4e3d8-107">pro Pole logických hodnot, které jsou `true`, pokud je generace, která odpovídá indexu pole, shromažďována tímto uvolňováním paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="4e3d8-108">Pole je indexováno hodnotou [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčtu, což označuje generaci.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="4e3d8-109">pro Hodnota výčtu [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) , která označuje důvod vystavení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e3d8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e3d8-110">Remarks</span></span>  
 <span data-ttu-id="4e3d8-111">Všechna zpětná volání, která souvisí s tímto uvolňováním paměti, budou provedena mezi `GarbageCollectionStarted`ovým zpětným voláním a odpovídajícím voláním [ICorProfilerCallback2:: GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4e3d8-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="4e3d8-112">Tato zpětná volání nemusí být ve stejném vlákně.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="4e3d8-113">Profiler je bezpečně kontrolovat objekty v původních umístěních během `GarbageCollectionStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="4e3d8-114">Systém uvolňování paměti začne přesouvat objekty po návratu z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="4e3d8-115">Až se Profiler vrátí z tohoto zpětného volání, Profiler by měl považovat všechna ID objektů za neplatnou, dokud neobdrží zpětné volání `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="4e3d8-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e3d8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e3d8-116">Requirements</span></span>  
 <span data-ttu-id="4e3d8-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e3d8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e3d8-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4e3d8-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e3d8-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4e3d8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e3d8-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e3d8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3d8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e3d8-121">See also</span></span>

- [<span data-ttu-id="4e3d8-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e3d8-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4e3d8-123">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e3d8-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
