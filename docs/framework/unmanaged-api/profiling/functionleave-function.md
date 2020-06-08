---
title: FunctionLeave – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 836e4843ead940bc9f76ff6bdd0433e21e400afd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500634"
---
# <a name="functionleave-function"></a><span data-ttu-id="a543a-102">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="a543a-102">FunctionLeave Function</span></span>
<span data-ttu-id="a543a-103">Upozorní profileru, že se chystá návrat funkce k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="a543a-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a543a-104">`FunctionLeave`Funkce je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a543a-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="a543a-105">Bude i nadále fungovat, ale dojde k snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a543a-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="a543a-106">Místo toho použijte funkci [FunctionLeave2 –](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a543a-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a543a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a543a-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a543a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a543a-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="a543a-109">\[in] identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="a543a-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="a543a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a543a-110">Remarks</span></span>  
 <span data-ttu-id="a543a-111">`FunctionLeave`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="a543a-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="a543a-112">Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().</span><span class="sxs-lookup"><span data-stu-id="a543a-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a543a-113">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="a543a-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a543a-114">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="a543a-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a543a-115">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="a543a-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a543a-116">Implementace `FunctionLeave` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a543a-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a543a-117">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a543a-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a543a-118">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionLeave` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a543a-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="a543a-119">`FunctionLeave`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="a543a-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a543a-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a543a-120">Requirements</span></span>  
 <span data-ttu-id="a543a-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a543a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a543a-122">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a543a-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a543a-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a543a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a543a-124">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="a543a-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a543a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a543a-125">See also</span></span>

- [<span data-ttu-id="a543a-126">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a543a-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="a543a-127">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a543a-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="a543a-128">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a543a-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="a543a-129">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a543a-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a543a-130">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="a543a-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
