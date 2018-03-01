---
title: "ICorProfilerInfo3::GetFunctionTailcall3Info – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec36194a11d3d85353c96d4c048d4932071958cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="78123-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="78123-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="78123-103">Poskytuje rámce zásobníku funkce, která je hlášena profileru pomocí [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="78123-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="78123-104">Tuto metodu lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="78123-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78123-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78123-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78123-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="78123-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="78123-107">[v] `FunctionID` Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="78123-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="78123-108">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="78123-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="78123-109">Profileru by měl poskytovat stejné `eltInfo` který byl zadán profileru pomocí `FunctionTailcall3WithInfo` funkce.</span><span class="sxs-lookup"><span data-stu-id="78123-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="78123-110">[out] Neprůhledného popisovače, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="78123-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="78123-111">Tento popisovač je platný pouze během `FunctionTailcall3WithInfo` zpětného volání, ve kterém se nazývá profileru `GetFunctionTailcall3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="78123-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78123-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78123-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78123-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78123-113">Requirements</span></span>  
 <span data-ttu-id="78123-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78123-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78123-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78123-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78123-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78123-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78123-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78123-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78123-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="78123-118">See Also</span></span>  
 [<span data-ttu-id="78123-119">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="78123-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="78123-120">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="78123-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="78123-121">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="78123-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="78123-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78123-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="78123-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="78123-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="78123-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="78123-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
