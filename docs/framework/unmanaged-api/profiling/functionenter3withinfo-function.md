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
ms.openlocfilehash: 75a9a7174f105d99e9d1c9b220cfc5bf928d46ec
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866967"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="04272-102">FunctionEnter3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="04272-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="04272-103">Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) pro načtení rámce zásobníku a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="04272-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04272-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04272-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04272-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04272-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="04272-106">\[in] je identifikátor funkce, do které byl ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="04272-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="04272-107">\[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="04272-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="04272-108">Tento popisovač je platný pouze během zpětného volání, na které je předáno.</span><span class="sxs-lookup"><span data-stu-id="04272-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="04272-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04272-109">Remarks</span></span>  
 <span data-ttu-id="04272-110">Metoda `FunctionEnter3WithInfo` zpětného volání oznámí profileru jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="04272-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="04272-111">Chcete-li získat přístup k informacím o argumentech, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_ARGS`.</span><span class="sxs-lookup"><span data-stu-id="04272-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="04272-112">Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="04272-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="04272-113">Funkce `FunctionEnter3WithInfo` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="04272-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="04272-114">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="04272-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="04272-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="04272-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="04272-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="04272-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="04272-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="04272-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="04272-118">Implementace `FunctionEnter3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="04272-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="04272-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="04272-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="04272-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionEnter3WithInfo` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="04272-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="04272-121">Funkce `FunctionEnter3WithInfo` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="04272-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04272-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04272-122">Requirements</span></span>  
 <span data-ttu-id="04272-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04272-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04272-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="04272-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="04272-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04272-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04272-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04272-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04272-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04272-127">See also</span></span>

- [<span data-ttu-id="04272-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="04272-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="04272-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="04272-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="04272-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="04272-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="04272-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="04272-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
