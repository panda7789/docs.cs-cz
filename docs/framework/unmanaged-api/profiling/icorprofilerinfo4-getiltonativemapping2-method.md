---
title: ICorProfilerInfo4::GetILToNativeMapping2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442921"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="b94ba-102">ICorProfilerInfo4::GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b94ba-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="b94ba-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span><span class="sxs-lookup"><span data-stu-id="b94ba-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b94ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b94ba-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b94ba-106">[in] The ID of the function that contains the code.</span><span class="sxs-lookup"><span data-stu-id="b94ba-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="b94ba-107">[in] The identity of the JIT-recompiled function.</span><span class="sxs-lookup"><span data-stu-id="b94ba-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="b94ba-108">The identity must be zero in the .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b94ba-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="b94ba-109">[in] The maximum size of the `map` array.</span><span class="sxs-lookup"><span data-stu-id="b94ba-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="b94ba-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span><span class="sxs-lookup"><span data-stu-id="b94ba-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="b94ba-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span><span class="sxs-lookup"><span data-stu-id="b94ba-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="b94ba-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="b94ba-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b94ba-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b94ba-113">Remarks</span></span>  
 <span data-ttu-id="b94ba-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span><span class="sxs-lookup"><span data-stu-id="b94ba-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b94ba-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span><span class="sxs-lookup"><span data-stu-id="b94ba-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="b94ba-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b94ba-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="b94ba-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="b94ba-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b94ba-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="b94ba-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="b94ba-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="b94ba-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b94ba-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span><span class="sxs-lookup"><span data-stu-id="b94ba-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="b94ba-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span><span class="sxs-lookup"><span data-stu-id="b94ba-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="b94ba-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="b94ba-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b94ba-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span><span class="sxs-lookup"><span data-stu-id="b94ba-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b94ba-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b94ba-124">Requirements</span></span>  
 <span data-ttu-id="b94ba-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b94ba-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b94ba-126">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b94ba-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b94ba-127">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b94ba-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b94ba-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b94ba-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94ba-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b94ba-129">See also</span></span>

- [<span data-ttu-id="b94ba-130">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="b94ba-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="b94ba-131">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94ba-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b94ba-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b94ba-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b94ba-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="b94ba-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
