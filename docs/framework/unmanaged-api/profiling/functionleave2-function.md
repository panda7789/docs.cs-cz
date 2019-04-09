---
title: FunctionLeave2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3efee2e2b595f1e0d9116dcac3fdaa99aa4659d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192761"
---
# <a name="functionleave2-function"></a><span data-ttu-id="ebf5c-102">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ebf5c-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="ebf5c-103">Profiler upozorní, že funkce je vracet volajícímu a poskytuje informace o zásobníku rámce a funkce návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebf5c-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebf5c-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="ebf5c-106">[in] Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="ebf5c-107">[in] Identifikátor změnu mapování funkce, který dříve zadaný profiler přes [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="ebf5c-108">[in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="ebf5c-109">Profiler by měl považovat za to neprůhledného popisovače, který může být předán zpět prováděcí modul v [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="ebf5c-110">[in] Ukazatel [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktura, která určuje umístění v paměti návratové hodnoty funkce.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="ebf5c-111">Aby bylo možné získat přístup k informacím návratová hodnota `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="ebf5c-112">Profiler může použít [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebf5c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebf5c-113">Remarks</span></span>  
 <span data-ttu-id="ebf5c-114">Hodnoty `func` a `retvalRange` parametry jsou neplatné po `FunctionLeave2` funkce vrátí hodnoty se mohou změnit nebo zničení.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="ebf5c-115">`FunctionLeave2` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="ebf5c-116">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="ebf5c-117">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="ebf5c-118">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="ebf5c-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="ebf5c-119">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ebf5c-120">Provádění `FunctionLeave2` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="ebf5c-121">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ebf5c-122">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="ebf5c-123">Také `FunctionLeave2` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="ebf5c-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf5c-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebf5c-124">Requirements</span></span>  
 <span data-ttu-id="ebf5c-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf5c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf5c-126">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ebf5c-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ebf5c-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf5c-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ebf5c-128">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ebf5c-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ebf5c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebf5c-129">See also</span></span>

- [<span data-ttu-id="ebf5c-130">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ebf5c-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="ebf5c-131">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ebf5c-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="ebf5c-132">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ebf5c-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="ebf5c-133">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="ebf5c-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
