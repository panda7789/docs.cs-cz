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
ms.openlocfilehash: 1bbdfa93913b9fdf8aa164c8ca6c35cd33a228df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449917"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="700c6-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="700c6-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="700c6-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span><span class="sxs-lookup"><span data-stu-id="700c6-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="700c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="700c6-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="700c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="700c6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="700c6-106">[in] The ID of the function that was compiled.</span><span class="sxs-lookup"><span data-stu-id="700c6-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="700c6-107">[in] A value indicating whether compilation was successful.</span><span class="sxs-lookup"><span data-stu-id="700c6-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="700c6-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="700c6-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="700c6-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="700c6-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="700c6-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span><span class="sxs-lookup"><span data-stu-id="700c6-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="700c6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="700c6-111">Requirements</span></span>  
 <span data-ttu-id="700c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="700c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="700c6-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="700c6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="700c6-114">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="700c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="700c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="700c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700c6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="700c6-116">See also</span></span>

- [<span data-ttu-id="700c6-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="700c6-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="700c6-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="700c6-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
