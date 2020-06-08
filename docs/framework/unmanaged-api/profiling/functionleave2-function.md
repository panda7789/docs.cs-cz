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
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500660"
---
# <a name="functionleave2-function"></a><span data-ttu-id="6d16c-102">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6d16c-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="6d16c-103">Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce.</span><span class="sxs-lookup"><span data-stu-id="6d16c-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d16c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d16c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d16c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d16c-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="6d16c-106">\[in] identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="6d16c-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="6d16c-107">\[in] identifikátor přemapované funkce, který profil dřív zadal přes funkci [FunctionIDMapper –](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6d16c-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="6d16c-108">\[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6d16c-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="6d16c-109">Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d16c-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="6d16c-110">\[in] ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , která určuje umístění paměti návratové hodnoty funkce.</span><span class="sxs-lookup"><span data-stu-id="6d16c-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="6d16c-111">Aby bylo možné získat přístup k informacím o vrácených hodnotách, `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="6d16c-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="6d16c-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.</span><span class="sxs-lookup"><span data-stu-id="6d16c-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d16c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d16c-113">Remarks</span></span>  
 <span data-ttu-id="6d16c-114">Hodnoty `func` `retvalRange` parametrů a nejsou platné poté, co `FunctionLeave2` funkce vrátí, protože hodnoty se mohou změnit nebo zničit.</span><span class="sxs-lookup"><span data-stu-id="6d16c-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="6d16c-115">`FunctionLeave2`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="6d16c-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="6d16c-116">Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().</span><span class="sxs-lookup"><span data-stu-id="6d16c-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="6d16c-117">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="6d16c-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6d16c-118">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="6d16c-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6d16c-119">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="6d16c-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6d16c-120">Implementace `FunctionLeave2` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6d16c-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="6d16c-121">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6d16c-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6d16c-122">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionLeave2` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="6d16c-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="6d16c-123">`FunctionLeave2`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="6d16c-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d16c-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d16c-124">Requirements</span></span>  
 <span data-ttu-id="6d16c-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d16c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d16c-126">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6d16c-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6d16c-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d16c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d16c-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d16c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d16c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d16c-129">See also</span></span>

- [<span data-ttu-id="6d16c-130">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6d16c-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="6d16c-131">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6d16c-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="6d16c-132">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6d16c-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="6d16c-133">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="6d16c-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
