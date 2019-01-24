---
title: ICorProfilerCallback4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a96aadcec6cb3c4f4680499585bf1c950bc5ddd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525307"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="ae57d-102">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae57d-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="ae57d-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="ae57d-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae57d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae57d-104">Methods</span></span>  
  
|<span data-ttu-id="ae57d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-105">Method</span></span>|<span data-ttu-id="ae57d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ae57d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae57d-107">GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="ae57d-108">Umožňuje profileru kódu nastavit alternativní kód generování příznaky pro nové tělo překompilovanou metody.</span><span class="sxs-lookup"><span data-stu-id="ae57d-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="ae57d-109">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="ae57d-110">Sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae57d-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="ae57d-111">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="ae57d-112">Oznámí profileru, kompilátor just-in-time (JIT) dokončil rekompilace funkce.</span><span class="sxs-lookup"><span data-stu-id="ae57d-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="ae57d-113">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="ae57d-114">Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna znovu zkompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="ae57d-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="ae57d-115">ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="ae57d-116">Sestavy došlo k chybě při zpracování požadavku na opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ae57d-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="ae57d-117">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ae57d-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="ae57d-118">Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním.</span><span class="sxs-lookup"><span data-stu-id="ae57d-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae57d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae57d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae57d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae57d-120">Requirements</span></span>  
 <span data-ttu-id="ae57d-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae57d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae57d-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae57d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae57d-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae57d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae57d-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae57d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae57d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae57d-125">See also</span></span>
- [<span data-ttu-id="ae57d-126">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae57d-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="ae57d-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ae57d-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ae57d-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae57d-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
