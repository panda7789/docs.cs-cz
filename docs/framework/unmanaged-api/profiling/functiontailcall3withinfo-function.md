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
ms.openlocfilehash: 0aa43954c3e10d04524bf976d0dd3b29d2bc724c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866814"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="f82a4-102">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f82a4-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="f82a4-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) pro načtení rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82a4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f82a4-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f82a4-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="f82a4-106">\[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="f82a4-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="f82a4-107">\[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82a4-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f82a4-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="f82a4-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f82a4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f82a4-109">Remarks</span></span>  
 <span data-ttu-id="f82a4-110">Metoda `FunctionTailcall3WithInfo` zpětného volání oznámí profileru jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) ke kontrole rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82a4-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="f82a4-111">Chcete-li získat přístup k informacím o snímku zásobníku, je nutné nastavit příznak `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="f82a4-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="f82a4-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="f82a4-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f82a4-113">Funkce `FunctionTailcall3WithInfo` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="f82a4-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="f82a4-114">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="f82a4-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f82a4-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="f82a4-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f82a4-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="f82a4-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f82a4-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="f82a4-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f82a4-118">Implementace `FunctionTailcall3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f82a4-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f82a4-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f82a4-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f82a4-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionTailcall3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="f82a4-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="f82a4-121">Také funkce Functiontailcall3withinfo – nesmí volat do spravovaného kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="f82a4-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82a4-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f82a4-122">Requirements</span></span>  
 <span data-ttu-id="f82a4-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f82a4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82a4-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="f82a4-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f82a4-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f82a4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f82a4-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82a4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82a4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f82a4-127">See also</span></span>

- [<span data-ttu-id="f82a4-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f82a4-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="f82a4-129">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="f82a4-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="f82a4-130">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="f82a4-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f82a4-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f82a4-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f82a4-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f82a4-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="f82a4-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f82a4-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f82a4-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f82a4-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f82a4-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f82a4-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f82a4-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="f82a4-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f82a4-137">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f82a4-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
