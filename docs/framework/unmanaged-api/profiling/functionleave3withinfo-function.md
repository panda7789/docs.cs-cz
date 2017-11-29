---
title: "FunctionLeave3WithInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3WithInfo
helpviewer_keywords: FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e42614531afb11a811e8862abad0caddf8873483
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="b2a09-102">FunctionLeave3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="b2a09-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="b2a09-103">Profileru upozorní, že se vrací ovládací prvek z funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctionleave3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) načíst rámce zásobníku a návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2a09-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2a09-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2a09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2a09-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="b2a09-106">[v] Identifikátor funkce, ze kterého se vrátí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b2a09-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b2a09-107">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b2a09-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b2a09-108">Tento popisovač je platný pouze během zpětného volání, ke kterému je předán.</span><span class="sxs-lookup"><span data-stu-id="b2a09-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2a09-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2a09-109">Remarks</span></span>  
 <span data-ttu-id="b2a09-110">`FunctionLeave3WithInfo` Metoda zpětného volání upozorní profileru jako funkce se nazývají a umožňuje profileru používat [icorprofilerinfo3::getfunctionleave3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) kontrola návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2a09-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="b2a09-111">Pro přístup k informacím návratovou hodnotu `COR_PRF_ENABLE_FUNCTION_RETVAL` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="b2a09-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="b2a09-112">Můžete použít profileru [icorprofilerinfo::seteventmask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavte příznaky událostí, a pak použít [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="b2a09-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b2a09-113">`FunctionLeave3WithInfo` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="b2a09-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="b2a09-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="b2a09-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b2a09-115">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="b2a09-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="b2a09-116">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="b2a09-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="b2a09-117">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="b2a09-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b2a09-118">Implementace `FunctionLeave3WithInfo` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b2a09-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b2a09-119">Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="b2a09-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b2a09-120">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="b2a09-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="b2a09-121">`FunctionLeave3WithInfo` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b2a09-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a09-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2a09-122">Requirements</span></span>  
 <span data-ttu-id="b2a09-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a09-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a09-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b2a09-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b2a09-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2a09-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2a09-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a09-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a09-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2a09-127">See Also</span></span>  
 [<span data-ttu-id="b2a09-128">Getfunctionleave3info –</span><span class="sxs-lookup"><span data-stu-id="b2a09-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)  
 [<span data-ttu-id="b2a09-129">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="b2a09-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="b2a09-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="b2a09-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="b2a09-131">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="b2a09-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="b2a09-132">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b2a09-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="b2a09-133">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b2a09-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="b2a09-134">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="b2a09-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="b2a09-135">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b2a09-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="b2a09-136">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="b2a09-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="b2a09-137">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="b2a09-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="b2a09-138">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="b2a09-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
