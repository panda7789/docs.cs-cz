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
ms.openlocfilehash: 8ad04a7a6705b961686317c9473b885fb90676ce
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861915"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="5b7b6-102">ICorProfilerInfo4::GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5b7b6-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="5b7b6-103">Mapuje ukazatel na instrukci spravovaného kódu pro Rekompilované verze funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="5b7b6-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b7b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b7b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b7b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b7b6-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="5b7b6-106">pro Ukazatel na instrukci ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="5b7b6-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="5b7b6-107">mimo ID funkce</span><span class="sxs-lookup"><span data-stu-id="5b7b6-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="5b7b6-108">mimo Identita funkce Rekompilované verze JIT.</span><span class="sxs-lookup"><span data-stu-id="5b7b6-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b7b6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b7b6-109">Remarks</span></span>  
 <span data-ttu-id="5b7b6-110">`GetFunctionFromIP2` je podobná `GetFunctionFromIP`, s tím rozdílem, že získá znovu zkompilované ID JIT namísto ID funkce funkce, která obsahuje zadanou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="5b7b6-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b7b6-111">`GetFunctionFromIP2` může aktivovat uvolňování paměti, zatímco `GetFunctionFromIP` nebude.</span><span class="sxs-lookup"><span data-stu-id="5b7b6-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="5b7b6-112">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="5b7b6-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b7b6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b7b6-113">Requirements</span></span>  
 <span data-ttu-id="5b7b6-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b7b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b7b6-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b7b6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b7b6-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b7b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b7b6-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b7b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b7b6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b7b6-118">See also</span></span>

- [<span data-ttu-id="5b7b6-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b7b6-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
