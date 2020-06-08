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
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496175"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="2433f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2433f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="2433f-103">Určuje funkce implementované profilerem, které budou volány na [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –ch](functiontailcall3withinfo-function.md) zapojování spravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="2433f-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2433f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2433f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2433f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2433f-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="2433f-106">pro Ukazatel na implementaci, která se má použít jako `FunctionEnter3WithInfo` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="2433f-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="2433f-107">pro Ukazatel na implementaci, která se má použít jako `FunctionLeave3WithInfo` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="2433f-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="2433f-108">pro Ukazatel na implementaci, která se má použít jako `FunctionTailcall3WithInfo` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="2433f-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2433f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2433f-109">Remarks</span></span>  
 <span data-ttu-id="2433f-110">Vidlice [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) poskytují kontrolu rámce zásobníku a argumentů.</span><span class="sxs-lookup"><span data-stu-id="2433f-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="2433f-111">Pro přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` `COR_PRF_ENABLE_FRAME_INFO` musí být nastavené příznaky, a.</span><span class="sxs-lookup"><span data-stu-id="2433f-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="2433f-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a potom použít `SetEnterLeaveFunctionHooks3WithInfo` metodu k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="2433f-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="2433f-113">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost.</span><span class="sxs-lookup"><span data-stu-id="2433f-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="2433f-114">Proto pokud profiler volá [SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3WithInfo` , `SetEnterLeaveFunctionHooks3WithInfo` je použit.</span><span class="sxs-lookup"><span data-stu-id="2433f-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="2433f-115">`SetEnterLeaveFunctionHooks3WithInfo`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="2433f-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2433f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2433f-116">Requirements</span></span>  
 <span data-ttu-id="2433f-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2433f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2433f-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2433f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2433f-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2433f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2433f-120">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2433f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2433f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2433f-121">See also</span></span>

- [<span data-ttu-id="2433f-122">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="2433f-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="2433f-123">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="2433f-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="2433f-124">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="2433f-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="2433f-125">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="2433f-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="2433f-126">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="2433f-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="2433f-127">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="2433f-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="2433f-128">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="2433f-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="2433f-129">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="2433f-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="2433f-130">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2433f-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2433f-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2433f-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2433f-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="2433f-132">Profiling</span></span>](index.md)
