---
title: FunctionEnter2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440858"
---
# <a name="functionenter2-function"></a><span data-ttu-id="04378-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="04378-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="04378-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span><span class="sxs-lookup"><span data-stu-id="04378-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="04378-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="04378-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04378-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04378-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04378-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="04378-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="04378-107">[in] The identifier of the function to which control is passed.</span><span class="sxs-lookup"><span data-stu-id="04378-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="04378-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="04378-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="04378-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span><span class="sxs-lookup"><span data-stu-id="04378-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="04378-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="04378-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="04378-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span><span class="sxs-lookup"><span data-stu-id="04378-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="04378-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span><span class="sxs-lookup"><span data-stu-id="04378-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="04378-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span><span class="sxs-lookup"><span data-stu-id="04378-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04378-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04378-114">Remarks</span></span>  
 <span data-ttu-id="04378-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span><span class="sxs-lookup"><span data-stu-id="04378-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="04378-116">The `FunctionEnter2` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="04378-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="04378-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="04378-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="04378-118">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="04378-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="04378-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="04378-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="04378-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="04378-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="04378-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="04378-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="04378-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="04378-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="04378-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span><span class="sxs-lookup"><span data-stu-id="04378-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="04378-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span><span class="sxs-lookup"><span data-stu-id="04378-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04378-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04378-125">Requirements</span></span>  
 <span data-ttu-id="04378-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04378-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04378-127">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="04378-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="04378-128">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04378-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04378-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04378-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04378-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04378-130">See also</span></span>

- [<span data-ttu-id="04378-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="04378-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="04378-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="04378-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="04378-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="04378-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="04378-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="04378-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
