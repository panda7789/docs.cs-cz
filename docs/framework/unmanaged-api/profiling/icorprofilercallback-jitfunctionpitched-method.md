---
title: ICorProfilerCallback::JITFunctionPitched – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 9bb3934be4a2f4de4a3a235a00522c801331e1eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448427"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="01d53-102">ICorProfilerCallback::JITFunctionPitched – metoda</span><span class="sxs-lookup"><span data-stu-id="01d53-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="01d53-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span><span class="sxs-lookup"><span data-stu-id="01d53-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01d53-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01d53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01d53-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="01d53-106">[in] The ID of the function that was removed.</span><span class="sxs-lookup"><span data-stu-id="01d53-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01d53-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01d53-107">Remarks</span></span>  
 <span data-ttu-id="01d53-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span><span class="sxs-lookup"><span data-stu-id="01d53-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="01d53-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span><span class="sxs-lookup"><span data-stu-id="01d53-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="01d53-110">The value of `functionId` is not valid until the function is recompiled.</span><span class="sxs-lookup"><span data-stu-id="01d53-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="01d53-111">When the function is recompiled, the same `functionId` value will be used.</span><span class="sxs-lookup"><span data-stu-id="01d53-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d53-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01d53-112">Requirements</span></span>  
 <span data-ttu-id="01d53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01d53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d53-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01d53-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01d53-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01d53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01d53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d53-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d53-117">See also</span></span>

- [<span data-ttu-id="01d53-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01d53-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
