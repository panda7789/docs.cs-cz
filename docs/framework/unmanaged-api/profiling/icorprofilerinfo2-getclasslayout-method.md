---
title: ICorProfilerInfo2::GetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433389"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="0240b-102">ICorProfilerInfo2::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="0240b-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="0240b-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span><span class="sxs-lookup"><span data-stu-id="0240b-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="0240b-104">That is, this method gets the offsets of the class's fields.</span><span class="sxs-lookup"><span data-stu-id="0240b-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0240b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0240b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0240b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0240b-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="0240b-107">[in] The ID of the class for which the layout will be retrieved.</span><span class="sxs-lookup"><span data-stu-id="0240b-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="0240b-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span><span class="sxs-lookup"><span data-stu-id="0240b-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="0240b-109">[in] The size of the `rFieldOffset` array.</span><span class="sxs-lookup"><span data-stu-id="0240b-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="0240b-110">[out] A pointer to the total number of available elements.</span><span class="sxs-lookup"><span data-stu-id="0240b-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="0240b-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span><span class="sxs-lookup"><span data-stu-id="0240b-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="0240b-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span><span class="sxs-lookup"><span data-stu-id="0240b-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0240b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0240b-113">Remarks</span></span>  
 <span data-ttu-id="0240b-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span><span class="sxs-lookup"><span data-stu-id="0240b-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="0240b-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span><span class="sxs-lookup"><span data-stu-id="0240b-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="0240b-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="0240b-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="0240b-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span><span class="sxs-lookup"><span data-stu-id="0240b-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="0240b-118">`GetClassLayout` will also fail when called with an array class.</span><span class="sxs-lookup"><span data-stu-id="0240b-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="0240b-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span><span class="sxs-lookup"><span data-stu-id="0240b-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="0240b-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span><span class="sxs-lookup"><span data-stu-id="0240b-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="0240b-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span><span class="sxs-lookup"><span data-stu-id="0240b-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="0240b-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="0240b-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0240b-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span><span class="sxs-lookup"><span data-stu-id="0240b-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0240b-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0240b-124">Requirements</span></span>  
 <span data-ttu-id="0240b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0240b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0240b-126">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0240b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0240b-127">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0240b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0240b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0240b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0240b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0240b-129">See also</span></span>

- [<span data-ttu-id="0240b-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0240b-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0240b-131">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0240b-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="0240b-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0240b-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0240b-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="0240b-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
