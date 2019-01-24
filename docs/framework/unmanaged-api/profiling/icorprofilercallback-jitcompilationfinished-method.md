---
title: ICorProfilerCallback::JITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530749"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="76828-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="76828-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="76828-103">Oznámí profileru, že byla dokončena kompilátor just-in-time (JIT) kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="76828-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76828-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76828-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="76828-106">[in] ID funkce, která byla zkompilována.</span><span class="sxs-lookup"><span data-stu-id="76828-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="76828-107">[in] Hodnota označující, zda kompilace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="76828-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="76828-108">[in] Hodnotu, která k profileru, zda blokování bude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="76828-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="76828-109">Hodnota je `true` Pokud blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="76828-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="76828-110">I když hodnota `true` nepoškodí modul runtime, je zkosení výsledků profilace.</span><span class="sxs-lookup"><span data-stu-id="76828-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76828-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76828-111">Requirements</span></span>  
 <span data-ttu-id="76828-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76828-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76828-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76828-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76828-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76828-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76828-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76828-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76828-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76828-116">See also</span></span>
- [<span data-ttu-id="76828-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76828-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="76828-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="76828-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
