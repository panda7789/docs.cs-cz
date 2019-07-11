---
title: ICorProfilerCallback4::ReJITCompilationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58293929b576493d3751f9ce30ba00cec92e180c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758163"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="42ea8-102">ICorProfilerCallback4::ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="42ea8-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="42ea8-103">Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna znovu zkompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="42ea8-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ea8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42ea8-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42ea8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42ea8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="42ea8-106">[in] ID funkce, které kompilátor JIT začal znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="42ea8-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="42ea8-107">[in] ID rekompilace novou verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="42ea8-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="42ea8-108">[in] `true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="42ea8-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="42ea8-109">Hodnota `true` nepoškodí modul runtime, ale může mít vliv na výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="42ea8-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42ea8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42ea8-110">Remarks</span></span>  
 <span data-ttu-id="42ea8-111">Je možné přijímat více než jednu dvojici `ReJITCompilationStarted` a [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda volá pro každou funkci kvůli způsobu, jakým modul runtime konstruktor třídy obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="42ea8-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="42ea8-112">Například modul runtime spustí znovu zkompilovat metoda A, ale třída konstruktor třídy B musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="42ea8-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="42ea8-113">Proto se modul runtime konstruktor třídy B se znovu zkompiluje a spustí ji.</span><span class="sxs-lookup"><span data-stu-id="42ea8-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="42ea8-114">Je spuštěn konstruktoru, provede volání do metody A, což způsobí, že metoda A znovu překompilovat.</span><span class="sxs-lookup"><span data-stu-id="42ea8-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="42ea8-115">V tomto scénáři je první opětovnou kompilaci metody A zastaveno.</span><span class="sxs-lookup"><span data-stu-id="42ea8-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="42ea8-116">Ale i pokusí znovu zkompilovat metoda se nahlásí se rekompilace JIT – události.</span><span class="sxs-lookup"><span data-stu-id="42ea8-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="42ea8-117">Profilovací programy musí podporovat posloupnost zpětných volání rekompilace JIT v případech, kde dva vláken současně, aby zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="42ea8-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="42ea8-118">Například, vlákna A zavolá `ReJITCompilationStarted`; však před volání vlákna A [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B vyvolá [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID – funkce z `ReJITCompilationStarted` zpětného volání pro vlákno A. Může se zdát, že ID funkce by neměl být ještě platný protože volání [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nebyl dosud nebylo přijato pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="42ea8-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="42ea8-119">Ale v takovém případě ID funkce je platný.</span><span class="sxs-lookup"><span data-stu-id="42ea8-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42ea8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42ea8-120">Requirements</span></span>  
 <span data-ttu-id="42ea8-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42ea8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42ea8-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42ea8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42ea8-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42ea8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42ea8-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42ea8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ea8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42ea8-125">See also</span></span>

- [<span data-ttu-id="42ea8-126">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42ea8-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="42ea8-127">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42ea8-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="42ea8-128">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="42ea8-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="42ea8-129">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="42ea8-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
