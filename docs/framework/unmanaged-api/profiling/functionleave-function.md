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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 412a01dc1dd498c2f55307958e5feec36a556b9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586925"
---
# <a name="functionleave-function"></a><span data-ttu-id="9d2a5-102">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="9d2a5-102">FunctionLeave Function</span></span>
<span data-ttu-id="9d2a5-103">Oznámí profileru, že funkce se chystá vrácení volajícímu.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d2a5-104">`FunctionLeave` Funkce je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="9d2a5-105">Bude nadále fungovat, ale bude mít za následek snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="9d2a5-106">Použití [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2a5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d2a5-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d2a5-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d2a5-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="9d2a5-109">[in] Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d2a5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d2a5-110">Remarks</span></span>  
 <span data-ttu-id="9d2a5-111">`FunctionLeave` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="9d2a5-112">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="9d2a5-113">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="9d2a5-114">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="9d2a5-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="9d2a5-115">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9d2a5-116">Provádění `FunctionLeave` by neměla blokovat, protože způsobí zpoždění uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="9d2a5-117">Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9d2a5-118">Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave` vrátí.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="9d2a5-119">Také `FunctionLeave` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9d2a5-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2a5-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d2a5-120">Requirements</span></span>  
 <span data-ttu-id="9d2a5-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d2a5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d2a5-122">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9d2a5-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9d2a5-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d2a5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d2a5-124">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9d2a5-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2a5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d2a5-125">See also</span></span>

- [<span data-ttu-id="9d2a5-126">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9d2a5-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="9d2a5-127">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9d2a5-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="9d2a5-128">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9d2a5-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="9d2a5-129">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9d2a5-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="9d2a5-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9d2a5-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
