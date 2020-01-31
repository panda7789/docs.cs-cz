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
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865776"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="7c12f-102">ICorProfilerCallback2::GarbageCollectionStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="7c12f-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="7c12f-103">Oznamuje profileru kódu, že se spustilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7c12f-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c12f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c12f-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c12f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c12f-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="7c12f-106">pro Celkový počet položek v poli `generationCollected`.</span><span class="sxs-lookup"><span data-stu-id="7c12f-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="7c12f-107">pro Pole logických hodnot, které jsou `true`, pokud je generace, která odpovídá indexu pole, shromažďována tímto uvolňováním paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7c12f-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="7c12f-108">Pole je indexováno hodnotou [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) výčtu, což označuje generaci.</span><span class="sxs-lookup"><span data-stu-id="7c12f-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="7c12f-109">pro Hodnota výčtu [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , která označuje důvod vystavení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7c12f-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c12f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c12f-110">Remarks</span></span>  
 <span data-ttu-id="7c12f-111">Všechna zpětná volání, která souvisí s tímto uvolňováním paměti, budou provedena mezi `GarbageCollectionStarted`ovým zpětným voláním a odpovídajícím voláním [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7c12f-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="7c12f-112">Tato zpětná volání nemusí být ve stejném vlákně.</span><span class="sxs-lookup"><span data-stu-id="7c12f-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="7c12f-113">Profiler je bezpečně kontrolovat objekty v původních umístěních během `GarbageCollectionStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7c12f-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="7c12f-114">Systém uvolňování paměti začne přesouvat objekty po návratu z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="7c12f-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="7c12f-115">Až se Profiler vrátí z tohoto zpětného volání, Profiler by měl považovat všechna ID objektů za neplatnou, dokud neobdrží zpětné volání `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="7c12f-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c12f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c12f-116">Requirements</span></span>  
 <span data-ttu-id="7c12f-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c12f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c12f-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7c12f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c12f-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c12f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c12f-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c12f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c12f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c12f-121">See also</span></span>

- [<span data-ttu-id="7c12f-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c12f-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7c12f-123">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c12f-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
