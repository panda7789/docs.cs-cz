---
title: ICorProfilerInfo2::GetCodeInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 5149e3fab023de42d03673ec5d3e5ae888a9ed5a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433289"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="b25b4-102">ICorProfilerInfo2::GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b25b4-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="b25b4-103">Gets the extents of native code associated with the specified `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="b25b4-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b25b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b25b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b25b4-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="b25b4-106">[in] The ID of the function with which the native code is associated.</span><span class="sxs-lookup"><span data-stu-id="b25b4-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="b25b4-107">[in] The size of the `codeInfos` array.</span><span class="sxs-lookup"><span data-stu-id="b25b4-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="b25b4-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span><span class="sxs-lookup"><span data-stu-id="b25b4-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="b25b4-109">[out] A caller-provided buffer.</span><span class="sxs-lookup"><span data-stu-id="b25b4-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="b25b4-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span><span class="sxs-lookup"><span data-stu-id="b25b4-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25b4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b25b4-111">Remarks</span></span>  
 <span data-ttu-id="b25b4-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span><span class="sxs-lookup"><span data-stu-id="b25b4-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="b25b4-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span><span class="sxs-lookup"><span data-stu-id="b25b4-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="b25b4-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span><span class="sxs-lookup"><span data-stu-id="b25b4-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="b25b4-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="b25b4-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="b25b4-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="b25b4-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b25b4-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="b25b4-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25b4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b25b4-118">Requirements</span></span>  
 <span data-ttu-id="b25b4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b25b4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25b4-120">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b25b4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b25b4-121">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b25b4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b25b4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25b4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25b4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b25b4-123">See also</span></span>

- [<span data-ttu-id="b25b4-124">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="b25b4-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="b25b4-125">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b25b4-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="b25b4-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b25b4-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b25b4-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="b25b4-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
