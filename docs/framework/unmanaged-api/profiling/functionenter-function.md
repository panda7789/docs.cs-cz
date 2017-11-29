---
title: "FunctionEnter – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="5f839-102">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="5f839-102">FunctionEnter Function</span></span>
<span data-ttu-id="5f839-103">Upozorní profileru, že se ovládací prvek předán do funkce.</span><span class="sxs-lookup"><span data-stu-id="5f839-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f839-104">`FunctionEnter` Funkce je zastaralé v rozhraní .NET Framework verze 2.0 a jeho použití je zpoplatněná snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5f839-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="5f839-105">Použití [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="5f839-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f839-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f839-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f839-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f839-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="5f839-108">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5f839-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f839-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f839-109">Remarks</span></span>  
 <span data-ttu-id="5f839-110">`FunctionEnter` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="5f839-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="5f839-111">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="5f839-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="5f839-112">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="5f839-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="5f839-113">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="5f839-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="5f839-114">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="5f839-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5f839-115">Implementace `FunctionEnter` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5f839-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="5f839-116">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="5f839-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5f839-117">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter` vrátí.</span><span class="sxs-lookup"><span data-stu-id="5f839-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="5f839-118">Navíc `FunctionEnter` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="5f839-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f839-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f839-119">Requirements</span></span>  
 <span data-ttu-id="5f839-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f839-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f839-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5f839-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5f839-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f839-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f839-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="5f839-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f839-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f839-124">See Also</span></span>  
 [<span data-ttu-id="5f839-125">Functionenter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5f839-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="5f839-126">Functionleave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5f839-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="5f839-127">Functiontailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5f839-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="5f839-128">Setenterleavefunctionhooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5f839-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="5f839-129">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="5f839-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
