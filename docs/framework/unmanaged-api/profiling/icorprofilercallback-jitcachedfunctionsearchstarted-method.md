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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598015"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="ea153-102">ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ea153-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="ea153-103">Oznámí profileru, pro funkci, která se zkompilovala pomocí dříve Native Image Generator (NGen.exe) bylo zahájeno hledání.</span><span class="sxs-lookup"><span data-stu-id="ea153-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea153-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea153-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea153-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea153-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ea153-106">[in] ID funkce, pro které se provádí vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="ea153-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="ea153-107">[out] `true` pokud prováděcí modul by měl používat v mezipaměti verzi funkci (je-li k dispozici). v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="ea153-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="ea153-108">Pokud je hodnota `false`, provádění modulu JIT zkompiluje funkci namísto použití verzi, která není kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="ea153-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea153-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea153-109">Remarks</span></span>  
 <span data-ttu-id="ea153-110">V rozhraní .NET Framework verze 2.0 `JITCachedFunctionSearchStarted` a [icorprofilercallback::jitcachedfunctionsearchfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) zpětná volání, nebude možné zavést pro všechny funkce v běžných bitových kopií technologie NGen.</span><span class="sxs-lookup"><span data-stu-id="ea153-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="ea153-111">Pouze obrázků NGen optimalizovaná pro profil, který vygeneruje zpětná volání pro všechny funkce v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="ea153-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="ea153-112">Ale z důvodu další režie profileru by měl požádat o profileru optimalizované Image NGen pouze v případě, že to chce využít tato zpětná volání k vynucení funkce kompilované just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="ea153-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="ea153-113">Profiler by jinak použijte opožděné strategie pro shromažďování informací funkce.</span><span class="sxs-lookup"><span data-stu-id="ea153-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="ea153-114">Profilovací programy musí podporovat případy, kdy více vláken profilované aplikace jsou volání stejné metody současně.</span><span class="sxs-lookup"><span data-stu-id="ea153-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="ea153-115">Například, vlákna A zavolá `JITCachedFunctionSearchStarted` a profiler odpovídá nastavením *pbUseCachedFunction*na FALSE, pokud chcete vynutit kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="ea153-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="ea153-116">Vlákna A poté zavolá [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) a [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="ea153-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="ea153-117">Nyní vlákna volání B `JITCachedFunctionSearchStarted` pro stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="ea153-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="ea153-118">I v případě, že profiler je uvedeno podat JIT-kompilovat funkci, profiler obdrží druhý zpětné volání, protože vlákno B odesílá zpětné volání před profiler reagoval na vlákno A volání `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="ea153-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="ea153-119">Pořadí, ve kterém vlákna volání závisí na plánování vláken.</span><span class="sxs-lookup"><span data-stu-id="ea153-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="ea153-120">Když profiler obdrží duplicitní zpětná volání, je nutné nastavit hodnotu odkazuje `pbUseCachedFunction` na stejnou hodnotu pro duplicitní zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="ea153-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="ea153-121">To znamená, když `JITCachedFunctionSearchStarted` je se stejným názvem více než jednou `functionId` hodnotu, profiler musí odpovědět, stejné pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="ea153-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea153-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea153-122">Requirements</span></span>  
 <span data-ttu-id="ea153-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea153-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea153-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea153-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea153-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea153-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea153-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea153-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea153-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea153-127">See also</span></span>

- [<span data-ttu-id="ea153-128">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea153-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
