---
title: "FunctionTailcall3WithInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3WithInfo
helpviewer_keywords: FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bd2bb56724f977d93e6ebff7d2c4c855a5a222b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="7dacd-102">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="7dacd-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="7dacd-103">Upozorní profileru, který aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) načíst rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7dacd-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dacd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dacd-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dacd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dacd-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="7dacd-106">[v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.</span><span class="sxs-lookup"><span data-stu-id="7dacd-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7dacd-107">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7dacd-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7dacd-108">Tento popisovač je platný pouze během zpětného volání, ke kterému je předán.</span><span class="sxs-lookup"><span data-stu-id="7dacd-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dacd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7dacd-109">Remarks</span></span>  
 <span data-ttu-id="7dacd-110">`FunctionTailcall3WithInfo` Metoda zpětného volání upozorní profileru jako funkce se nazývají a umožňuje profileru používat [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) kontrola rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7dacd-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="7dacd-111">Přístup k informacím rámce zásobníku, `COR_PRF_ENABLE_FRAME_INFO` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="7dacd-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="7dacd-112">Můžete použít profileru [icorprofilerinfo::seteventmask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavte příznaky událostí, a pak použít [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="7dacd-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7dacd-113">`FunctionTailcall3WithInfo` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="7dacd-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="7dacd-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="7dacd-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7dacd-115">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="7dacd-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="7dacd-116">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="7dacd-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="7dacd-117">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="7dacd-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7dacd-118">Implementace `FunctionTailcall3WithInfo` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7dacd-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7dacd-119">Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="7dacd-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7dacd-120">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7dacd-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="7dacd-121">Functiontailcall3withinfo – funkce nesmí navíc volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7dacd-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dacd-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7dacd-122">Requirements</span></span>  
 <span data-ttu-id="7dacd-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dacd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dacd-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7dacd-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7dacd-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dacd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dacd-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dacd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dacd-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dacd-127">See Also</span></span>  
 [<span data-ttu-id="7dacd-128">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="7dacd-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="7dacd-129">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="7dacd-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="7dacd-130">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="7dacd-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="7dacd-131">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="7dacd-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="7dacd-132">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="7dacd-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="7dacd-133">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="7dacd-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="7dacd-134">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="7dacd-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="7dacd-135">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="7dacd-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="7dacd-136">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="7dacd-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="7dacd-137">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7dacd-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
