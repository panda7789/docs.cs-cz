---
title: ICorProfilerCallback4::ReJITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e5d49e46c6b34c6efca5d6819cb4ca341f010bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524725"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="435b3-102">ICorProfilerCallback4::ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="435b3-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="435b3-103">Oznámí profileru, kompilátor just-in-time (JIT) dokončil rekompilace funkce.</span><span class="sxs-lookup"><span data-stu-id="435b3-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="435b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="435b3-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="435b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="435b3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="435b3-106">[in] ID funkce, která byla znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="435b3-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="435b3-107">[in] Identita funkce překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="435b3-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="435b3-108">[in] Hodnota, která určuje, zda rekompilace JIT byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="435b3-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="435b3-109">[in] `true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="435b3-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="435b3-110">Hodnota `true` nepoškodí modul runtime, ale může mít vliv na výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="435b3-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="435b3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="435b3-111">Requirements</span></span>  
 <span data-ttu-id="435b3-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="435b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="435b3-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="435b3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="435b3-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="435b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="435b3-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="435b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435b3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="435b3-116">See also</span></span>
- [<span data-ttu-id="435b3-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="435b3-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="435b3-118">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="435b3-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="435b3-119">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="435b3-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="435b3-120">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="435b3-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
