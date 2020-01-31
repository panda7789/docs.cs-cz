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
ms.openlocfilehash: 81d11c87c9bc970dd5b5c9010023610cea7c0e72
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865191"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="f1f1b-102">ICorProfilerCallback4::ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f1f1b-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="f1f1b-103">Upozorní profileru, že kompilátor JIT (just-in-time) začal znovu kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1f1b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1f1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1f1b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f1f1b-106">pro ID funkce, kterou byl kompilátor JIT spuštěn pro rekompilaci.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="f1f1b-107">pro ID překompilace nové verze funkce</span><span class="sxs-lookup"><span data-stu-id="f1f1b-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f1f1b-108">[in] `true` označuje, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="f1f1b-109">Hodnota `true` nepoškozuje modul runtime, ale může ovlivnit výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1f1b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1f1b-110">Remarks</span></span>  
 <span data-ttu-id="f1f1b-111">Je možné získat více než jednu dvojici `ReJITCompilationStarted` a [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md) volání metody pro každou funkci z důvodu způsobu, jakým modul runtime zpracovává konstruktory třídy.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="f1f1b-112">Například modul runtime začíná znovu kompilovat metodu A, ale je nutné spustit konstruktor třídy pro třídu B.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="f1f1b-113">Proto modul runtime znovu zkompiluje konstruktor pro třídu B a spustí jej.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="f1f1b-114">I když je konstruktor spuštěn, provede volání metody A, což způsobí, že metoda A bude znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="f1f1b-115">V tomto scénáři je první opětovná kompilace metody A zastavena.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="f1f1b-116">Oba pokusy o rekompilaci metody A jsou však hlášeny s událostmi opětovné kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="f1f1b-117">Profilery musí podporovat sekvenci zpětných volání rekompilace JIT v případech, kdy dvě vlákna současně provádí zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="f1f1b-118">Například vlákno A volání `ReJITCompilationStarted`; Nicméně před voláním vlákna A [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md)vlákno B volá [ICorProfilerCallback:: ExceptionSearchFunctionEnter –](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z zpětného volání `ReJITCompilationStarted` pro vlákno A. Může se zdát, že ID funkce by ještě nemělo být platné, protože Profiler ještě nepřijal volání [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1f1b-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="f1f1b-119">V tomto případě je však ID funkce platné.</span><span class="sxs-lookup"><span data-stu-id="f1f1b-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1f1b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1f1b-120">Requirements</span></span>  
 <span data-ttu-id="f1f1b-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1f1b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f1b-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f1f1b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1f1b-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f1f1b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1f1b-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f1b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f1b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1f1b-125">See also</span></span>

- [<span data-ttu-id="f1f1b-126">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1f1b-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f1f1b-127">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1f1b-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="f1f1b-128">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f1f1b-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="f1f1b-129">ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f1f1b-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
