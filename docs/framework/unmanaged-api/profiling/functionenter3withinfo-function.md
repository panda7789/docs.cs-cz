---
title: "FunctionEnter3WithInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 848ef06f73aa0cce5d6991a7a59a8ce51ab1745a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="7b662-102">FunctionEnter3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="7b662-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="7b662-103">Profileru upozorní, že se ovládací prvek předán do funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) k načtení argumentů rámec a funkce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b662-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b662-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b662-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b662-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b662-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="7b662-106">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7b662-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7b662-107">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b662-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7b662-108">Tento popisovač je platný pouze během zpětného volání, ke kterému je předán.</span><span class="sxs-lookup"><span data-stu-id="7b662-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b662-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b662-109">Remarks</span></span>  
 <span data-ttu-id="7b662-110">`FunctionEnter3WithInfo` Metoda zpětného volání upozorní profileru jako funkce se nazývají a umožňuje profileru používat [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="7b662-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="7b662-111">Pro přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` příznak musí být nastavena.</span><span class="sxs-lookup"><span data-stu-id="7b662-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="7b662-112">Můžete použít profileru [icorprofilerinfo::seteventmask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavte příznaky událostí, a pak použít [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="7b662-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7b662-113">`FunctionEnter3WithInfo` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="7b662-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="7b662-114">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b662-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7b662-115">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="7b662-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="7b662-116">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="7b662-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="7b662-117">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="7b662-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7b662-118">Implementace `FunctionEnter3WithInfo` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7b662-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7b662-119">Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="7b662-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7b662-120">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter3WithInfo` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7b662-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="7b662-121">`FunctionEnter3WithInfo` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7b662-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b662-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b662-122">Requirements</span></span>  
 <span data-ttu-id="7b662-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b662-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b662-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7b662-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7b662-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b662-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b662-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b662-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b662-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b662-127">See Also</span></span>  
 [<span data-ttu-id="7b662-128">Getfunctionenter3info –</span><span class="sxs-lookup"><span data-stu-id="7b662-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="7b662-129">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="7b662-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="7b662-130">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="7b662-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="7b662-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7b662-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
