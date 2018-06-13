---
title: FunctionEnter2 – funkce
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d79249a2540adbd7f1b7e9bf36c899ba94d71e2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452387"
---
# <a name="functionenter2-function"></a><span data-ttu-id="ff7f2-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ff7f2-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="ff7f2-103">Profileru upozorní, že ovládací prvek je předávána funkci a poskytuje informace o zásobníku argumenty rámec a funkce.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="ff7f2-104">Tato funkce nahrazuje [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff7f2-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff7f2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff7f2-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="ff7f2-107">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="ff7f2-108">[v] Identifikátor změnu mapování funkce, které profileru dříve zadán pomocí [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="ff7f2-109">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="ff7f2-110">To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="ff7f2-111">[v] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která určuje umístění v paměti funkce argumentů.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="ff7f2-112">Chcete-li získat přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="ff7f2-113">Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff7f2-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff7f2-114">Remarks</span></span>  
 <span data-ttu-id="ff7f2-115">Hodnoty `func` a `argumentInfo` parametry nejsou platné po `FunctionEnter2` funkce vrátí hodnotu, protože hodnoty může změnit nebo zničena.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="ff7f2-116">`FunctionEnter2` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="ff7f2-117">Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="ff7f2-118">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="ff7f2-119">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="ff7f2-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="ff7f2-120">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ff7f2-121">Implementace `FunctionEnter2` by neměly blokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="ff7f2-122">Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ff7f2-123">Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter2` vrátí.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="ff7f2-124">Navíc `FunctionEnter2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="ff7f2-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff7f2-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff7f2-125">Requirements</span></span>  
 <span data-ttu-id="ff7f2-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff7f2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff7f2-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ff7f2-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ff7f2-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff7f2-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff7f2-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff7f2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7f2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff7f2-130">See Also</span></span>  
 [<span data-ttu-id="ff7f2-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ff7f2-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="ff7f2-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ff7f2-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="ff7f2-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ff7f2-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="ff7f2-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ff7f2-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
