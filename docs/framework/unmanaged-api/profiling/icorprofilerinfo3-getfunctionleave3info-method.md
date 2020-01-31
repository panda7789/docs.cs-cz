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
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862396"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="32fb2-102">ICorProfilerInfo3::GetFunctionLeave3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="32fb2-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="32fb2-103">Poskytuje rámec zásobníku a návratovou hodnotu funkce, která je hlášena profileru funkcí [FunctionLeave3WithInfo – Function](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="32fb2-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="32fb2-104">Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="32fb2-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32fb2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32fb2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32fb2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="32fb2-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="32fb2-107">pro `FunctionID` funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="32fb2-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="32fb2-108">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="32fb2-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="32fb2-109">Profiler by měl poskytnout stejnou `eltInfo`, která byla přidělena profileru funkcí [FunctionLeave3WithInfo –](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="32fb2-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="32fb2-110">mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="32fb2-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="32fb2-111">Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětného volání, ve kterém Profiler volal metodu `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="32fb2-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="32fb2-112">mimo Ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , která obsahuje hodnotu vrácenou z funkce.</span><span class="sxs-lookup"><span data-stu-id="32fb2-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="32fb2-113">Chcete-li získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="32fb2-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="32fb2-114">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.</span><span class="sxs-lookup"><span data-stu-id="32fb2-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32fb2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32fb2-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32fb2-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32fb2-116">Requirements</span></span>  
 <span data-ttu-id="32fb2-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32fb2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32fb2-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="32fb2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32fb2-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32fb2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32fb2-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32fb2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fb2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32fb2-121">See also</span></span>

- [<span data-ttu-id="32fb2-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="32fb2-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="32fb2-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="32fb2-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="32fb2-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="32fb2-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="32fb2-125">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32fb2-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="32fb2-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="32fb2-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="32fb2-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="32fb2-127">Profiling</span></span>](index.md)
