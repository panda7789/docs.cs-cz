---
title: "ICorProfilerCallback2::GarbageCollectionStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1e79eea059fab4810ece12dbc264f3d3b08b7ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="52a04-102">ICorProfilerCallback2::GarbageCollectionStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="52a04-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="52a04-103">Upozorní profileru kódu, aby bylo zahájeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="52a04-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52a04-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52a04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52a04-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="52a04-106">[v] Celkový počet záznamů v `generationCollected` pole.</span><span class="sxs-lookup"><span data-stu-id="52a04-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="52a04-107">[v] Pole logické hodnoty, které jsou `true` Pokud generace, která odpovídá pole indexu je shromažďují tento uvolňování paměti; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="52a04-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="52a04-108">Pole není indexované podle hodnotu [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčtu, který označuje generování.</span><span class="sxs-lookup"><span data-stu-id="52a04-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="52a04-109">[v] Hodnota [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) byla vyvolané výčet, který označuje z důvodu uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="52a04-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a04-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52a04-110">Remarks</span></span>  
 <span data-ttu-id="52a04-111">Všechny zpětná volání, které se vztahují k této kolekci paměti dojde k mezi `GarbageCollectionStarted` zpětného volání a odpovídající [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="52a04-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="52a04-112">Ve stejném vlákně, nemusí dojít tyto zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="52a04-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="52a04-113">Je bezpečné pro přístup z profileru ke kontrole objekty do jejich původního umístění během `GarbageCollectionStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="52a04-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="52a04-114">Uvolňování paměti zahájíte přesunutí objekty po návratu z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="52a04-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="52a04-115">Po profileru vrátila z této zpětné volání, profileru měli zvážit všechna ID objektu je neplatná, dokud neobdrží `ICorProfilerCallback2::GarbageCollectionFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="52a04-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a04-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52a04-116">Requirements</span></span>  
 <span data-ttu-id="52a04-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52a04-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a04-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52a04-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52a04-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a04-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a04-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a04-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a04-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="52a04-121">See Also</span></span>  
 [<span data-ttu-id="52a04-122">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52a04-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="52a04-123">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52a04-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
