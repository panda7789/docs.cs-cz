---
title: FunctionLeave3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 456d9a0e8236948ac69ed069495b1999ebf7e80a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500608"
---
# <a name="functionleave3-function"></a><span data-ttu-id="f129c-102">FunctionLeave3 – funkce</span><span class="sxs-lookup"><span data-stu-id="f129c-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="f129c-103">Upozorní profiler, že se vrací řízení z funkce.</span><span class="sxs-lookup"><span data-stu-id="f129c-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f129c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f129c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f129c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f129c-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="f129c-106">\[in] identifikátor funkce, ze které je vrácen ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f129c-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f129c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f129c-107">Remarks</span></span>  
 <span data-ttu-id="f129c-108">`FunctionLeave3`Funkce zpětného volání oznámí profileru jako volání funkcí, ale nepodporuje kontrolu návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="f129c-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="f129c-109">K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f129c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f129c-110">`FunctionLeave3`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="f129c-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="f129c-111">Implementace musí používat `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="f129c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f129c-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="f129c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f129c-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="f129c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f129c-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="f129c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f129c-115">Implementace `FunctionLeave3` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f129c-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f129c-116">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f129c-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f129c-117">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionLeave3` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="f129c-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="f129c-118">`FunctionLeave3`Funkce nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="f129c-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f129c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f129c-119">Requirements</span></span>  
 <span data-ttu-id="f129c-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f129c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f129c-121">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="f129c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f129c-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f129c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f129c-123">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f129c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f129c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f129c-124">See also</span></span>

- [<span data-ttu-id="f129c-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="f129c-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="f129c-126">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="f129c-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f129c-127">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f129c-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f129c-128">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f129c-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="f129c-129">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f129c-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f129c-130">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="f129c-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f129c-131">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="f129c-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f129c-132">SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="f129c-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f129c-133">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="f129c-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f129c-134">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="f129c-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
