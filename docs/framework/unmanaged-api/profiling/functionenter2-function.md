---
title: "FunctionEnter2 – funkce"
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
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0709d54589b3f88b461adde3f3d380407d263855
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter2-function"></a><span data-ttu-id="6de00-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6de00-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="6de00-103">Profileru upozorní, že ovládací prvek je předávána funkci a poskytuje informace o zásobníku argumenty rámec a funkce.</span><span class="sxs-lookup"><span data-stu-id="6de00-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="6de00-104">Tato funkce nahrazuje [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6de00-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de00-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de00-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6de00-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6de00-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="6de00-107">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6de00-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="6de00-108">[v] Identifikátor změnu mapování funkce, které profileru dříve zadán pomocí [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6de00-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="6de00-109">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6de00-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="6de00-110">To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6de00-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="6de00-111">[v] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která určuje umístění v paměti funkce argumentů.</span><span class="sxs-lookup"><span data-stu-id="6de00-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="6de00-112">Chcete-li získat přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="6de00-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="6de00-113">Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="6de00-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de00-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6de00-114">Remarks</span></span>  
 <span data-ttu-id="6de00-115">Hodnoty `func` a `argumentInfo` parametry nejsou platné po `FunctionEnter2` funkce vrátí hodnotu, protože hodnoty může změnit nebo zničena.</span><span class="sxs-lookup"><span data-stu-id="6de00-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="6de00-116">`FunctionEnter2` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="6de00-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="6de00-117">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="6de00-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="6de00-118">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="6de00-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="6de00-119">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="6de00-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="6de00-120">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="6de00-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6de00-121">Implementace `FunctionEnter2` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6de00-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="6de00-122">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="6de00-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6de00-123">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="6de00-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="6de00-124">Navíc `FunctionEnter2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="6de00-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de00-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6de00-125">Requirements</span></span>  
 <span data-ttu-id="6de00-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de00-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de00-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6de00-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6de00-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6de00-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6de00-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de00-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de00-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6de00-130">See Also</span></span>  
 [<span data-ttu-id="6de00-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6de00-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="6de00-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="6de00-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="6de00-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6de00-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="6de00-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6de00-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
