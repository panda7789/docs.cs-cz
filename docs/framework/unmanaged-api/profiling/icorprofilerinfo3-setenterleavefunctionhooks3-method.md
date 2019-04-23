---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73321a28b1c61775d08e2c60ee2b9a863b8250dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121677"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="f4993-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda</span><span class="sxs-lookup"><span data-stu-id="f4993-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="f4993-103">Určuje funkce implementované profileru, které bude volána při [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f4993-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4993-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4993-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4993-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="f4993-106">[in] Ukazatel na implementaci pro použití jako `FunctionEnter3` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f4993-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="f4993-107">[in] Ukazatel na implementaci pro použití jako `FunctionLeave3` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f4993-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="f4993-108">[in] Ukazatel na implementaci pro použití jako `FunctionTailcall3` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f4993-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4993-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4993-109">Remarks</span></span>  
 <span data-ttu-id="f4993-110">[Functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) háky neposkytují kontroly zásobníku rámce a argumentů.</span><span class="sxs-lookup"><span data-stu-id="f4993-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="f4993-111">Přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, a/nebo `COR_PRF_ENABLE_FRAME_INFO` příznaky musí být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="f4993-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="f4993-112">Profiler může použít [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metoda nastavit příznaky událostí, a pak používat [icorprofilerinfo3::setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metody pro registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="f4993-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f4993-113">Pouze jednu sadu zpětná volání může být aktivní v čase a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="f4993-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="f4993-114">Proto pokud profiler volá i [setenterleavefunctionhooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3` metody `SetEnterLeaveFunctionHooks3` se používá.</span><span class="sxs-lookup"><span data-stu-id="f4993-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="f4993-115">`SetEnterLeaveFunctionHooks3` Metoda může volat pouze z okna profilování [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f4993-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4993-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4993-116">Requirements</span></span>  
 <span data-ttu-id="f4993-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4993-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4993-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4993-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4993-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4993-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4993-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4993-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4993-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4993-121">See also</span></span>

- [<span data-ttu-id="f4993-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f4993-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f4993-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f4993-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="f4993-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f4993-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="f4993-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="f4993-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="f4993-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f4993-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="f4993-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f4993-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="f4993-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f4993-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f4993-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f4993-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="f4993-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="f4993-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f4993-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f4993-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f4993-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="f4993-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
