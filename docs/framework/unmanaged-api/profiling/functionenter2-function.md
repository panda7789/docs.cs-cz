---
title: FunctionEnter2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825da3a09f8b8013ffecaedfee0dce2362c8a7b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227805"
---
# <a name="functionenter2-function"></a><span data-ttu-id="fee2d-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="fee2d-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="fee2d-103">Profiler upozorní, že ovládací prvek je předáván funkci a poskytuje informace o zásobníku rámce a funkce argumenty.</span><span class="sxs-lookup"><span data-stu-id="fee2d-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="fee2d-104">Tato funkce nahrazuje [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fee2d-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fee2d-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fee2d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fee2d-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="fee2d-107">[in] Identifikátor funkce, do které se předá řízení.</span><span class="sxs-lookup"><span data-stu-id="fee2d-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="fee2d-108">[in] Identifikátor změnu mapování funkce, který dříve zadanou profileru pomocí [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fee2d-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="fee2d-109">[in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fee2d-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="fee2d-110">Profiler by měl považovat za to neprůhledného popisovače, který může být předán zpět prováděcí modul v [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fee2d-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="fee2d-111">[in] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která určuje umístění v paměti argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="fee2d-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="fee2d-112">Aby bylo možné přistupovat k informací o argumentech, `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="fee2d-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="fee2d-113">Profiler může použít [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="fee2d-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fee2d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fee2d-114">Remarks</span></span>  
 <span data-ttu-id="fee2d-115">Hodnoty `func` a `argumentInfo` parametry jsou neplatné po `FunctionEnter2` funkce vrátí hodnoty se mohou změnit nebo zničení.</span><span class="sxs-lookup"><span data-stu-id="fee2d-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="fee2d-116">`FunctionEnter2` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="fee2d-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="fee2d-117">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="fee2d-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="fee2d-118">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="fee2d-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="fee2d-119">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="fee2d-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="fee2d-120">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="fee2d-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fee2d-121">Provádění `FunctionEnter2` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fee2d-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="fee2d-122">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fee2d-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fee2d-123">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionEnter2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="fee2d-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="fee2d-124">Také `FunctionEnter2` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="fee2d-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee2d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fee2d-125">Requirements</span></span>  
 <span data-ttu-id="fee2d-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee2d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee2d-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fee2d-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fee2d-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee2d-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fee2d-129">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fee2d-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fee2d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fee2d-130">See also</span></span>

- [<span data-ttu-id="fee2d-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="fee2d-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="fee2d-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="fee2d-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="fee2d-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fee2d-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="fee2d-134">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="fee2d-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
