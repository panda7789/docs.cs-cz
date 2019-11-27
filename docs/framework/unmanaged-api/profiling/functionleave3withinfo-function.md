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
ms.openlocfilehash: a62f402fbfae6188ab0423ea7a55a4dfc6cb4112
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427398"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="977b3-102">FunctionLeave3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="977b3-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="977b3-103">Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionLeave3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pro načtení rámce zásobníku a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="977b3-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="977b3-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="977b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="977b3-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="977b3-106">pro Identifikátor funkce, ze které je vrácen ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="977b3-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="977b3-107">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="977b3-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="977b3-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="977b3-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="977b3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="977b3-109">Remarks</span></span>  
 <span data-ttu-id="977b3-110">Metoda `FunctionLeave3WithInfo` zpětného volání oznámí profileru jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionLeave3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) ke kontrole návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="977b3-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="977b3-111">Chcete-li získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="977b3-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="977b3-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="977b3-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="977b3-113">Funkce `FunctionLeave3WithInfo` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="977b3-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="977b3-114">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="977b3-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="977b3-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="977b3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="977b3-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="977b3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="977b3-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="977b3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="977b3-118">Implementace `FunctionLeave3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="977b3-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="977b3-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="977b3-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="977b3-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="977b3-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="977b3-121">Funkce `FunctionLeave3WithInfo` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="977b3-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977b3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="977b3-122">Requirements</span></span>  
 <span data-ttu-id="977b3-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="977b3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977b3-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="977b3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="977b3-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="977b3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="977b3-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="977b3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977b3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="977b3-127">See also</span></span>

- [<span data-ttu-id="977b3-128">Getfunctionleave3info –</span><span class="sxs-lookup"><span data-stu-id="977b3-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="977b3-129">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="977b3-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="977b3-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="977b3-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="977b3-131">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="977b3-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="977b3-132">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="977b3-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="977b3-133">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="977b3-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="977b3-134">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="977b3-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="977b3-135">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="977b3-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="977b3-136">SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="977b3-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="977b3-137">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="977b3-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="977b3-138">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="977b3-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
