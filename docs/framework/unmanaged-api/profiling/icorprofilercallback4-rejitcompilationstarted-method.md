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
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430191"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="24e9f-102">ICorProfilerCallback4::ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="24e9f-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="24e9f-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span><span class="sxs-lookup"><span data-stu-id="24e9f-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24e9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24e9f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="24e9f-106">[in] The ID of the function that the JIT compiler has started to recompile.</span><span class="sxs-lookup"><span data-stu-id="24e9f-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="24e9f-107">[in] The recompilation ID of the new version of the function.</span><span class="sxs-lookup"><span data-stu-id="24e9f-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="24e9f-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="24e9f-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="24e9f-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span><span class="sxs-lookup"><span data-stu-id="24e9f-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24e9f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24e9f-110">Remarks</span></span>  
 <span data-ttu-id="24e9f-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span><span class="sxs-lookup"><span data-stu-id="24e9f-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="24e9f-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span><span class="sxs-lookup"><span data-stu-id="24e9f-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="24e9f-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span><span class="sxs-lookup"><span data-stu-id="24e9f-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="24e9f-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span><span class="sxs-lookup"><span data-stu-id="24e9f-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="24e9f-115">In this scenario, the first recompilation of method A is halted.</span><span class="sxs-lookup"><span data-stu-id="24e9f-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="24e9f-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span><span class="sxs-lookup"><span data-stu-id="24e9f-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="24e9f-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span><span class="sxs-lookup"><span data-stu-id="24e9f-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="24e9f-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span><span class="sxs-lookup"><span data-stu-id="24e9f-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="24e9f-119">However, in this case, the function ID is valid.</span><span class="sxs-lookup"><span data-stu-id="24e9f-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e9f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24e9f-120">Requirements</span></span>  
 <span data-ttu-id="24e9f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24e9f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e9f-122">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24e9f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24e9f-123">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24e9f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24e9f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e9f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e9f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24e9f-125">See also</span></span>

- [<span data-ttu-id="24e9f-126">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24e9f-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="24e9f-127">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24e9f-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="24e9f-128">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="24e9f-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="24e9f-129">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="24e9f-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
