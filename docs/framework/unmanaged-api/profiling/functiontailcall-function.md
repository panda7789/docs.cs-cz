---
title: FunctionTailcall – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03b49f4da8c9dd9ad02549f3836a841535bf1f74
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502420"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="d74a5-102">FunctionTailcall – funkce</span><span class="sxs-lookup"><span data-stu-id="d74a5-102">FunctionTailcall Function</span></span>
<span data-ttu-id="d74a5-103">Oznámí profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="d74a5-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d74a5-104">`FunctionTailcall` Funkce je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d74a5-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d74a5-105">Bude nadále fungovat, ale bude mít za následek snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="d74a5-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="d74a5-106">Použití [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="d74a5-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d74a5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d74a5-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d74a5-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="d74a5-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="d74a5-109">[in] Identifikátor aktuálně prováděné funkci, která se chystá provést tail volání.</span><span class="sxs-lookup"><span data-stu-id="d74a5-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d74a5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d74a5-110">Remarks</span></span>  
 <span data-ttu-id="d74a5-111">Cílová funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volajícího, který vytvořil tail volání funkce.</span><span class="sxs-lookup"><span data-stu-id="d74a5-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="d74a5-112">To znamená, že [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="d74a5-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="d74a5-113">`FunctionTailcall` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="d74a5-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="d74a5-114">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="d74a5-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d74a5-115">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="d74a5-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="d74a5-116">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="d74a5-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="d74a5-117">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="d74a5-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d74a5-118">Provádění `FunctionTailcall` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d74a5-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d74a5-119">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d74a5-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d74a5-120">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionTailcall` vrátí.</span><span class="sxs-lookup"><span data-stu-id="d74a5-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="d74a5-121">Také `FunctionTailcall` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="d74a5-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74a5-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d74a5-122">Requirements</span></span>  
 <span data-ttu-id="d74a5-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d74a5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74a5-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d74a5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d74a5-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d74a5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d74a5-126">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="d74a5-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74a5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d74a5-127">See also</span></span>
- [<span data-ttu-id="d74a5-128">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="d74a5-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="d74a5-129">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="d74a5-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="d74a5-130">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d74a5-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="d74a5-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d74a5-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
