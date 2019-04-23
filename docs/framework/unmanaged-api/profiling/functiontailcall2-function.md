---
title: FunctionTailcall2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06dd3b028f4f43ca8681c80a5caa4716104068dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080888"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="4749e-102">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="4749e-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="4749e-103">Profiler upozorní, že aktuálně prováděné funkci je provést volání funkce tail do jiné funkce a poskytuje informace o zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4749e-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4749e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4749e-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4749e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4749e-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="4749e-106">[in] Identifikátor aktuálně prováděné funkci, která se chystá provést tail volání.</span><span class="sxs-lookup"><span data-stu-id="4749e-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="4749e-107">[in] Identifikátor změnu mapování funkce, který dříve zadaný profiler přes [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), aktuálně prováděné funkce, která se chystá provést tail volání.</span><span class="sxs-lookup"><span data-stu-id="4749e-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="4749e-108">[in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4749e-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="4749e-109">Profiler by měl považovat za to neprůhledného popisovače, který může být předán zpět prováděcí modul v [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4749e-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4749e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4749e-110">Remarks</span></span>  
 <span data-ttu-id="4749e-111">Cílová funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volajícího, který vytvořil tail volání funkce.</span><span class="sxs-lookup"><span data-stu-id="4749e-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="4749e-112">To znamená, že [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="4749e-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="4749e-113">Hodnota `func` parametr není platný po `FunctionTailcall2` funkce vrátí, protože se může změnit hodnotu nebo zničení.</span><span class="sxs-lookup"><span data-stu-id="4749e-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="4749e-114">`FunctionTailcall2` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="4749e-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="4749e-115">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="4749e-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="4749e-116">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="4749e-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="4749e-117">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="4749e-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="4749e-118">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="4749e-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4749e-119">Provádění `FunctionTailcall2` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="4749e-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="4749e-120">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="4749e-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4749e-121">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionTailcall2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="4749e-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="4749e-122">Také `FunctionTailcall2` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="4749e-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4749e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4749e-123">Requirements</span></span>  
 <span data-ttu-id="4749e-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4749e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4749e-125">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4749e-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4749e-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4749e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4749e-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4749e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4749e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4749e-128">See also</span></span>

- [<span data-ttu-id="4749e-129">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="4749e-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="4749e-130">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="4749e-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="4749e-131">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4749e-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="4749e-132">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4749e-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
