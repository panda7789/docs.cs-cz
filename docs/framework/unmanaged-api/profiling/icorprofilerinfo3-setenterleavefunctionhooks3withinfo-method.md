---
title: "ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9d9af004abbee19d6b553c431381af55d210095
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="d5828-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d5828-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="d5828-103">Určuje implementované profileru funkce, které bude volána při [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="d5828-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5828-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5828-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="d5828-106">[v] Ukazatel na implementaci má být použit jako `FunctionEnter3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5828-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="d5828-107">[v] Ukazatel na implementaci má být použit jako `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5828-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="d5828-108">[v] Ukazatel na implementaci má být použit jako `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5828-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5828-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5828-109">Remarks</span></span>  
 <span data-ttu-id="d5828-110">[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky poskytují rámec a argument kontroly zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d5828-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="d5828-111">Přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, nebo `COR_PRF_ENABLE_FRAME_INFO` příznaky musí být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="d5828-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="d5828-112">Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) má metoda nastavte příznaky události a potom pomocí `SetEnterLeaveFunctionHooks3WithInfo` metody pro registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="d5828-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d5828-113">Jen jednu sadu zpětná volání může být aktivní v čase a má přednost před nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="d5828-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="d5828-114">Proto pokud profileru volá obě [setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` se používá.</span><span class="sxs-lookup"><span data-stu-id="d5828-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="d5828-115">`SetEnterLeaveFunctionHooks3WithInfo` Metoda může volat pouze z okna profilování [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5828-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5828-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5828-116">Requirements</span></span>  
 <span data-ttu-id="d5828-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5828-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5828-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5828-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5828-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5828-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5828-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5828-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5828-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5828-121">See Also</span></span>  
 [<span data-ttu-id="d5828-122">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="d5828-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="d5828-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="d5828-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="d5828-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="d5828-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="d5828-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="d5828-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="d5828-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5828-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="d5828-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5828-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="d5828-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5828-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="d5828-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5828-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="d5828-130">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5828-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="d5828-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5828-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d5828-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="d5828-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
