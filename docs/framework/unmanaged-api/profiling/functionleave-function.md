---
title: "FunctionLeave – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3368a97adf6ffceaa5ac56b7ffe16d6e2802437c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave-function"></a><span data-ttu-id="48436-102">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="48436-102">FunctionLeave Function</span></span>
<span data-ttu-id="48436-103">Upozorní profileru, že funkce je se vraťte na volajícího.</span><span class="sxs-lookup"><span data-stu-id="48436-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48436-104">`FunctionLeave` Funkce je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="48436-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="48436-105">Bude nadále fungovat, ale bude způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="48436-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="48436-106">Použití [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="48436-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48436-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48436-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48436-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="48436-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="48436-109">[v] Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="48436-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48436-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48436-110">Remarks</span></span>  
 <span data-ttu-id="48436-111">`FunctionLeave` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="48436-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="48436-112">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="48436-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="48436-113">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="48436-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="48436-114">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="48436-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="48436-115">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="48436-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="48436-116">Implementace `FunctionLeave` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="48436-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="48436-117">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="48436-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="48436-118">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave` vrátí.</span><span class="sxs-lookup"><span data-stu-id="48436-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="48436-119">Navíc `FunctionLeave` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="48436-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48436-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48436-120">Requirements</span></span>  
 <span data-ttu-id="48436-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48436-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48436-122">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="48436-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="48436-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48436-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48436-124">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="48436-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48436-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="48436-125">See Also</span></span>  
 [<span data-ttu-id="48436-126">Functionenter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="48436-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="48436-127">Functionleave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="48436-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="48436-128">Functiontailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="48436-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="48436-129">Setenterleavefunctionhooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="48436-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="48436-130">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="48436-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
