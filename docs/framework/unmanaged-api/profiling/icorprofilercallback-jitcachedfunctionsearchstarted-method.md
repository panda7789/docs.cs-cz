---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09fcdc67dc730b59b76a2da9f6ccea04800e20c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="cfa89-102">ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="cfa89-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="cfa89-103">Aby bylo zahájeno hledání pro funkce, který byl kompilován s použitím dříve generátor (NGen.exe) upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="cfa89-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfa89-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfa89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfa89-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cfa89-106">[v] ID funkce, pro které se provádí vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="cfa89-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="cfa89-107">[out] `true` jestli modul provádění by neměl používat v mezipaměti verze funkce (Pokud je k dispozici); jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="cfa89-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="cfa89-108">Pokud je hodnota `false`, provádění modul JIT zkompiluje funkce místo použití na verzi, která není kompilována.</span><span class="sxs-lookup"><span data-stu-id="cfa89-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfa89-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfa89-109">Remarks</span></span>  
 <span data-ttu-id="cfa89-110">V rozhraní .NET Framework verze 2.0 `JITCachedFunctionSearchStarted` a [icorprofilercallback::jitcachedfunctionsearchfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) zpětná volání nebude možné vytvořit pro všechny funkce v pravidelných NGen bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="cfa89-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="cfa89-111">Pouze NGen obrázky optimalizované pro profil vygeneruje zpětných volání pro všechny funkce v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="cfa89-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="cfa89-112">Však z důvodu další režie profileru měli požádat o optimalizované profileru obrazy NGen pouze v případě, že má v úmyslu použít tyto zpětná volání, které vynutí funkce, která má být kompilované v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="cfa89-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="cfa89-113">Profileru, jinak hodnota by měla použít opožděné strategie pro shromažďování informací funkce.</span><span class="sxs-lookup"><span data-stu-id="cfa89-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="cfa89-114">Profilery musí podporovat případy, kdy několik vláken PROFILOVANÉHO aplikace jsou volání stejnou metodu současně.</span><span class="sxs-lookup"><span data-stu-id="cfa89-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="cfa89-115">Například přístup z více vláken A volá `JITCachedFunctionSearchStarted` a profileru odpovídá nastavením *pbUseCachedFunction*na hodnotu FALSE, chcete-li vynutit JIT – kompilace.</span><span class="sxs-lookup"><span data-stu-id="cfa89-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="cfa89-116">Přístup z více vláken potom volá [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) a [icorprofilercallback::jitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfa89-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="cfa89-117">Nyní vláken B volání `JITCachedFunctionSearchStarted` pro stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="cfa89-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="cfa89-118">I když profileru má uvádí svůj záměr JIT – kompilace funkce, profileru obdrží druhý zpětného volání, protože vlákno B odesílá zpětné volání, než profileru reagoval na vlákno na volání `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="cfa89-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="cfa89-119">Pořadí, ve kterém vláken volání závisí na tom, jak jsou naplánovány vláken.</span><span class="sxs-lookup"><span data-stu-id="cfa89-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="cfa89-120">Když profileru obdrží duplicitní zpětná volání, je nutné nastavit hodnotu odkazuje `pbUseCachedFunction` na stejnou hodnotu pro všechny duplicitní zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="cfa89-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="cfa89-121">To znamená, že pokud `JITCachedFunctionSearchStarted` je volat vícekrát, se stejným `functionId` hodnotu, profileru musí odpovědět, stejné pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="cfa89-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa89-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfa89-122">Requirements</span></span>  
 <span data-ttu-id="cfa89-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa89-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa89-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfa89-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfa89-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfa89-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfa89-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa89-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa89-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfa89-127">See Also</span></span>  
 [<span data-ttu-id="cfa89-128">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfa89-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
