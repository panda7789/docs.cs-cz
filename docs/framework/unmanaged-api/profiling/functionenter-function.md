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
ms.openlocfilehash: caea1d3d526017c0118f95bb138ee4ac45d2c137
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866993"
---
# <a name="functionenter-function"></a><span data-ttu-id="d4dea-102">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="d4dea-102">FunctionEnter Function</span></span>
<span data-ttu-id="d4dea-103">Upozorňuje profileru, že řízení je předáno funkci.</span><span class="sxs-lookup"><span data-stu-id="d4dea-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4dea-104">Funkce `FunctionEnter` je v .NET Framework verze 2,0 zastaralá a její použití bude mít za následek snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="d4dea-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="d4dea-105">Místo toho použijte funkci [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d4dea-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4dea-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4dea-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4dea-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4dea-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="d4dea-108">\[in] je identifikátor funkce, do které byl ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="d4dea-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4dea-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4dea-109">Remarks</span></span>  
 <span data-ttu-id="d4dea-110">Funkce `FunctionEnter` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="d4dea-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="d4dea-111">Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="d4dea-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d4dea-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="d4dea-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d4dea-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="d4dea-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d4dea-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="d4dea-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d4dea-115">Implementace `FunctionEnter` by neměla zablokovat, protože bude odloženo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4dea-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d4dea-116">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4dea-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d4dea-117">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionEnter` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="d4dea-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="d4dea-118">Také funkce `FunctionEnter` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="d4dea-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4dea-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4dea-119">Requirements</span></span>  
 <span data-ttu-id="d4dea-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4dea-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4dea-121">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d4dea-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d4dea-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4dea-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4dea-123">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d4dea-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4dea-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4dea-124">See also</span></span>

- [<span data-ttu-id="d4dea-125">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="d4dea-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d4dea-126">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="d4dea-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="d4dea-127">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="d4dea-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="d4dea-128">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d4dea-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="d4dea-129">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d4dea-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
