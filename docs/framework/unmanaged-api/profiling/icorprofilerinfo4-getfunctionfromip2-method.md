---
title: "ICorProfilerInfo4::GetFunctionFromIP2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f354bdc198a8060c7241a2b9bdb472bee5ed7b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="024f9-102">ICorProfilerInfo4::GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="024f9-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="024f9-103">Mapuje ukazatel instrukce spravovaného kódu na verzi překompilovat JIT funkce.</span><span class="sxs-lookup"><span data-stu-id="024f9-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="024f9-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="024f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="024f9-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="024f9-106">[v] Ukazatel instrukce ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="024f9-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="024f9-107">[out] ID funkce.</span><span class="sxs-lookup"><span data-stu-id="024f9-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="024f9-108">[out] Identita překompilovat JIT verze funkce.</span><span class="sxs-lookup"><span data-stu-id="024f9-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="024f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="024f9-109">Remarks</span></span>  
 <span data-ttu-id="024f9-110">`GetFunctionFromIP2`je podobná `GetFunctionFromIP`kromě toho, že získá ID překompilovat JIT místo ID funkce funkce, která obsahuje zadaná IP adresa.</span><span class="sxs-lookup"><span data-stu-id="024f9-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="024f9-111">`GetFunctionFromIP2`můžete aktivovat uvolňování paměti, zatímco `GetFunctionFromIP` nikoli.</span><span class="sxs-lookup"><span data-stu-id="024f9-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="024f9-112">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="024f9-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="024f9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="024f9-113">Requirements</span></span>  
 <span data-ttu-id="024f9-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="024f9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024f9-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="024f9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="024f9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="024f9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="024f9-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024f9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="024f9-118">See Also</span></span>  
 [<span data-ttu-id="024f9-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="024f9-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
