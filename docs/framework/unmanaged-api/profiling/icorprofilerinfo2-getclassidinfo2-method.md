---
title: ICorProfilerInfo2::GetClassIDInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433439"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="4e275-102">ICorProfilerInfo2::GetClassIDInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4e275-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="4e275-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span><span class="sxs-lookup"><span data-stu-id="4e275-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e275-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e275-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e275-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e275-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4e275-106">[in] The ID of the class for which information will be retrieved.</span><span class="sxs-lookup"><span data-stu-id="4e275-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="4e275-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span><span class="sxs-lookup"><span data-stu-id="4e275-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="4e275-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span><span class="sxs-lookup"><span data-stu-id="4e275-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="4e275-109">[out] Pointer to the ID of the parent class.</span><span class="sxs-lookup"><span data-stu-id="4e275-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="4e275-110">[in] The size of the `typeArgs` array.</span><span class="sxs-lookup"><span data-stu-id="4e275-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="4e275-111">[out] Pointer to the total number of available elements.</span><span class="sxs-lookup"><span data-stu-id="4e275-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="4e275-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span><span class="sxs-lookup"><span data-stu-id="4e275-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="4e275-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span><span class="sxs-lookup"><span data-stu-id="4e275-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e275-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e275-114">Remarks</span></span>  
 <span data-ttu-id="4e275-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span><span class="sxs-lookup"><span data-stu-id="4e275-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="4e275-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span><span class="sxs-lookup"><span data-stu-id="4e275-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="4e275-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span><span class="sxs-lookup"><span data-stu-id="4e275-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="4e275-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span><span class="sxs-lookup"><span data-stu-id="4e275-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="4e275-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span><span class="sxs-lookup"><span data-stu-id="4e275-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="4e275-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="4e275-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="4e275-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="4e275-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4e275-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="4e275-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e275-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e275-123">Requirements</span></span>  
 <span data-ttu-id="4e275-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e275-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e275-125">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e275-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e275-126">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e275-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e275-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e275-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e275-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e275-128">See also</span></span>

- [<span data-ttu-id="4e275-129">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e275-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4e275-130">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e275-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="4e275-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4e275-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4e275-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="4e275-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
