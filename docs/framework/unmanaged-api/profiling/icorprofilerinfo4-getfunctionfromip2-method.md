---
title: ICorProfilerInfo4::GetFunctionFromIP2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: 5153a25ef87d9c06bb46b74945c8eb68eb041682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443140"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="12dc1-102">ICorProfilerInfo4::GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="12dc1-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="12dc1-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span><span class="sxs-lookup"><span data-stu-id="12dc1-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12dc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12dc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12dc1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12dc1-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="12dc1-106">[in] The instruction pointer in managed code.</span><span class="sxs-lookup"><span data-stu-id="12dc1-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="12dc1-107">[out] The function ID.</span><span class="sxs-lookup"><span data-stu-id="12dc1-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="12dc1-108">[out] The identity of the JIT-recompiled version of the function.</span><span class="sxs-lookup"><span data-stu-id="12dc1-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12dc1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12dc1-109">Remarks</span></span>  
 <span data-ttu-id="12dc1-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span><span class="sxs-lookup"><span data-stu-id="12dc1-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12dc1-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span><span class="sxs-lookup"><span data-stu-id="12dc1-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="12dc1-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="12dc1-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12dc1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12dc1-113">Requirements</span></span>  
 <span data-ttu-id="12dc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12dc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12dc1-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12dc1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12dc1-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12dc1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12dc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12dc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dc1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12dc1-118">See also</span></span>

- [<span data-ttu-id="12dc1-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12dc1-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
