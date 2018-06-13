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
ms.openlocfilehash: 77de59de8fcf3797237245ce42c7f0eaa96d3d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451779"
---
# <a name="functionenter-function"></a><span data-ttu-id="6c24f-102">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="6c24f-102">FunctionEnter Function</span></span>
<span data-ttu-id="6c24f-103">Upozorní profileru, že se ovládací prvek předán do funkce.</span><span class="sxs-lookup"><span data-stu-id="6c24f-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c24f-104">`FunctionEnter` Funkce je zastaralé v rozhraní .NET Framework verze 2.0 a jeho použití je zpoplatněná snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="6c24f-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="6c24f-105">Použití [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="6c24f-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c24f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c24f-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c24f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c24f-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="6c24f-108">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6c24f-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c24f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c24f-109">Remarks</span></span>  
 <span data-ttu-id="6c24f-110">`FunctionEnter` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="6c24f-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="6c24f-111">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="6c24f-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="6c24f-112">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="6c24f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="6c24f-113">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="6c24f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="6c24f-114">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="6c24f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6c24f-115">Implementace `FunctionEnter` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6c24f-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="6c24f-116">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="6c24f-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6c24f-117">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter` vrátí.</span><span class="sxs-lookup"><span data-stu-id="6c24f-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="6c24f-118">Navíc `FunctionEnter` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="6c24f-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c24f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c24f-119">Requirements</span></span>  
 <span data-ttu-id="6c24f-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c24f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c24f-121">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6c24f-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6c24f-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c24f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c24f-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="6c24f-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c24f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c24f-124">See Also</span></span>  
 [<span data-ttu-id="6c24f-125">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6c24f-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="6c24f-126">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6c24f-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="6c24f-127">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6c24f-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="6c24f-128">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6c24f-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="6c24f-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6c24f-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
