---
title: ICorProfilerInfo3::GetFunctionLeave3Info – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172390"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="ec92b-102">ICorProfilerInfo3::GetFunctionLeave3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="ec92b-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="ec92b-103">Poskytuje rámec zásobníku a návratovou hodnotu funkce, která se hlásí do profileru pomocí [functionleave3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ec92b-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="ec92b-104">Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ec92b-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec92b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec92b-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec92b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec92b-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ec92b-107">[in] `FunctionID` Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="ec92b-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="ec92b-108">[in] Neprůhledný popisovač, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ec92b-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="ec92b-109">Profiler by měl poskytovat stejné `eltInfo` , který byl zadán do profileru pomocí [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ec92b-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="ec92b-110">[out] Neprůhledný popisovač, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ec92b-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="ec92b-111">Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětné volání, ve kterém profiler volal `GetFunctionLeave3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="ec92b-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="ec92b-112">[out] Ukazatel [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturu, která obsahuje hodnotu, která je vrácena z funkce.</span><span class="sxs-lookup"><span data-stu-id="ec92b-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="ec92b-113">Přístup k informacím návratová hodnota `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="ec92b-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="ec92b-114">Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="ec92b-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec92b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec92b-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec92b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec92b-116">Requirements</span></span>  
 <span data-ttu-id="ec92b-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec92b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec92b-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec92b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec92b-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec92b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec92b-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec92b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec92b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec92b-121">See also</span></span>

- [<span data-ttu-id="ec92b-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ec92b-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="ec92b-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ec92b-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="ec92b-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ec92b-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ec92b-125">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec92b-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ec92b-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ec92b-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ec92b-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="ec92b-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
