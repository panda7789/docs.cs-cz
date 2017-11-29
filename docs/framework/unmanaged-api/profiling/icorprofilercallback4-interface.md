---
title: "ICorProfilerCallback4 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="8978c-102">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8978c-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="8978c-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="8978c-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8978c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8978c-104">Methods</span></span>  
  
|<span data-ttu-id="8978c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-105">Method</span></span>|<span data-ttu-id="8978c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8978c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8978c-107">Getrejitparameters – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="8978c-108">Umožňuje profileru kódu nastavit alternativní kód pro nový text Rekompilované metoda příznaky generace.</span><span class="sxs-lookup"><span data-stu-id="8978c-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="8978c-109">Movedreferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="8978c-110">Sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8978c-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="8978c-111">Rejitcompilationfinished – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="8978c-112">Upozorní profileru, že kompilátoru za běhu (JIT) byla dokončena rekompilace funkce.</span><span class="sxs-lookup"><span data-stu-id="8978c-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="8978c-113">Rejitcompilationstarted – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="8978c-114">Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="8978c-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="8978c-115">Rejiterror – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="8978c-116">Sestavy k chybě při zpracování požadavku. pak ji znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="8978c-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="8978c-117">Survivingreferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="8978c-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="8978c-118">Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi.</span><span class="sxs-lookup"><span data-stu-id="8978c-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8978c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8978c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8978c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8978c-120">Requirements</span></span>  
 <span data-ttu-id="8978c-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8978c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8978c-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8978c-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8978c-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8978c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8978c-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8978c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8978c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8978c-125">See Also</span></span>  
 [<span data-ttu-id="8978c-126">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8978c-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="8978c-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8978c-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8978c-128">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8978c-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
