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
ms.openlocfilehash: 1b85c48859ac29738347d112dd0466a76bfdfd2c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865334"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="bd1dc-102">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd1dc-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="bd1dc-103">Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá ke sdělování informací do profileru.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd1dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd1dc-104">Methods</span></span>  
  
|<span data-ttu-id="bd1dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-105">Method</span></span>|<span data-ttu-id="bd1dc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bd1dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd1dc-107">GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="bd1dc-108">Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="bd1dc-109">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="bd1dc-110">Nahlásí nové rozložení objektů v haldě jako výsledek komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="bd1dc-111">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="bd1dc-112">Upozorní profileru, že kompilátor JIT (just-in-time) dokončil rekompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="bd1dc-113">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="bd1dc-114">Upozorní profileru, že kompilátor JIT (just-in-time) začal znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="bd1dc-115">ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="bd1dc-116">Oznamuje chybu při zpracování žádosti o opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="bd1dc-117">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1dc-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="bd1dc-118">Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bd1dc-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd1dc-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd1dc-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1dc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd1dc-120">Requirements</span></span>  
 <span data-ttu-id="bd1dc-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1dc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1dc-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd1dc-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd1dc-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd1dc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd1dc-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1dc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1dc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd1dc-125">See also</span></span>

- [<span data-ttu-id="bd1dc-126">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd1dc-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="bd1dc-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bd1dc-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bd1dc-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd1dc-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
