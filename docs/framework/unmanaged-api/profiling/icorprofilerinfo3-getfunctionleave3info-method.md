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
ms.openlocfilehash: bacb50520df9f1553226ec6bf1e878238b64bb17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449706"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="6426b-102">ICorProfilerInfo3::GetFunctionLeave3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="6426b-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="6426b-103">Poskytuje rámec zásobníku a návratovou hodnotu funkce, která je hlášena profileru funkcí [FunctionLeave3WithInfo – Function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6426b-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="6426b-104">Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6426b-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6426b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6426b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6426b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6426b-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6426b-107">pro `FunctionID` funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="6426b-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6426b-108">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6426b-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6426b-109">Profiler by měl poskytnout stejnou `eltInfo`, která byla přidělena profileru funkcí [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6426b-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="6426b-110">mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6426b-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="6426b-111">Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětného volání, ve kterém Profiler volal metodu `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="6426b-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="6426b-112">mimo Ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) , která obsahuje hodnotu vrácenou z funkce.</span><span class="sxs-lookup"><span data-stu-id="6426b-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="6426b-113">Chcete-li získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="6426b-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="6426b-114">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.</span><span class="sxs-lookup"><span data-stu-id="6426b-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6426b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6426b-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6426b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6426b-116">Requirements</span></span>  
 <span data-ttu-id="6426b-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6426b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6426b-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6426b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6426b-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6426b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6426b-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6426b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6426b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6426b-121">See also</span></span>

- [<span data-ttu-id="6426b-122">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6426b-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="6426b-123">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6426b-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="6426b-124">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6426b-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6426b-125">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6426b-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6426b-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6426b-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6426b-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="6426b-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
