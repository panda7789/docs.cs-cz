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
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177056"
---
# <a name="functionenter2-function"></a><span data-ttu-id="3c64a-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3c64a-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="3c64a-103">Upozorní profiler, že ovládací prvek je předáván funkci a poskytuje informace o argumentech rámce zásobníku a funkce.</span><span class="sxs-lookup"><span data-stu-id="3c64a-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="3c64a-104">Tato funkce nahrazuje funkci [FunctionEnter.](functionenter-function.md)</span><span class="sxs-lookup"><span data-stu-id="3c64a-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c64a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c64a-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c64a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c64a-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="3c64a-107">\[in] Identifikátor funkce, které je ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="3c64a-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="3c64a-108">\[in] Přemapovaný identifikátor funkce, který profiler dříve zadal pomocí funkce [FunctionIDMapper.](functionidmapper-function.md)</span><span class="sxs-lookup"><span data-stu-id="3c64a-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="3c64a-109">\[in] `COR_PRF_FRAME_INFO` Hodnota, která odkazuje na informace o rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3c64a-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="3c64a-110">Profiler by měl považovat za neprůhledný popisovač, který může být předán zpět do modulu provádění v [Metodě ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="3c64a-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="3c64a-111">\[in] Ukazatel na [strukturu COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) která určuje umístění v paměti argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="3c64a-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="3c64a-112">Chcete-li získat přístup `COR_PRF_ENABLE_FUNCTION_ARGS` k informacím o argumentech, musí být příznak nastaven.</span><span class="sxs-lookup"><span data-stu-id="3c64a-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="3c64a-113">Profiler můžete použít [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metoda nastavit příznaky události.</span><span class="sxs-lookup"><span data-stu-id="3c64a-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c64a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c64a-114">Remarks</span></span>  
 <span data-ttu-id="3c64a-115">Hodnoty `func` a `argumentInfo` parametry nejsou platné po `FunctionEnter2` vrátí funkce, protože hodnoty mohou změnit nebo být zničeny.</span><span class="sxs-lookup"><span data-stu-id="3c64a-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="3c64a-116">Funkce `FunctionEnter2` je zpětné volání; musíte jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="3c64a-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="3c64a-117">Implementace musí používat `__declspec``naked`atribut ( ) třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="3c64a-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3c64a-118">Spuštění motoru neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="3c64a-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3c64a-119">Při vstupu je nutné uložit všechny registry, které používáte, včetně registrů v jednotce s plovoucí desetinnou tálicí (FPU).</span><span class="sxs-lookup"><span data-stu-id="3c64a-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3c64a-120">Při ukončení je nutné obnovit zásobník odprýskávání mačkání všechny parametry, které byly posunuty jeho volajícího.</span><span class="sxs-lookup"><span data-stu-id="3c64a-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3c64a-121">Implementace `FunctionEnter2` by nemělblokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3c64a-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3c64a-122">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu vhodném pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3c64a-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3c64a-123">Pokud dojde k pokusu o uvolnění paměti, zaběhu se zablokuje, dokud `FunctionEnter2` se vrátí.</span><span class="sxs-lookup"><span data-stu-id="3c64a-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="3c64a-124">`FunctionEnter2` Funkce také nesmí volat do spravovaného kódu nebo žádným způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3c64a-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c64a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c64a-125">Requirements</span></span>  
 <span data-ttu-id="3c64a-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c64a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c64a-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3c64a-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3c64a-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c64a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c64a-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c64a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c64a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c64a-130">See also</span></span>

- [<span data-ttu-id="3c64a-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3c64a-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="3c64a-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3c64a-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="3c64a-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3c64a-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3c64a-134">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="3c64a-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
