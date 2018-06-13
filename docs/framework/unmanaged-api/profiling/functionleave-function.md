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
ms.openlocfilehash: 2614ad988496a22f0e6234c2f3300e22ef548308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452439"
---
# <a name="functionleave-function"></a><span data-ttu-id="a47b9-102">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="a47b9-102">FunctionLeave Function</span></span>
<span data-ttu-id="a47b9-103">Upozorní profileru, že funkce je se vraťte na volajícího.</span><span class="sxs-lookup"><span data-stu-id="a47b9-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a47b9-104">`FunctionLeave` Funkce je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a47b9-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="a47b9-105">Bude nadále fungovat, ale bude způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a47b9-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="a47b9-106">Použití [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="a47b9-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47b9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a47b9-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a47b9-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a47b9-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="a47b9-109">[v] Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="a47b9-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a47b9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a47b9-110">Remarks</span></span>  
 <span data-ttu-id="a47b9-111">`FunctionLeave` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="a47b9-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="a47b9-112">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="a47b9-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a47b9-113">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="a47b9-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="a47b9-114">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="a47b9-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="a47b9-115">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="a47b9-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a47b9-116">Implementace `FunctionLeave` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a47b9-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a47b9-117">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="a47b9-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a47b9-118">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave` vrátí.</span><span class="sxs-lookup"><span data-stu-id="a47b9-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="a47b9-119">Navíc `FunctionLeave` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="a47b9-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a47b9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a47b9-120">Requirements</span></span>  
 <span data-ttu-id="a47b9-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a47b9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a47b9-122">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a47b9-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a47b9-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a47b9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a47b9-124">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="a47b9-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a47b9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a47b9-125">See Also</span></span>  
 [<span data-ttu-id="a47b9-126">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a47b9-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="a47b9-127">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a47b9-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="a47b9-128">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="a47b9-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="a47b9-129">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a47b9-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="a47b9-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a47b9-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
