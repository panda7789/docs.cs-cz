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
ms.openlocfilehash: 979b3401cbf13761bc5b58b4d8734dfa5e83ec49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586767"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="f948b-102">FunctionTailcall3 – funkce</span><span class="sxs-lookup"><span data-stu-id="f948b-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="f948b-103">Oznámí profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="f948b-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f948b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f948b-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f948b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f948b-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="f948b-106">[in] Identifikátor aktuálně prováděné funkci, která se chystá provést tail volání.</span><span class="sxs-lookup"><span data-stu-id="f948b-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f948b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f948b-107">Remarks</span></span>  
 <span data-ttu-id="f948b-108">`FunctionTailcall3` Funkce zpětného volání oznámí profileru, jako jsou funkce volány.</span><span class="sxs-lookup"><span data-stu-id="f948b-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="f948b-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaši implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="f948b-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f948b-110">`FunctionTailcall3` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="f948b-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="f948b-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="f948b-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f948b-112">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="f948b-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f948b-113">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="f948b-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f948b-114">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="f948b-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f948b-115">Provádění `FunctionTailcall3` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f948b-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f948b-116">Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f948b-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f948b-117">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionTailcall3` vrátí.</span><span class="sxs-lookup"><span data-stu-id="f948b-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="f948b-118">`FunctionTailcall3` Funkce nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f948b-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f948b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f948b-119">Requirements</span></span>  
 <span data-ttu-id="f948b-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f948b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f948b-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f948b-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f948b-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f948b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f948b-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f948b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f948b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f948b-124">See also</span></span>

- [<span data-ttu-id="f948b-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f948b-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="f948b-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f948b-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="f948b-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f948b-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="f948b-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f948b-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="f948b-129">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f948b-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f948b-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f948b-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f948b-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f948b-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f948b-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f948b-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f948b-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="f948b-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f948b-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f948b-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
