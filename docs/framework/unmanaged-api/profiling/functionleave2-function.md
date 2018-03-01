---
title: "FunctionLeave2 – funkce"
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
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86ffb6cc18de0b0b7b68b418477c1e8cdd6e6cc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave2-function"></a><span data-ttu-id="0b1f7-102">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="0b1f7-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="0b1f7-103">Profileru upozorní, že funkce je vrátit volajícímu a poskytuje informace o zásobník rámec a funkce návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b1f7-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b1f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b1f7-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="0b1f7-106">[v] Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="0b1f7-107">[v] Identifikátor změnu mapování funkce, které profileru dříve zadán prostřednictvím [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="0b1f7-108">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="0b1f7-109">To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="0b1f7-110">[v] Ukazatel [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktura, která určuje umístění paměti funkce návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="0b1f7-111">Chcete-li získat přístup k informacím návratovou hodnotu `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="0b1f7-112">Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b1f7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b1f7-113">Remarks</span></span>  
 <span data-ttu-id="0b1f7-114">Hodnoty `func` a `retvalRange` parametry nejsou platné po `FunctionLeave2` funkce vrátí hodnotu, protože hodnoty může změnit nebo zničena.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="0b1f7-115">`FunctionLeave2` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="0b1f7-116">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="0b1f7-117">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="0b1f7-118">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="0b1f7-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="0b1f7-119">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0b1f7-120">Implementace `FunctionLeave2` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="0b1f7-121">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0b1f7-122">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="0b1f7-123">Navíc `FunctionLeave2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="0b1f7-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b1f7-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b1f7-124">Requirements</span></span>  
 <span data-ttu-id="0b1f7-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b1f7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b1f7-126">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="0b1f7-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0b1f7-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b1f7-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b1f7-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b1f7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1f7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b1f7-129">See Also</span></span>  
 [<span data-ttu-id="0b1f7-130">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="0b1f7-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="0b1f7-131">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="0b1f7-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="0b1f7-132">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0b1f7-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="0b1f7-133">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0b1f7-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
