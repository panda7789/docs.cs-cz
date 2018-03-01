---
title: "ICorProfilerCallback4::ReJITCompilationStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 903db06089f7c68843b503c94483087ff9fce636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="6aea9-102">ICorProfilerCallback4::ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="6aea9-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="6aea9-103">Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="6aea9-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aea9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6aea9-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6aea9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6aea9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6aea9-106">[v] ID funkce, která JIT kompilátoru bylo zahájeno její kompilace.</span><span class="sxs-lookup"><span data-stu-id="6aea9-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="6aea9-107">[v] ID rekompilace nové verze funkce.</span><span class="sxs-lookup"><span data-stu-id="6aea9-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="6aea9-108">[v] `true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6aea9-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="6aea9-109">Hodnota `true` nepříznivý vliv modul runtime, ale může ovlivnit profilování výsledky.</span><span class="sxs-lookup"><span data-stu-id="6aea9-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aea9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6aea9-110">Remarks</span></span>  
 <span data-ttu-id="6aea9-111">Je možné získat více než jednu dvojici `ReJITCompilationStarted` a [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda volá pro jednotlivé funkce z důvodu způsob, jakým modul runtime konstruktory třídu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6aea9-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="6aea9-112">Například modul runtime začne znovu zkompiluje metoda A, ale konstruktoru třídy pro třídy B musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="6aea9-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="6aea9-113">Modul runtime proto znovu zkompiluje v konstruktoru pro třídy B a ho spouští.</span><span class="sxs-lookup"><span data-stu-id="6aea9-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="6aea9-114">Je spuštěn v konstruktoru, provede volání do metody A, což způsobí, že metoda A k akci zopakovat.</span><span class="sxs-lookup"><span data-stu-id="6aea9-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="6aea9-115">V tomto scénáři je první rekompilace metody A zastavit.</span><span class="sxs-lookup"><span data-stu-id="6aea9-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="6aea9-116">Však obě pokusí znovu zkompiluje metoda A jsou hlášené s rekompilace JIT – události.</span><span class="sxs-lookup"><span data-stu-id="6aea9-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="6aea9-117">Profilery musí podporovat posloupnost zpětných volání rekompilace JIT v případech, kde jsou dva vláken současně provádění zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="6aea9-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="6aea9-118">Například přístup z více vláken A volá `ReJITCompilationStarted`; však před volání vláken A [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B volání [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID – funkce z `ReJITCompilationStarted` zpětné volání pro přístup z více vláken A. Může se zdát, že funkce ID nesmí být ještě platný protože volání [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) kdyby ještě přijatý nástrojem profileru.</span><span class="sxs-lookup"><span data-stu-id="6aea9-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="6aea9-119">V takovém případě Identifikátor funkce je však platný.</span><span class="sxs-lookup"><span data-stu-id="6aea9-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aea9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6aea9-120">Requirements</span></span>  
 <span data-ttu-id="6aea9-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aea9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aea9-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6aea9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6aea9-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aea9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aea9-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aea9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aea9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6aea9-125">See Also</span></span>  
 [<span data-ttu-id="6aea9-126">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6aea9-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6aea9-127">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6aea9-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="6aea9-128">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6aea9-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="6aea9-129">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6aea9-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
