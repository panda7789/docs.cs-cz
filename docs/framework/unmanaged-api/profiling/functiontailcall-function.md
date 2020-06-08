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
ms.openlocfilehash: 42ea497bdcab71518bec08514b827d76f0317d57
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500595"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="5cc02-102">FunctionTailcall – funkce</span><span class="sxs-lookup"><span data-stu-id="5cc02-102">FunctionTailcall Function</span></span>
<span data-ttu-id="5cc02-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="5cc02-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cc02-104">`FunctionTailcall`Funkce je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="5cc02-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5cc02-105">Bude i nadále fungovat, ale dojde k snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5cc02-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="5cc02-106">Místo toho použijte funkci [FunctionTailcall2 –](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5cc02-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc02-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cc02-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cc02-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cc02-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="5cc02-109">\[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="5cc02-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cc02-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cc02-110">Remarks</span></span>  
 <span data-ttu-id="5cc02-111">Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="5cc02-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="5cc02-112">To znamená, že zpětné volání [FunctionLeave –](functionleave-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="5cc02-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="5cc02-113">`FunctionTailcall`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="5cc02-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="5cc02-114">Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().</span><span class="sxs-lookup"><span data-stu-id="5cc02-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="5cc02-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="5cc02-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="5cc02-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="5cc02-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="5cc02-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="5cc02-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5cc02-118">Implementace `FunctionTailcall` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5cc02-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="5cc02-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5cc02-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5cc02-120">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="5cc02-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="5cc02-121">`FunctionTailcall`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="5cc02-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc02-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cc02-122">Requirements</span></span>  
 <span data-ttu-id="5cc02-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc02-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc02-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="5cc02-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5cc02-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5cc02-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cc02-126">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="5cc02-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc02-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cc02-127">See also</span></span>

- [<span data-ttu-id="5cc02-128">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5cc02-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="5cc02-129">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5cc02-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="5cc02-130">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5cc02-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="5cc02-131">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="5cc02-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
