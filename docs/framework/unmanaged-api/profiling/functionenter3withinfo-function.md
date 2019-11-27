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
ms.openlocfilehash: 86b1c8b3f5bd88b216c59f5cc6846f83f3c094ee
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440748"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="a210b-102">FunctionEnter3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="a210b-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="a210b-103">Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionEnter3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pro načtení rámce zásobníku a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="a210b-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a210b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a210b-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a210b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a210b-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="a210b-106">pro Identifikátor funkce, do které je ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="a210b-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a210b-107">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a210b-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a210b-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="a210b-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a210b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a210b-109">Remarks</span></span>  
 <span data-ttu-id="a210b-110">Metoda `FunctionEnter3WithInfo` zpětného volání oznámí profileru jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionEnter3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="a210b-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="a210b-111">Chcete-li získat přístup k informacím o argumentech, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_ARGS`.</span><span class="sxs-lookup"><span data-stu-id="a210b-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="a210b-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="a210b-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a210b-113">Funkce `FunctionEnter3WithInfo` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="a210b-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="a210b-114">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="a210b-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a210b-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="a210b-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a210b-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="a210b-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a210b-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="a210b-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a210b-118">Implementace `FunctionEnter3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a210b-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a210b-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a210b-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a210b-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionEnter3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a210b-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="a210b-121">Funkce `FunctionEnter3WithInfo` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="a210b-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a210b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a210b-122">Requirements</span></span>  
 <span data-ttu-id="a210b-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a210b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a210b-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a210b-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a210b-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a210b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a210b-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a210b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a210b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a210b-127">See also</span></span>

- [<span data-ttu-id="a210b-128">Getfunctionenter3info –</span><span class="sxs-lookup"><span data-stu-id="a210b-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="a210b-129">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="a210b-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="a210b-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="a210b-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="a210b-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a210b-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
