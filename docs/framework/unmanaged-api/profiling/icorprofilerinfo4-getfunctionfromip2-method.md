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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7281f1aa0da417eba618b748ac68ba1fefb4907d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780855"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="a5142-102">ICorProfilerInfo4::GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a5142-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="a5142-103">Mapuje ukazatel na instrukci spravovaného kódu na verzi funkce překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="a5142-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5142-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5142-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5142-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5142-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="a5142-106">[in] Ukazatele na instrukci ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a5142-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="a5142-107">[out] ID funkce.</span><span class="sxs-lookup"><span data-stu-id="a5142-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="a5142-108">[out] Identita překompilován JIT verze funkce.</span><span class="sxs-lookup"><span data-stu-id="a5142-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5142-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5142-109">Remarks</span></span>  
 <span data-ttu-id="a5142-110">`GetFunctionFromIP2` je podobný `GetFunctionFromIP`, s tím rozdílem, že získá ID překompilován JIT místo ID funkce funkce, která obsahuje zadaná IP adresa.</span><span class="sxs-lookup"><span data-stu-id="a5142-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5142-111">`GetFunctionFromIP2` můžete aktivovat kolekce uvolnění paměti, že `GetFunctionFromIP` se tak nestane.</span><span class="sxs-lookup"><span data-stu-id="a5142-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="a5142-112">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="a5142-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5142-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5142-113">Requirements</span></span>  
 <span data-ttu-id="a5142-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5142-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5142-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5142-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5142-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5142-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5142-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5142-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5142-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5142-118">See also</span></span>

- [<span data-ttu-id="a5142-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5142-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
