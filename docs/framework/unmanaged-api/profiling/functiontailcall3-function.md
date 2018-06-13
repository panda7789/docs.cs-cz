---
title: FunctionTailcall3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82d718c6f6aee36f3a916eb7f9b9a1e0b3b46cb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452465"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="012af-102">FunctionTailcall3 – funkce</span><span class="sxs-lookup"><span data-stu-id="012af-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="012af-103">Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="012af-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="012af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="012af-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="012af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="012af-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="012af-106">[v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.</span><span class="sxs-lookup"><span data-stu-id="012af-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="012af-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="012af-107">Remarks</span></span>  
 <span data-ttu-id="012af-108">`FunctionTailcall3` Funkce zpětného volání upozorní profileru, jako jsou volaná funkce.</span><span class="sxs-lookup"><span data-stu-id="012af-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="012af-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="012af-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="012af-110">`FunctionTailcall3` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="012af-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="012af-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="012af-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="012af-112">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="012af-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="012af-113">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="012af-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="012af-114">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="012af-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="012af-115">Implementace `FunctionTailcall3` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="012af-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="012af-116">Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="012af-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="012af-117">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall3` vrátí.</span><span class="sxs-lookup"><span data-stu-id="012af-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="012af-118">`FunctionTailcall3` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="012af-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="012af-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="012af-119">Requirements</span></span>  
 <span data-ttu-id="012af-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="012af-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="012af-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="012af-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="012af-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="012af-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="012af-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="012af-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012af-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="012af-124">See Also</span></span>  
 [<span data-ttu-id="012af-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="012af-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="012af-126">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="012af-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="012af-127">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="012af-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="012af-128">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="012af-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="012af-129">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="012af-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="012af-130">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="012af-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="012af-131">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="012af-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="012af-132">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="012af-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="012af-133">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="012af-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="012af-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="012af-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
