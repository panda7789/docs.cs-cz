---
title: ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e7a25fce945504cff0d07f499ae4bb79378e9f3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449701"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="00225-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="00225-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="00225-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="00225-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="00225-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span><span class="sxs-lookup"><span data-stu-id="00225-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00225-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00225-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00225-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00225-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="00225-107">[in] The `FunctionID` of the function that is returning.</span><span class="sxs-lookup"><span data-stu-id="00225-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="00225-108">[in] An opaque handle that represents information about a given stack frame.</span><span class="sxs-lookup"><span data-stu-id="00225-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="00225-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span><span class="sxs-lookup"><span data-stu-id="00225-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="00225-110">[out] An opaque handle that represents generics information about a given stack frame.</span><span class="sxs-lookup"><span data-stu-id="00225-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="00225-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span><span class="sxs-lookup"><span data-stu-id="00225-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00225-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00225-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00225-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00225-113">Requirements</span></span>  
 <span data-ttu-id="00225-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00225-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00225-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00225-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00225-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00225-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00225-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00225-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00225-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00225-118">See also</span></span>

- [<span data-ttu-id="00225-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00225-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="00225-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00225-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="00225-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00225-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="00225-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00225-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="00225-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="00225-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="00225-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="00225-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
