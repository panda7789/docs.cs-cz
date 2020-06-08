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
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496230"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="1032a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda</span><span class="sxs-lookup"><span data-stu-id="1032a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="1032a-103">Určuje funkce implementované profilerem, které budou volány ve funkcích [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1032a-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1032a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1032a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1032a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1032a-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="1032a-106">pro Ukazatel na implementaci, která se má použít jako `FunctionEnter3` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="1032a-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="1032a-107">pro Ukazatel na implementaci, která se má použít jako `FunctionLeave3` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="1032a-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="1032a-108">pro Ukazatel na implementaci, která se má použít jako `FunctionTailcall3` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="1032a-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1032a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1032a-109">Remarks</span></span>  
 <span data-ttu-id="1032a-110">[FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md) háky neposkytují kontrolu rámce zásobníku a argumentů.</span><span class="sxs-lookup"><span data-stu-id="1032a-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="1032a-111">Pro přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` `COR_PRF_ENABLE_FRAME_INFO` musí být nastavené příznaky, a.</span><span class="sxs-lookup"><span data-stu-id="1032a-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="1032a-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít metodu [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="1032a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="1032a-113">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="1032a-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="1032a-114">Proto pokud profiler volá [metodu SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3` metodu, `SetEnterLeaveFunctionHooks3` je použit.</span><span class="sxs-lookup"><span data-stu-id="1032a-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="1032a-115">`SetEnterLeaveFunctionHooks3`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="1032a-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1032a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1032a-116">Requirements</span></span>  
 <span data-ttu-id="1032a-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1032a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1032a-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1032a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1032a-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1032a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1032a-120">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1032a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1032a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1032a-121">See also</span></span>

- [<span data-ttu-id="1032a-122">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="1032a-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="1032a-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="1032a-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="1032a-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="1032a-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="1032a-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="1032a-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="1032a-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="1032a-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="1032a-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="1032a-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="1032a-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="1032a-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="1032a-129">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="1032a-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="1032a-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="1032a-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1032a-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1032a-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1032a-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="1032a-132">Profiling</span></span>](index.md)
