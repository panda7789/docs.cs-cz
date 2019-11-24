---
title: ICorProfilerInfo::GetModuleInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438890"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="2ece9-102">ICorProfilerInfo::GetModuleInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2ece9-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="2ece9-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span><span class="sxs-lookup"><span data-stu-id="2ece9-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ece9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ece9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ece9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ece9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2ece9-106">[in] The ID of the module for which information will be retrieved.</span><span class="sxs-lookup"><span data-stu-id="2ece9-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="2ece9-107">[out] The base address at which the module is loaded.</span><span class="sxs-lookup"><span data-stu-id="2ece9-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2ece9-108">[in] The length, in characters, of the `szName` return buffer.</span><span class="sxs-lookup"><span data-stu-id="2ece9-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2ece9-109">[out] A pointer to the total character length of the module's file name that is returned.</span><span class="sxs-lookup"><span data-stu-id="2ece9-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="2ece9-110">[out] A caller-provided wide character buffer.</span><span class="sxs-lookup"><span data-stu-id="2ece9-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="2ece9-111">When the method returns, this buffer contains the file name of the module.</span><span class="sxs-lookup"><span data-stu-id="2ece9-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="2ece9-112">[out] A pointer to the ID of the module's parent assembly.</span><span class="sxs-lookup"><span data-stu-id="2ece9-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ece9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ece9-113">Remarks</span></span>  
 <span data-ttu-id="2ece9-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="2ece9-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="2ece9-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="2ece9-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="2ece9-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span><span class="sxs-lookup"><span data-stu-id="2ece9-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="2ece9-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span><span class="sxs-lookup"><span data-stu-id="2ece9-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="2ece9-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span><span class="sxs-lookup"><span data-stu-id="2ece9-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="2ece9-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="2ece9-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2ece9-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span><span class="sxs-lookup"><span data-stu-id="2ece9-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ece9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ece9-121">Requirements</span></span>  
 <span data-ttu-id="2ece9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ece9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ece9-123">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ece9-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ece9-124">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ece9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ece9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ece9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ece9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ece9-126">See also</span></span>

- [<span data-ttu-id="2ece9-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ece9-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2ece9-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2ece9-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2ece9-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="2ece9-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="2ece9-130">GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2ece9-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
