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
ms.openlocfilehash: 3eb1f46900199db65be5d14c56bfc0b6f55bf269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205131"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="fbbb2-102">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbbb2-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="fbbb2-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbbb2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fbbb2-104">Methods</span></span>  
  
|<span data-ttu-id="fbbb2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-105">Method</span></span>|<span data-ttu-id="fbbb2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fbbb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbbb2-107">GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="fbbb2-108">Umožňuje profileru kódu nastavit alternativní kód generování příznaky pro nové tělo překompilovanou metody.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="fbbb2-109">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="fbbb2-110">Sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="fbbb2-111">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="fbbb2-112">Oznámí profileru, kompilátor just-in-time (JIT) dokončil rekompilace funkce.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="fbbb2-113">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="fbbb2-114">Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna znovu zkompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="fbbb2-115">ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="fbbb2-116">Sestavy došlo k chybě při zpracování požadavku na opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="fbbb2-117">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbb2-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="fbbb2-118">Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním.</span><span class="sxs-lookup"><span data-stu-id="fbbb2-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbbb2-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbbb2-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbbb2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbbb2-120">Requirements</span></span>  
 <span data-ttu-id="fbbb2-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbbb2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbbb2-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbbb2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbbb2-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbbb2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbbb2-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbbb2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbb2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbbb2-125">See also</span></span>

- [<span data-ttu-id="fbbb2-126">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbbb2-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="fbbb2-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fbbb2-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fbbb2-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbbb2-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
