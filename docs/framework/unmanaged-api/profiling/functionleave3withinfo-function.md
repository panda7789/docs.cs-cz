---
title: FunctionLeave3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4304c933b9802ef565b8d18f1e04591e7fa83cb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189914"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="fa45b-102">FunctionLeave3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="fa45b-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="fa45b-103">Profiler upozorní, že ovládací prvek se vrací z funkce a poskytuje popisovač, který lze předat [icorprofilerinfo3::getfunctionleave3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) načíst rámec zásobníku a návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa45b-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa45b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa45b-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa45b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa45b-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="fa45b-106">[in] Identifikátor funkce, ve kterém ovládací prvek se vrátí.</span><span class="sxs-lookup"><span data-stu-id="fa45b-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="fa45b-107">[in] Neprůhledný popisovač, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fa45b-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="fa45b-108">Tento popisovač je platný pouze během zpětného volání, který je předán.</span><span class="sxs-lookup"><span data-stu-id="fa45b-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa45b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa45b-109">Remarks</span></span>  
 <span data-ttu-id="fa45b-110">`FunctionLeave3WithInfo` Metoda zpětného volání oznámí profileru a funkce jsou volány umožňuje profileru používat [icorprofilerinfo3::getfunctionleave3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) zkontrolovat návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa45b-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="fa45b-111">Přístup k informacím návratová hodnota `COR_PRF_ENABLE_FUNCTION_RETVAL` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="fa45b-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="fa45b-112">Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí, a pak používat [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vašeho implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="fa45b-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fa45b-113">`FunctionLeave3WithInfo` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="fa45b-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="fa45b-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="fa45b-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="fa45b-115">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="fa45b-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="fa45b-116">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="fa45b-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="fa45b-117">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="fa45b-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fa45b-118">Provádění `FunctionLeave3WithInfo` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fa45b-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="fa45b-119">Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fa45b-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fa45b-120">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="fa45b-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="fa45b-121">`FunctionLeave3WithInfo` Funkce nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="fa45b-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa45b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa45b-122">Requirements</span></span>  
 <span data-ttu-id="fa45b-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa45b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa45b-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fa45b-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fa45b-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa45b-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fa45b-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fa45b-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa45b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa45b-127">See also</span></span>

- [<span data-ttu-id="fa45b-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="fa45b-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="fa45b-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fa45b-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="fa45b-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fa45b-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="fa45b-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fa45b-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="fa45b-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fa45b-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="fa45b-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fa45b-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="fa45b-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="fa45b-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="fa45b-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fa45b-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="fa45b-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="fa45b-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="fa45b-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="fa45b-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="fa45b-138">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="fa45b-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
