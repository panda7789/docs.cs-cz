---
title: FunctionLeave2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446012"
---
# <a name="functionleave2-function"></a><span data-ttu-id="a4e2b-102">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a4e2b-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="a4e2b-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4e2b-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4e2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4e2b-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="a4e2b-106">[in] The identifier of the function that is returning.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="a4e2b-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="a4e2b-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="a4e2b-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="a4e2b-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="a4e2b-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="a4e2b-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4e2b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4e2b-113">Remarks</span></span>  
 <span data-ttu-id="a4e2b-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="a4e2b-115">The `FunctionLeave2` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="a4e2b-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a4e2b-117">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a4e2b-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="a4e2b-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a4e2b-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a4e2b-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a4e2b-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a4e2b-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="a4e2b-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span><span class="sxs-lookup"><span data-stu-id="a4e2b-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e2b-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4e2b-124">Requirements</span></span>  
 <span data-ttu-id="a4e2b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e2b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e2b-126">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a4e2b-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a4e2b-127">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4e2b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4e2b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e2b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e2b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4e2b-129">See also</span></span>

- [<span data-ttu-id="a4e2b-130">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a4e2b-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="a4e2b-131">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a4e2b-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="a4e2b-132">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a4e2b-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a4e2b-133">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a4e2b-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
