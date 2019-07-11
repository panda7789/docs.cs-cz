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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74f0e6e39f99c9e6981066e6a3171bb9508cf1a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782142"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="0db97-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="0db97-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="0db97-103">Poskytuje funkce, která se hlásí do profileru pomocí rámce zásobníku [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0db97-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="0db97-104">Tuto metodu lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0db97-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db97-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0db97-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0db97-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0db97-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0db97-107">[in] `FunctionID` Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="0db97-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="0db97-108">[in] Neprůhledný popisovač, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0db97-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0db97-109">Profiler by měl poskytovat stejné `eltInfo` , který byl zadán do profileru pomocí `FunctionTailcall3WithInfo` funkce.</span><span class="sxs-lookup"><span data-stu-id="0db97-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="0db97-110">[out] Neprůhledný popisovač, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0db97-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="0db97-111">Tento popisovač je platný pouze během `FunctionTailcall3WithInfo` zpětné volání, ve kterém profiler volal `GetFunctionTailcall3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="0db97-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0db97-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0db97-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0db97-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0db97-113">Requirements</span></span>  
 <span data-ttu-id="0db97-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0db97-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0db97-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0db97-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0db97-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0db97-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0db97-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0db97-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db97-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0db97-118">See also</span></span>

- [<span data-ttu-id="0db97-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db97-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="0db97-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db97-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="0db97-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db97-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0db97-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0db97-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0db97-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0db97-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0db97-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="0db97-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
