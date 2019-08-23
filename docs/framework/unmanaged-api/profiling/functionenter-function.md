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
ms.openlocfilehash: 354736890a4b042a8da5e747a0ab6ea3777e398e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952907"
---
# <a name="functionenter-function"></a><span data-ttu-id="eb6c3-102">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="eb6c3-102">FunctionEnter Function</span></span>
<span data-ttu-id="eb6c3-103">Upozorňuje profileru, že řízení je předáno funkci.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb6c3-104">`FunctionEnter` Funkce je zastaralá ve verzi .NET Framework 2,0 a její použití bude mít za následek snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="eb6c3-105">Místo toho použijte funkci [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="eb6c3-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb6c3-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb6c3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb6c3-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="eb6c3-108">pro Identifikátor funkce, do které je ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb6c3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb6c3-109">Remarks</span></span>  
 <span data-ttu-id="eb6c3-110">`FunctionEnter` Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="eb6c3-111">Implementace musí používat `__declspec`atribut třídy úložiště`naked`().</span><span class="sxs-lookup"><span data-stu-id="eb6c3-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="eb6c3-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="eb6c3-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="eb6c3-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="eb6c3-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="eb6c3-115">Implementace `FunctionEnter` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="eb6c3-116">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="eb6c3-117">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud `FunctionEnter` se nevrátí.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="eb6c3-118">`FunctionEnter` Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="eb6c3-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb6c3-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb6c3-119">Requirements</span></span>  
 <span data-ttu-id="eb6c3-120">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb6c3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6c3-121">**Hlaviček** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="eb6c3-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="eb6c3-122">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb6c3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb6c3-123">**Verze .NET Framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="eb6c3-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6c3-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb6c3-124">See also</span></span>

- [<span data-ttu-id="eb6c3-125">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="eb6c3-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="eb6c3-126">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="eb6c3-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="eb6c3-127">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="eb6c3-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="eb6c3-128">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eb6c3-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="eb6c3-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="eb6c3-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
