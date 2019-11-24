---
title: ICorProfilerInfo4::RequestRevert – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444834"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="a5de2-102">ICorProfilerInfo4::RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="a5de2-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="a5de2-103">Reverts all instances of the specified functions to their original versions.</span><span class="sxs-lookup"><span data-stu-id="a5de2-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5de2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5de2-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5de2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5de2-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="a5de2-106">[in] The number of functions to revert.</span><span class="sxs-lookup"><span data-stu-id="a5de2-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="a5de2-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span><span class="sxs-lookup"><span data-stu-id="a5de2-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="a5de2-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span><span class="sxs-lookup"><span data-stu-id="a5de2-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="a5de2-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span><span class="sxs-lookup"><span data-stu-id="a5de2-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="a5de2-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="a5de2-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5de2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a5de2-111">Return Value</span></span>  
 <span data-ttu-id="a5de2-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span><span class="sxs-lookup"><span data-stu-id="a5de2-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5de2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5de2-113">HRESULT</span></span>|<span data-ttu-id="a5de2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a5de2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5de2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5de2-115">S_OK</span></span>|<span data-ttu-id="a5de2-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span><span class="sxs-lookup"><span data-stu-id="a5de2-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="a5de2-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="a5de2-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="a5de2-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span><span class="sxs-lookup"><span data-stu-id="a5de2-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="a5de2-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="a5de2-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="a5de2-120">JIT recompilation has not been enabled.</span><span class="sxs-lookup"><span data-stu-id="a5de2-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="a5de2-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span><span class="sxs-lookup"><span data-stu-id="a5de2-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="a5de2-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a5de2-122">E_INVALIDARG</span></span>|<span data-ttu-id="a5de2-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span><span class="sxs-lookup"><span data-stu-id="a5de2-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="a5de2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a5de2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a5de2-125">The CLR was unable to complete the request because it ran out of memory.</span><span class="sxs-lookup"><span data-stu-id="a5de2-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="a5de2-126">Status HRESULTS</span><span class="sxs-lookup"><span data-stu-id="a5de2-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="a5de2-127">Status array HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5de2-127">Status array HRESULT</span></span>|<span data-ttu-id="a5de2-128">Popis</span><span class="sxs-lookup"><span data-stu-id="a5de2-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="a5de2-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5de2-129">S_OK</span></span>|<span data-ttu-id="a5de2-130">The corresponding function was successfully reverted.</span><span class="sxs-lookup"><span data-stu-id="a5de2-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="a5de2-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a5de2-131">E_INVALIDARG</span></span>|<span data-ttu-id="a5de2-132">The `moduleID` or `methodDef` parameter is `NULL`.</span><span class="sxs-lookup"><span data-stu-id="a5de2-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="a5de2-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="a5de2-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="a5de2-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span><span class="sxs-lookup"><span data-stu-id="a5de2-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="a5de2-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="a5de2-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="a5de2-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="a5de2-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="a5de2-137">Therefore, it is not supported by this method.</span><span class="sxs-lookup"><span data-stu-id="a5de2-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="a5de2-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="a5de2-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="a5de2-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span><span class="sxs-lookup"><span data-stu-id="a5de2-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="a5de2-140">Either the recompilation was never requested or the function was already reverted.</span><span class="sxs-lookup"><span data-stu-id="a5de2-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="a5de2-141">Ostatní</span><span class="sxs-lookup"><span data-stu-id="a5de2-141">Other</span></span>|<span data-ttu-id="a5de2-142">The operating system returned a failure outside the control of the CLR.</span><span class="sxs-lookup"><span data-stu-id="a5de2-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="a5de2-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span><span class="sxs-lookup"><span data-stu-id="a5de2-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5de2-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5de2-144">Remarks</span></span>  
 <span data-ttu-id="a5de2-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span><span class="sxs-lookup"><span data-stu-id="a5de2-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="a5de2-146">If a function is already running, it will finish executing the version that is running.</span><span class="sxs-lookup"><span data-stu-id="a5de2-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5de2-147">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5de2-147">Requirements</span></span>  
 <span data-ttu-id="a5de2-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5de2-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5de2-149">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5de2-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5de2-150">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5de2-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5de2-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5de2-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5de2-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5de2-152">See also</span></span>

- [<span data-ttu-id="a5de2-153">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5de2-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a5de2-154">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a5de2-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a5de2-155">Profilace</span><span class="sxs-lookup"><span data-stu-id="a5de2-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
