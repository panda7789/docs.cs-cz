---
title: FunctionEnter3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e086f54865307e116a9e522b2fbadee8502249
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105667"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="5bb2d-102">FunctionEnter3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="5bb2d-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="5bb2d-103">Oznámí profileru, že ovládací prvek je předáván funkci a poskytuje popisovač, který lze předat [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) načíst zásobník snímků a funkce argumenty.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2d-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bb2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bb2d-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="5bb2d-106">[in] Identifikátor funkce, do které se předá řízení.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="5bb2d-107">[in] Neprůhledný popisovač, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="5bb2d-108">Tento popisovač je platný pouze během zpětného volání, který je předán.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bb2d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bb2d-109">Remarks</span></span>  
 <span data-ttu-id="5bb2d-110">`FunctionEnter3WithInfo` Metoda zpětného volání oznámí profileru a funkce jsou volány umožňuje profileru pomocí [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnoty argumentů.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="5bb2d-111">Přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="5bb2d-112">Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí, a pak používat [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vašeho implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="5bb2d-113">`FunctionEnter3WithInfo` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="5bb2d-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="5bb2d-115">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="5bb2d-116">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="5bb2d-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="5bb2d-117">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5bb2d-118">Provádění `FunctionEnter3WithInfo` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="5bb2d-119">Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5bb2d-120">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionEnter3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="5bb2d-121">`FunctionEnter3WithInfo` Funkce nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bb2d-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bb2d-122">Requirements</span></span>  
 <span data-ttu-id="5bb2d-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bb2d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bb2d-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5bb2d-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5bb2d-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bb2d-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5bb2d-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5bb2d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5bb2d-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bb2d-127">See also</span></span>

- [<span data-ttu-id="5bb2d-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="5bb2d-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="5bb2d-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="5bb2d-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="5bb2d-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="5bb2d-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="5bb2d-131">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="5bb2d-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
