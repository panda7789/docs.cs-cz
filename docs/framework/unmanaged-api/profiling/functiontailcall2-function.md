---
title: "FunctionTailcall2 – funkce"
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
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="bb06f-102">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="bb06f-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="bb06f-103">Profileru upozorní, že aktuálně prováděné funkce provede volání funkce tail do jiné funkce a poskytuje informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bb06f-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb06f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb06f-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb06f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb06f-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="bb06f-106">[v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.</span><span class="sxs-lookup"><span data-stu-id="bb06f-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="bb06f-107">[v] Identifikátor změnu mapování funkce, které profileru dříve zadán prostřednictvím [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), aktuálně prováděné funkce, která se chystáte provést, tail volání.</span><span class="sxs-lookup"><span data-stu-id="bb06f-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="bb06f-108">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bb06f-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="bb06f-109">To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="bb06f-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb06f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb06f-110">Remarks</span></span>  
 <span data-ttu-id="bb06f-111">Cíl funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volající funkce, který vytvořil tail volání.</span><span class="sxs-lookup"><span data-stu-id="bb06f-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="bb06f-112">To znamená, že [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="bb06f-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="bb06f-113">Hodnota `func` parametr není platný po `FunctionTailcall2` funkce vrátí hodnotu, protože hodnota může změnit nebo zničena.</span><span class="sxs-lookup"><span data-stu-id="bb06f-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="bb06f-114">`FunctionTailcall2` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="bb06f-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="bb06f-115">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="bb06f-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="bb06f-116">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="bb06f-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="bb06f-117">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="bb06f-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="bb06f-118">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="bb06f-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bb06f-119">Implementace `FunctionTailcall2` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bb06f-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="bb06f-120">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="bb06f-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bb06f-121">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="bb06f-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="bb06f-122">Navíc `FunctionTailcall2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="bb06f-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb06f-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb06f-123">Requirements</span></span>  
 <span data-ttu-id="bb06f-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb06f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb06f-125">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bb06f-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bb06f-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb06f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb06f-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb06f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb06f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb06f-128">See Also</span></span>  
 [<span data-ttu-id="bb06f-129">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="bb06f-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="bb06f-130">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="bb06f-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="bb06f-131">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="bb06f-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="bb06f-132">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bb06f-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
