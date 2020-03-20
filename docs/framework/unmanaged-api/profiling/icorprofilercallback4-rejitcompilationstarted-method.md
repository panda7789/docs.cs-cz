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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177084"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="b7978-102">ICorProfilerCallback4::ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="b7978-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="b7978-103">Upozorní profiler, že kompilátor just-in-time (JIT) začal znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="b7978-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7978-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7978-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7978-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7978-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b7978-106">[v] ID funkce, která kompilátor JIT začala znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="b7978-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="b7978-107">[v] ID rekompilace nové verze funkce.</span><span class="sxs-lookup"><span data-stu-id="b7978-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="b7978-108">[v] `true` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu.</span><span class="sxs-lookup"><span data-stu-id="b7978-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="b7978-109">Hodnota `true` nepoškozuje za běhu, ale může ovlivnit výsledky profilování.</span><span class="sxs-lookup"><span data-stu-id="b7978-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7978-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7978-110">Remarks</span></span>  
 <span data-ttu-id="b7978-111">Je možné přijímat více než `ReJITCompilationStarted` jeden pár a [ReJITCompilationFinish](icorprofilercallback4-rejitcompilationfinished-method.md) volání metody pro každou funkci z důvodu způsobu runtime zpracovává konstruktory třídy.</span><span class="sxs-lookup"><span data-stu-id="b7978-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="b7978-112">Například runtime začne překompilovat metodu A, ale konstruktor třídy pro třídu B musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="b7978-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="b7978-113">Proto runtime překompiluje konstruktor pro třídu B a spustí jej.</span><span class="sxs-lookup"><span data-stu-id="b7978-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="b7978-114">Při spuštění konstruktoru provede volání metody A, která způsobí, že metoda A znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="b7978-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="b7978-115">V tomto scénáři je zastavena první rekompilace metody A.</span><span class="sxs-lookup"><span data-stu-id="b7978-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="b7978-116">Oba pokusy o překompilování metody A jsou však hlášeny s událostmi rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="b7978-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="b7978-117">Profilovací programy musí podporovat posloupnost jit recompilation zpětná volání v případech, kdy dvě vlákna jsou současně volání.</span><span class="sxs-lookup"><span data-stu-id="b7978-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="b7978-118">Například volání vlákna A `ReJITCompilationStarted`; však před podproces volání [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B volání [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z zpětného `ReJITCompilationStarted` volání pro vlákno A. Může se zdát, že ID funkce by ještě neměla být platná, protože volání [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) ještě nebyla přijata profiler.</span><span class="sxs-lookup"><span data-stu-id="b7978-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="b7978-119">V tomto případě je však ID funkce platné.</span><span class="sxs-lookup"><span data-stu-id="b7978-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7978-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7978-120">Requirements</span></span>  
 <span data-ttu-id="b7978-121">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7978-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7978-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7978-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7978-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7978-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7978-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7978-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7978-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7978-125">See also</span></span>

- [<span data-ttu-id="b7978-126">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7978-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b7978-127">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7978-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="b7978-128">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="b7978-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="b7978-129">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="b7978-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
