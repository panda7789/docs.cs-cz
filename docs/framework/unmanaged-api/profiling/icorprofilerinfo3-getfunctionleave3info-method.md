---
title: "ICorProfilerInfo3::GetFunctionLeave3Info – metoda"
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
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5cbd73b6bfe89bec50eff0e09ec078db912adf25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="d0d8e-102">ICorProfilerInfo3::GetFunctionLeave3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d8e-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="d0d8e-103">Poskytuje rámce zásobníku a návratové hodnoty funkce, která je hlášena profileru pomocí [functionleave3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="d0d8e-104">Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d8e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d8e-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0d8e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0d8e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d0d8e-107">[v] `FunctionID` Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="d0d8e-108">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="d0d8e-109">Profileru by měl poskytovat stejné `eltInfo` který byl zadán profileru pomocí [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="d0d8e-110">[out] Neprůhledného popisovače, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="d0d8e-111">Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětného volání, ve kterém se nazývá profileru `GetFunctionLeave3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="d0d8e-112">[out] Ukazatel [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktura, která obsahuje hodnotu, která je vrácena z funkce.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="d0d8e-113">Pro přístup k informacím návratovou hodnotu `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="d0d8e-114">Můžete použít profileru [icorprofilerinfo::seteventmask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="d0d8e-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0d8e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0d8e-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d8e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0d8e-116">Requirements</span></span>  
 <span data-ttu-id="d0d8e-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d8e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d8e-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0d8e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0d8e-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0d8e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0d8e-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d8e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d8e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d8e-121">See Also</span></span>  
 [<span data-ttu-id="d0d8e-122">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d0d8e-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="d0d8e-123">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d0d8e-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="d0d8e-124">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d0d8e-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="d0d8e-125">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d8e-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="d0d8e-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d0d8e-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d0d8e-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="d0d8e-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
