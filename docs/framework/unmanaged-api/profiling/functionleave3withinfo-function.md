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
ms.openlocfilehash: f7a945fb7ef10f995be2d779a88b98bbce2fdfb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866840"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="316cc-102">FunctionLeave3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="316cc-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="316cc-103">Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) pro načtení rámce zásobníku a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="316cc-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="316cc-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="316cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="316cc-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="316cc-106">\[in] identifikátor funkce, ze které je vrácen ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="316cc-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="316cc-107">\[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="316cc-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="316cc-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="316cc-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="316cc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="316cc-109">Remarks</span></span>  
 <span data-ttu-id="316cc-110">Metoda `FunctionLeave3WithInfo` zpětného volání oznámí profileru jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) ke kontrole návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="316cc-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="316cc-111">Chcete-li získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="316cc-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="316cc-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="316cc-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="316cc-113">Funkce `FunctionLeave3WithInfo` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="316cc-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="316cc-114">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="316cc-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="316cc-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="316cc-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="316cc-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="316cc-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="316cc-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="316cc-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="316cc-118">Implementace `FunctionLeave3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="316cc-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="316cc-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="316cc-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="316cc-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="316cc-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="316cc-121">Funkce `FunctionLeave3WithInfo` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="316cc-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="316cc-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="316cc-122">Requirements</span></span>  
 <span data-ttu-id="316cc-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="316cc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316cc-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="316cc-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="316cc-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="316cc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="316cc-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316cc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316cc-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="316cc-127">See also</span></span>

- [<span data-ttu-id="316cc-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="316cc-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="316cc-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="316cc-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="316cc-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="316cc-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="316cc-131">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="316cc-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="316cc-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="316cc-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="316cc-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="316cc-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="316cc-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="316cc-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="316cc-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="316cc-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="316cc-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="316cc-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="316cc-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="316cc-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="316cc-138">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="316cc-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
