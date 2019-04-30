---
title: ICorProfilerCallback::JITCompilationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b75eebd8d9bf439a0317521a61c06ece3745be0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787917"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="ce2a8-102">ICorProfilerCallback::JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ce2a8-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="ce2a8-103">Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce2a8-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce2a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce2a8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ce2a8-106">[in] ID funkce, pro který se spouští kompilace.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="ce2a8-107">[in] Hodnotu, která k profileru, zda blokování bude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="ce2a8-108">Hodnota je `true` Pokud blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="ce2a8-109">I když hodnota `true` nepoškodí modul runtime, je zkosení výsledků profilace.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2a8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce2a8-110">Remarks</span></span>  
 <span data-ttu-id="ce2a8-111">Je možné přijímat více než jednu dvojici `JITCompilationStarted` a [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) volá pro každou funkci kvůli způsobu, jakým modul runtime konstruktor třídy obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="ce2a8-112">Například modul runtime spustí metodě JIT-kompilovat A, ale třída konstruktor třídy B musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="ce2a8-113">Proto se modul runtime JIT zkompiluje konstruktor třídy B a spustí ho.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="ce2a8-114">Je spuštěn konstruktoru, provede volání do metody A, což způsobí, že metoda A být znovu sestaveny JIT.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="ce2a8-115">V tomto scénáři je první JIT kompilaci metody A zastaveno.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="ce2a8-116">Ale i pokusy o metoda JIT-kompilovat A označené s událostmi kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="ce2a8-117">Pokud profileru kód Microsoft intermediate language (MSIL) pro metodu A nahraďte voláním [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metodu, musíte udělat, tak pro obě `JITCompilationStarted` události, ale může používat stejný blok MSIL u obou.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="ce2a8-118">Profilovací programy musí podporovat posloupnost zpětných volání JIT v případech, kde dva vláken současně, aby zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="ce2a8-119">Například, vlákna A zavolá `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="ce2a8-120">Nicméně před volání vlákna A `JITCompilationFinished`, vlákno B vyvolá [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z vlákna A `JITCompilationStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="ce2a8-121">Může se zdát, že ID funkce by neměl být ještě platný protože volání `JITCompilationFinished` nebyl dosud nebylo přijato pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="ce2a8-122">V případě tohoto typu, je však platné ID funkce.</span><span class="sxs-lookup"><span data-stu-id="ce2a8-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2a8-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce2a8-123">Requirements</span></span>  
 <span data-ttu-id="ce2a8-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce2a8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2a8-125">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce2a8-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce2a8-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce2a8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce2a8-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2a8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2a8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce2a8-128">See also</span></span>

- [<span data-ttu-id="ce2a8-129">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce2a8-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ce2a8-130">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ce2a8-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
