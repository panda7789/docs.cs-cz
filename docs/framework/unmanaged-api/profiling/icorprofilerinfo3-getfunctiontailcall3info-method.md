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
ms.openlocfilehash: c78d22c6566b49e85a59e4a682fa256d2d83ea3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455582"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="f2140-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="f2140-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="f2140-103">Poskytuje rámce zásobníku funkce, která je hlášena profileru pomocí [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f2140-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="f2140-104">Tuto metodu lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f2140-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2140-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2140-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2140-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2140-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f2140-107">[v] `FunctionID` Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="f2140-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="f2140-108">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f2140-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f2140-109">Profileru by měl poskytovat stejné `eltInfo` který byl zadán profileru pomocí `FunctionTailcall3WithInfo` funkce.</span><span class="sxs-lookup"><span data-stu-id="f2140-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="f2140-110">[out] Neprůhledného popisovače, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f2140-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="f2140-111">Tento popisovač je platný pouze během `FunctionTailcall3WithInfo` zpětného volání, ve kterém se nazývá profileru `GetFunctionTailcall3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="f2140-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2140-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2140-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2140-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2140-113">Requirements</span></span>  
 <span data-ttu-id="f2140-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2140-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2140-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2140-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2140-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2140-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2140-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2140-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2140-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2140-118">See Also</span></span>  
 [<span data-ttu-id="f2140-119">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f2140-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="f2140-120">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f2140-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="f2140-121">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f2140-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="f2140-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2140-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f2140-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f2140-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f2140-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="f2140-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
