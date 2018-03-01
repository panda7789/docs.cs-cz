---
title: "FunctionTailcall – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 223f112ba405e29b800456adca2f83e0cef6e7b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall-function"></a><span data-ttu-id="befdd-102">FunctionTailcall – funkce</span><span class="sxs-lookup"><span data-stu-id="befdd-102">FunctionTailcall Function</span></span>
<span data-ttu-id="befdd-103">Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="befdd-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="befdd-104">`FunctionTailcall` Funkce je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="befdd-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="befdd-105">Bude nadále fungovat, ale bude způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="befdd-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="befdd-106">Použití [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="befdd-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befdd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="befdd-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="befdd-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="befdd-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="befdd-109">[v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.</span><span class="sxs-lookup"><span data-stu-id="befdd-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="befdd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="befdd-110">Remarks</span></span>  
 <span data-ttu-id="befdd-111">Cíl funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volající funkce, který vytvořil tail volání.</span><span class="sxs-lookup"><span data-stu-id="befdd-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="befdd-112">To znamená, že [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="befdd-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="befdd-113">`FunctionTailcall` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="befdd-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="befdd-114">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="befdd-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="befdd-115">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="befdd-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="befdd-116">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="befdd-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="befdd-117">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="befdd-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="befdd-118">Implementace `FunctionTailcall` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="befdd-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="befdd-119">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="befdd-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="befdd-120">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall` vrátí.</span><span class="sxs-lookup"><span data-stu-id="befdd-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="befdd-121">Navíc `FunctionTailcall` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="befdd-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="befdd-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="befdd-122">Requirements</span></span>  
 <span data-ttu-id="befdd-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="befdd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="befdd-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="befdd-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="befdd-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="befdd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="befdd-126">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="befdd-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befdd-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="befdd-127">See Also</span></span>  
 [<span data-ttu-id="befdd-128">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="befdd-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="befdd-129">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="befdd-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="befdd-130">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="befdd-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="befdd-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="befdd-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
