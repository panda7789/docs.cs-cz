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
ms.openlocfilehash: a3394820f673e35777e1749229d4f8319841ca58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439388"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="85d18-102">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d18-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="85d18-103">Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá ke sdělování informací do profileru.</span><span class="sxs-lookup"><span data-stu-id="85d18-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85d18-104">Metody</span><span class="sxs-lookup"><span data-stu-id="85d18-104">Methods</span></span>  
  
|<span data-ttu-id="85d18-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-105">Method</span></span>|<span data-ttu-id="85d18-106">Popis</span><span class="sxs-lookup"><span data-stu-id="85d18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85d18-107">GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="85d18-108">Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.</span><span class="sxs-lookup"><span data-stu-id="85d18-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="85d18-109">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="85d18-110">Nahlásí nové rozložení objektů v haldě jako výsledek komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="85d18-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="85d18-111">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="85d18-112">Upozorní profileru, že kompilátor JIT (just-in-time) dokončil rekompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="85d18-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="85d18-113">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="85d18-114">Upozorní profileru, že kompilátor JIT (just-in-time) začal znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="85d18-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="85d18-115">ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="85d18-116">Oznamuje chybu při zpracování žádosti o opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="85d18-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="85d18-117">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="85d18-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="85d18-118">Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="85d18-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85d18-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85d18-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d18-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85d18-120">Requirements</span></span>  
 <span data-ttu-id="85d18-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d18-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d18-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="85d18-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85d18-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85d18-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85d18-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d18-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d18-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85d18-125">See also</span></span>

- [<span data-ttu-id="85d18-126">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d18-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="85d18-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="85d18-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="85d18-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d18-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
