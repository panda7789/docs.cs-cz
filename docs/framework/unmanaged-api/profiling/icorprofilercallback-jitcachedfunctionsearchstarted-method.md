---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 5d3fe6691a2d9989de002bad09c2e8f66a094f56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448431"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="c05fe-102">ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c05fe-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="c05fe-103">Upozorní profileru, že pro funkci, která byla dříve kompilována pomocí generátoru nativních imagí (NGen. exe), bylo spuštěno vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c05fe-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c05fe-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c05fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c05fe-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c05fe-106">pro ID funkce, pro kterou se provádí hledání</span><span class="sxs-lookup"><span data-stu-id="c05fe-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="c05fe-107">[out] `true`, zda má spouštěcí modul používat verzi funkce uložené v mezipaměti (Pokud je k dispozici); jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="c05fe-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="c05fe-108">Pokud je hodnota `false`, prováděcí modul JIT – zkompiluje funkci namísto použití verze, která není kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="c05fe-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c05fe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c05fe-109">Remarks</span></span>  
 <span data-ttu-id="c05fe-110">V .NET Framework verze 2,0 nebudou zpětná volání metod `JITCachedFunctionSearchStarted` a [ICorProfilerCallback:: jitcachedfunctionsearchfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) pro všechny funkce v normálních bitových kopiích Ngen provedeny.</span><span class="sxs-lookup"><span data-stu-id="c05fe-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="c05fe-111">Zpětná volání pro všechny funkce v imagi budou generovat pouze image NGen optimalizované pro profil.</span><span class="sxs-lookup"><span data-stu-id="c05fe-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="c05fe-112">V důsledku dodatečné režie by měl Profiler vyžádat image NGen optimalizované profilerem jenom v případě, že má v úmyslu použít tato zpětná volání k vynucení funkce JIT just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c05fe-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="c05fe-113">V opačném případě by Profiler měl používat opožděnou strategii pro shromažďování informací o funkcích.</span><span class="sxs-lookup"><span data-stu-id="c05fe-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="c05fe-114">Profilery musí podporovat případy, kdy více vláken profilované aplikace volá stejnou metodu současně.</span><span class="sxs-lookup"><span data-stu-id="c05fe-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="c05fe-115">Například vlákno A volá `JITCachedFunctionSearchStarted` a Profiler odpoví nastavením *pbUseCachedFunction*na hodnotu false pro vynucení kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="c05fe-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="c05fe-116">Vlákno A potom zavolá [ICorProfilerCallback:: JITCompilationStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) a [ICorProfilerCallback:: JITCompilationFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="c05fe-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="c05fe-117">Nyní vlákno B volá `JITCachedFunctionSearchStarted` pro stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="c05fe-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="c05fe-118">I když Profiler uvedl svůj úmysl na zkompilování funkce JIT, Profiler obdrží druhé zpětné volání, protože vlákno B odesílá zpětné volání, než Profiler odpoví na volání Thread A na `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="c05fe-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="c05fe-119">Pořadí, ve kterém vlákna volají, závisí na tom, jak jsou vlákna naplánována.</span><span class="sxs-lookup"><span data-stu-id="c05fe-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="c05fe-120">Když Profiler obdrží duplicitní zpětná volání, musí nastavit hodnotu, na kterou odkazuje `pbUseCachedFunction`, na stejnou hodnotu pro všechna duplicitní zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="c05fe-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="c05fe-121">To znamená, že když se `JITCachedFunctionSearchStarted` volá víckrát se stejnou `functionId` hodnotou, musí Profiler kdykoli odpovědět.</span><span class="sxs-lookup"><span data-stu-id="c05fe-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05fe-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c05fe-122">Requirements</span></span>  
 <span data-ttu-id="c05fe-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05fe-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05fe-124">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c05fe-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c05fe-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c05fe-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c05fe-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05fe-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05fe-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c05fe-127">See also</span></span>

- [<span data-ttu-id="c05fe-128">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c05fe-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
