---
title: FunctionEnter – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be144ac8250adf803ddb1f20ea55be09cb3e81d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687385"
---
# <a name="functionenter-function"></a><span data-ttu-id="2de2b-102">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="2de2b-102">FunctionEnter Function</span></span>
<span data-ttu-id="2de2b-103">Oznámí profileru, že se ovládací prvek předán funkci.</span><span class="sxs-lookup"><span data-stu-id="2de2b-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2de2b-104">`FunctionEnter` Funkce je zastaralé v rozhraní .NET Framework verze 2.0 a jejich použití bude mít za následek snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2de2b-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="2de2b-105">Použití [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="2de2b-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de2b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2de2b-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2de2b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2de2b-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="2de2b-108">[in] Identifikátor funkce, do které se předá řízení.</span><span class="sxs-lookup"><span data-stu-id="2de2b-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2de2b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2de2b-109">Remarks</span></span>  
 <span data-ttu-id="2de2b-110">`FunctionEnter` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="2de2b-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="2de2b-111">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="2de2b-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="2de2b-112">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="2de2b-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="2de2b-113">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="2de2b-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="2de2b-114">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="2de2b-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2de2b-115">Provádění `FunctionEnter` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2de2b-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="2de2b-116">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2de2b-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2de2b-117">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionEnter` vrátí.</span><span class="sxs-lookup"><span data-stu-id="2de2b-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="2de2b-118">Také `FunctionEnter` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="2de2b-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2de2b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2de2b-119">Requirements</span></span>  
 <span data-ttu-id="2de2b-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2de2b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de2b-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2de2b-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2de2b-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2de2b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2de2b-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="2de2b-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de2b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2de2b-124">See also</span></span>
- [<span data-ttu-id="2de2b-125">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="2de2b-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="2de2b-126">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="2de2b-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="2de2b-127">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="2de2b-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="2de2b-128">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2de2b-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="2de2b-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2de2b-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
