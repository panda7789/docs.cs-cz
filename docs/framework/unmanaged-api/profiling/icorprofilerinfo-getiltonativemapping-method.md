---
title: ICorProfilerInfo::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: 8dc551b2b1e29aba371e56eecfd981f16b4b1e3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439033"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="e04b8-102">ICorProfilerInfo::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="e04b8-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="e04b8-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span><span class="sxs-lookup"><span data-stu-id="e04b8-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e04b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e04b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e04b8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e04b8-106">[in] The ID of the function that contains the code.</span><span class="sxs-lookup"><span data-stu-id="e04b8-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="e04b8-107">[in] The maximum size of the `map` array.</span><span class="sxs-lookup"><span data-stu-id="e04b8-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="e04b8-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span><span class="sxs-lookup"><span data-stu-id="e04b8-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="e04b8-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span><span class="sxs-lookup"><span data-stu-id="e04b8-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="e04b8-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="e04b8-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e04b8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e04b8-111">Remarks</span></span>  
 <span data-ttu-id="e04b8-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="e04b8-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="e04b8-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="e04b8-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="e04b8-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span><span class="sxs-lookup"><span data-stu-id="e04b8-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="e04b8-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span><span class="sxs-lookup"><span data-stu-id="e04b8-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="e04b8-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span><span class="sxs-lookup"><span data-stu-id="e04b8-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="e04b8-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="e04b8-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e04b8-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span><span class="sxs-lookup"><span data-stu-id="e04b8-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e04b8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e04b8-119">Requirements</span></span>  
 <span data-ttu-id="e04b8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e04b8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e04b8-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e04b8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e04b8-122">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e04b8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e04b8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e04b8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04b8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e04b8-124">See also</span></span>

- [<span data-ttu-id="e04b8-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e04b8-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e04b8-126">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e04b8-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="e04b8-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e04b8-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e04b8-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="e04b8-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
