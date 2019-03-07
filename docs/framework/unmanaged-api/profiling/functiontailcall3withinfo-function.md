---
title: FunctionTailcall3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4c3487f39d4f4c667ec9eb4705e17ccf29d9a4c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490382"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="d6998-102">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="d6998-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="d6998-103">Oznámí profileru, který aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který lze předat [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) načíst rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6998-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6998-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6998-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6998-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6998-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="d6998-106">[in] Identifikátor aktuálně prováděné funkci, která se chystá provést tail volání.</span><span class="sxs-lookup"><span data-stu-id="d6998-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="d6998-107">[in] Neprůhledný popisovač, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6998-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="d6998-108">Tento popisovač je platný pouze během zpětného volání, který je předán.</span><span class="sxs-lookup"><span data-stu-id="d6998-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6998-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6998-109">Remarks</span></span>  
 <span data-ttu-id="d6998-110">`FunctionTailcall3WithInfo` Metoda zpětného volání oznámí profileru a funkce jsou volány umožňuje profileru používat [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) ke kontrole rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6998-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="d6998-111">Přístup k informacím rámce zásobníku, `COR_PRF_ENABLE_FRAME_INFO` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="d6998-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="d6998-112">Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí, a pak používat [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vašeho implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="d6998-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d6998-113">`FunctionTailcall3WithInfo` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="d6998-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="d6998-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="d6998-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="d6998-115">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="d6998-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="d6998-116">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="d6998-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="d6998-117">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="d6998-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d6998-118">Provádění `FunctionTailcall3WithInfo` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6998-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="d6998-119">Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6998-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d6998-120">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionTailcall3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="d6998-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="d6998-121">Functiontailcall3withinfo – funkce také, nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d6998-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6998-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6998-122">Requirements</span></span>  
 <span data-ttu-id="d6998-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6998-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6998-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d6998-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d6998-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6998-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6998-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6998-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6998-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6998-127">See also</span></span>
- [<span data-ttu-id="d6998-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d6998-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="d6998-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="d6998-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="d6998-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d6998-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d6998-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6998-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d6998-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6998-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="d6998-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="d6998-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="d6998-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6998-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="d6998-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d6998-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d6998-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d6998-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="d6998-137">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d6998-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
