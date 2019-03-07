---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 287f08c4ce5108ac9ae871135976cb45917fa861
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476706"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="fb12d-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fb12d-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="fb12d-103">Určuje funkce implementované profileru, které bude volána při [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="fb12d-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb12d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb12d-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb12d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb12d-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="fb12d-106">[in] Ukazatel na implementaci pro použití jako `FunctionEnter3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fb12d-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="fb12d-107">[in] Ukazatel na implementaci pro použití jako `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fb12d-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="fb12d-108">[in] Ukazatel na implementaci pro použití jako `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fb12d-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb12d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb12d-109">Remarks</span></span>  
 <span data-ttu-id="fb12d-110">[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) poskytovat háky kontroly zásobníku rámce a argument.</span><span class="sxs-lookup"><span data-stu-id="fb12d-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="fb12d-111">Přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, a/nebo `COR_PRF_ENABLE_FRAME_INFO` příznaky musí být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="fb12d-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="fb12d-112">Profiler může použít [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metoda nastavit příznaky událostí, a pak používat `SetEnterLeaveFunctionHooks3WithInfo` metody pro registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="fb12d-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fb12d-113">Pouze jednu sadu zpětná volání může být aktivní v čase a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="fb12d-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="fb12d-114">Proto pokud profiler volá obě [setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` se používá.</span><span class="sxs-lookup"><span data-stu-id="fb12d-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="fb12d-115">`SetEnterLeaveFunctionHooks3WithInfo` Metoda může volat pouze z okna profilování [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fb12d-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb12d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb12d-116">Requirements</span></span>  
 <span data-ttu-id="fb12d-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb12d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb12d-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb12d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb12d-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb12d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb12d-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb12d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb12d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb12d-121">See also</span></span>
- [<span data-ttu-id="fb12d-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="fb12d-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="fb12d-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fb12d-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="fb12d-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fb12d-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="fb12d-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fb12d-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="fb12d-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fb12d-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="fb12d-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fb12d-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="fb12d-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fb12d-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="fb12d-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fb12d-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="fb12d-130">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb12d-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fb12d-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fb12d-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fb12d-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="fb12d-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
