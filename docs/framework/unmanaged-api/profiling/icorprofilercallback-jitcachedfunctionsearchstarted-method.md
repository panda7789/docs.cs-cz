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
ms.openlocfilehash: 964ea11b8e8c8f494066249f7da2057970d7e8f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866257"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="1c691-102">ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="1c691-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="1c691-103">Upozorní profileru, že pro funkci, která byla dříve kompilována pomocí generátoru nativních imagí (NGen. exe), bylo spuštěno vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="1c691-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c691-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c691-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c691-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c691-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="1c691-106">\[in] ID funkce, pro kterou se provádí hledání.</span><span class="sxs-lookup"><span data-stu-id="1c691-106">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="1c691-107">\[] `true`, pokud spouštěcí modul by měl používat verzi funkce uložené v mezipaměti (Pokud je k dispozici); jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="1c691-107">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="1c691-108">Pokud je hodnota `false`, prováděcí modul JIT – zkompiluje funkci namísto použití verze, která není kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="1c691-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c691-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c691-109">Remarks</span></span>  
 <span data-ttu-id="1c691-110">V .NET Framework verze 2,0 nebudou zpětná volání metod `JITCachedFunctionSearchStarted` a [ICorProfilerCallback:: jitcachedfunctionsearchfinished –](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) pro všechny funkce v normálních bitových kopiích Ngen provedeny.</span><span class="sxs-lookup"><span data-stu-id="1c691-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="1c691-111">Zpětná volání pro všechny funkce v imagi budou generovat pouze image NGen optimalizované pro profil.</span><span class="sxs-lookup"><span data-stu-id="1c691-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="1c691-112">V důsledku dodatečné režie by měl Profiler vyžádat image NGen optimalizované profilerem jenom v případě, že má v úmyslu použít tato zpětná volání k vynucení funkce JIT just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="1c691-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="1c691-113">V opačném případě by Profiler měl používat opožděnou strategii pro shromažďování informací o funkcích.</span><span class="sxs-lookup"><span data-stu-id="1c691-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="1c691-114">Profilery musí podporovat případy, kdy více vláken profilované aplikace volá stejnou metodu současně.</span><span class="sxs-lookup"><span data-stu-id="1c691-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="1c691-115">Například vlákno A volá `JITCachedFunctionSearchStarted` a Profiler odpoví nastavením *pbUseCachedFunction*na hodnotu false pro vynucení kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="1c691-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="1c691-116">Vlákno A potom zavolá [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) a [ICorProfilerCallback:: JITCompilationFinished –](icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c691-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="1c691-117">Nyní vlákno B volá `JITCachedFunctionSearchStarted` pro stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="1c691-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="1c691-118">I když Profiler uvedl svůj úmysl na zkompilování funkce JIT, Profiler obdrží druhé zpětné volání, protože vlákno B odesílá zpětné volání, než Profiler odpoví na volání Thread A na `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="1c691-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="1c691-119">Pořadí, ve kterém vlákna volají, závisí na tom, jak jsou vlákna naplánována.</span><span class="sxs-lookup"><span data-stu-id="1c691-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="1c691-120">Když Profiler obdrží duplicitní zpětná volání, musí nastavit hodnotu, na kterou odkazuje `pbUseCachedFunction`, na stejnou hodnotu pro všechna duplicitní zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="1c691-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="1c691-121">To znamená, že když se `JITCachedFunctionSearchStarted` volá víckrát se stejnou `functionId` hodnotou, musí Profiler kdykoli odpovědět.</span><span class="sxs-lookup"><span data-stu-id="1c691-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c691-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c691-122">Requirements</span></span>  
 <span data-ttu-id="1c691-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c691-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c691-124">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1c691-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c691-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c691-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c691-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c691-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c691-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c691-127">See also</span></span>

- [<span data-ttu-id="1c691-128">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c691-128">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
