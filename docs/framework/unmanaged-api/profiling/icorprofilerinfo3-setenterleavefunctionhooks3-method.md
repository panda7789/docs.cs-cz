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
ms.openlocfilehash: da56018216a7c6cebdc0ec222d1cb1be3633ecc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449606"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="6dff9-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda</span><span class="sxs-lookup"><span data-stu-id="6dff9-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="6dff9-103">Určuje funkce implementované profilerem, které budou volány ve funkcích [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6dff9-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dff9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dff9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dff9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dff9-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="6dff9-106">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionEnter3`.</span><span class="sxs-lookup"><span data-stu-id="6dff9-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="6dff9-107">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionLeave3`.</span><span class="sxs-lookup"><span data-stu-id="6dff9-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="6dff9-108">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionTailcall3`.</span><span class="sxs-lookup"><span data-stu-id="6dff9-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dff9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dff9-109">Remarks</span></span>  
 <span data-ttu-id="6dff9-110">[FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) háky neposkytují kontrolu rámce zásobníku a argumentů.</span><span class="sxs-lookup"><span data-stu-id="6dff9-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="6dff9-111">Pro přístup k těmto informacím musí být nastavené příznaky `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`a/nebo `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="6dff9-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="6dff9-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít metodu [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="6dff9-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6dff9-113">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="6dff9-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="6dff9-114">Proto pokud profiler volá [metodu SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i metodu `SetEnterLeaveFunctionHooks3`, `SetEnterLeaveFunctionHooks3` se používá.</span><span class="sxs-lookup"><span data-stu-id="6dff9-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="6dff9-115">Metodu `SetEnterLeaveFunctionHooks3` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6dff9-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dff9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dff9-116">Requirements</span></span>  
 <span data-ttu-id="6dff9-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dff9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dff9-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6dff9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dff9-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6dff9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dff9-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dff9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dff9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dff9-121">See also</span></span>

- [<span data-ttu-id="6dff9-122">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6dff9-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="6dff9-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="6dff9-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="6dff9-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="6dff9-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="6dff9-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="6dff9-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="6dff9-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6dff9-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="6dff9-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6dff9-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="6dff9-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="6dff9-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6dff9-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6dff9-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="6dff9-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="6dff9-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6dff9-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6dff9-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6dff9-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="6dff9-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
