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
ms.openlocfilehash: b17ab9382e5195881e5629d482e4327fc67562f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449587"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="4eab1-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="4eab1-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="4eab1-103">Určuje funkce implementované profilerem, které budou volány na [FunctionEnter3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –ch](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zapojování spravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="4eab1-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eab1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4eab1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eab1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4eab1-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="4eab1-106">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="4eab1-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="4eab1-107">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="4eab1-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="4eab1-108">pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="4eab1-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eab1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4eab1-109">Remarks</span></span>  
 <span data-ttu-id="4eab1-110">Vidlice [FunctionEnter3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) poskytují kontrolu rámce zásobníku a argumentů.</span><span class="sxs-lookup"><span data-stu-id="4eab1-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="4eab1-111">Pro přístup k těmto informacím musí být nastavené příznaky `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`a/nebo `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="4eab1-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="4eab1-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít metodu `SetEnterLeaveFunctionHooks3WithInfo` k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="4eab1-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4eab1-113">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="4eab1-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="4eab1-114">Proto pokud profiler volá [SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` se používá.</span><span class="sxs-lookup"><span data-stu-id="4eab1-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="4eab1-115">Metodu `SetEnterLeaveFunctionHooks3WithInfo` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4eab1-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eab1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4eab1-116">Requirements</span></span>  
 <span data-ttu-id="4eab1-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eab1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eab1-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4eab1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4eab1-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4eab1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eab1-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eab1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eab1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4eab1-121">See also</span></span>

- [<span data-ttu-id="4eab1-122">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="4eab1-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="4eab1-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="4eab1-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="4eab1-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="4eab1-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="4eab1-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="4eab1-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="4eab1-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="4eab1-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="4eab1-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="4eab1-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="4eab1-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="4eab1-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="4eab1-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4eab1-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="4eab1-130">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4eab1-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4eab1-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4eab1-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4eab1-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="4eab1-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
