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
ms.openlocfilehash: a30dde6f406cfb6d1140e7cd8e2a8f8f3ab40006
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="f9b5a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="f9b5a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="f9b5a-103">Určuje implementované profileru funkce, které bude volána při [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9b5a-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9b5a-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="f9b5a-106">[v] Ukazatel na implementaci má být použit jako `FunctionEnter3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="f9b5a-107">[v] Ukazatel na implementaci má být použit jako `FunctionLeave3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="f9b5a-108">[v] Ukazatel na implementaci má být použit jako `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9b5a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9b5a-109">Remarks</span></span>  
 <span data-ttu-id="f9b5a-110">[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky poskytují rámec a argument kontroly zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="f9b5a-111">Přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, nebo `COR_PRF_ENABLE_FRAME_INFO` příznaky musí být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="f9b5a-112">Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) má metoda nastavte příznaky události a potom pomocí `SetEnterLeaveFunctionHooks3WithInfo` metody pro registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f9b5a-113">Jen jednu sadu zpětná volání může být aktivní v čase a má přednost před nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="f9b5a-114">Proto pokud profileru volá obě [setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` se používá.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="f9b5a-115">`SetEnterLeaveFunctionHooks3WithInfo` Metoda může volat pouze z okna profilování [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9b5a-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b5a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9b5a-116">Requirements</span></span>  
 <span data-ttu-id="f9b5a-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b5a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b5a-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9b5a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9b5a-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9b5a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9b5a-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b5a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b5a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9b5a-121">See Also</span></span>  
 [<span data-ttu-id="f9b5a-122">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="f9b5a-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="f9b5a-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="f9b5a-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="f9b5a-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="f9b5a-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="f9b5a-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f9b5a-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="f9b5a-129">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="f9b5a-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="f9b5a-130">Icorprofilerinfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9b5a-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f9b5a-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f9b5a-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f9b5a-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="f9b5a-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
