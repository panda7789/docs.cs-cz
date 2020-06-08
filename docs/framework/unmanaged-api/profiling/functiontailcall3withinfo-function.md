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
ms.openlocfilehash: f076044b44859cc39d90be528ee6648f5eaa626c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500582"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="bf376-102">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="bf376-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="bf376-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) pro načtení rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf376-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf376-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf376-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf376-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf376-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="bf376-106">\[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="bf376-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="bf376-107">\[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf376-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="bf376-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="bf376-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf376-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf376-109">Remarks</span></span>  
 <span data-ttu-id="bf376-110">`FunctionTailcall3WithInfo`Metoda zpětného volání upozorní Profiler jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) ke kontrole rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf376-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="bf376-111">Chcete-li získat přístup k informacím o snímku zásobníku, je `COR_PRF_ENABLE_FRAME_INFO` nutné nastavit příznak.</span><span class="sxs-lookup"><span data-stu-id="bf376-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="bf376-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="bf376-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bf376-113">`FunctionTailcall3WithInfo`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="bf376-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="bf376-114">Implementace musí používat `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="bf376-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="bf376-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="bf376-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bf376-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="bf376-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bf376-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="bf376-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bf376-118">Implementace `FunctionTailcall3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bf376-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="bf376-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bf376-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bf376-120">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="bf376-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="bf376-121">Také funkce Functiontailcall3withinfo – nesmí volat do spravovaného kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="bf376-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf376-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf376-122">Requirements</span></span>  
 <span data-ttu-id="bf376-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf376-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf376-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="bf376-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bf376-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bf376-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf376-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf376-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf376-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf376-127">See also</span></span>

- [<span data-ttu-id="bf376-128">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="bf376-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="bf376-129">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="bf376-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="bf376-130">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="bf376-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="bf376-131">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="bf376-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="bf376-132">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="bf376-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="bf376-133">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="bf376-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="bf376-134">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="bf376-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="bf376-135">SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="bf376-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="bf376-136">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="bf376-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="bf376-137">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="bf376-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
