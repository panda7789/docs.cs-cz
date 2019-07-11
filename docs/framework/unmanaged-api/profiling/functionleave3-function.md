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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27b2241f7eb0e1ce8b0728a54028f9b4a6112e36
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781254"
---
# <a name="functionleave3-function"></a><span data-ttu-id="7cd0f-102">FunctionLeave3 – funkce</span><span class="sxs-lookup"><span data-stu-id="7cd0f-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="7cd0f-103">Oznámí profileru, že se řízení vrací z funkce.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cd0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cd0f-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cd0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cd0f-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="7cd0f-106">[in] Identifikátor funkce, ve kterém ovládací prvek se vrátí.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cd0f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cd0f-107">Remarks</span></span>  
 <span data-ttu-id="7cd0f-108">`FunctionLeave3` Funkce zpětného volání oznámí profileru jako funkce je volána, ale nepodporuje kontrolu návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="7cd0f-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaši implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7cd0f-110">`FunctionLeave3` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="7cd0f-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7cd0f-112">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7cd0f-113">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="7cd0f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7cd0f-114">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7cd0f-115">Provádění `FunctionLeave3` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7cd0f-116">Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7cd0f-117">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave3` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="7cd0f-118">`FunctionLeave3` Funkce nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7cd0f-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cd0f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cd0f-119">Requirements</span></span>  
 <span data-ttu-id="7cd0f-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cd0f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cd0f-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7cd0f-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7cd0f-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cd0f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cd0f-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cd0f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd0f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cd0f-124">See also</span></span>

- [<span data-ttu-id="7cd0f-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="7cd0f-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="7cd0f-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7cd0f-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="7cd0f-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7cd0f-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="7cd0f-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7cd0f-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="7cd0f-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7cd0f-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7cd0f-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7cd0f-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="7cd0f-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7cd0f-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="7cd0f-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7cd0f-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7cd0f-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7cd0f-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="7cd0f-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7cd0f-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
