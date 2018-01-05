---
title: "FunctionLeave3 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3
helpviewer_keywords: FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 689de7f7a9ac370f20941dea57edd7b7224410af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave3-function"></a><span data-ttu-id="d5685-102">FunctionLeave3 – funkce</span><span class="sxs-lookup"><span data-stu-id="d5685-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="d5685-103">Upozorní profileru, že se vrací ovládací prvek z funkce.</span><span class="sxs-lookup"><span data-stu-id="d5685-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5685-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5685-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5685-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5685-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="d5685-106">[v] Identifikátor funkce, ze kterého se vrátí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d5685-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5685-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5685-107">Remarks</span></span>  
 <span data-ttu-id="d5685-108">`FunctionLeave3` Funkce zpětného volání upozorní profileru, jako jsou volaná funkce, ale nepodporuje kontroly návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5685-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="d5685-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="d5685-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d5685-110">`FunctionLeave3` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="d5685-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="d5685-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="d5685-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="d5685-112">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="d5685-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="d5685-113">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="d5685-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="d5685-114">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="d5685-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d5685-115">Implementace `FunctionLeave3` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d5685-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="d5685-116">Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="d5685-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d5685-117">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave3` vrátí.</span><span class="sxs-lookup"><span data-stu-id="d5685-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="d5685-118">`FunctionLeave3` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d5685-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5685-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5685-119">Requirements</span></span>  
 <span data-ttu-id="d5685-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5685-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5685-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d5685-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d5685-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5685-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5685-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5685-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5685-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5685-124">See Also</span></span>  
 [<span data-ttu-id="d5685-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="d5685-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="d5685-126">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="d5685-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="d5685-127">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5685-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="d5685-128">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5685-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="d5685-129">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5685-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="d5685-130">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="d5685-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="d5685-131">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="d5685-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="d5685-132">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="d5685-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="d5685-133">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="d5685-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="d5685-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5685-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
