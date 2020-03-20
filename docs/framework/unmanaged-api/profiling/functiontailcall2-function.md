---
title: FunctionTailcall2 – funkce
ms.date: 03/30/2017
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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175184"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="c79b1-102">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c79b1-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="c79b1-103">Upozorní profiler, že aktuálně spuštěná funkce se chystá provést volání ocasu na jinou funkci a poskytuje informace o rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c79b1-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c79b1-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c79b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c79b1-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="c79b1-106">\[in] Identifikátor aktuálně vykonávající funkce, která se chystá provést volání ocasu.</span><span class="sxs-lookup"><span data-stu-id="c79b1-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="c79b1-107">\[in] Přemapovaný identifikátor funkce, který profiler dříve zadal prostřednictvím [FunctionIDMapper](functionidmapper-function.md), aktuálně spuštěné funkce, která se chystá provést volání ocasu.</span><span class="sxs-lookup"><span data-stu-id="c79b1-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="c79b1-108">\[in] `COR_PRF_FRAME_INFO` Hodnota, která odkazuje na informace o rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c79b1-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="c79b1-109">Profiler by měl považovat za neprůhledný popisovač, který může být předán zpět do modulu provádění v [Metodě ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="c79b1-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="c79b1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c79b1-110">Remarks</span></span>  
 <span data-ttu-id="c79b1-111">Cílová funkce volání ocasu použije aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání ocasu.</span><span class="sxs-lookup"><span data-stu-id="c79b1-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="c79b1-112">To znamená, že zpětné volání [FunctionLeave2](functionleave2-function.md) nebude vydána pro funkci, která je cílem volání ocasu.</span><span class="sxs-lookup"><span data-stu-id="c79b1-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="c79b1-113">Hodnota parametru `func` není platná po `FunctionTailcall2` vrátí funkce, protože hodnota může změnit nebo být zničena.</span><span class="sxs-lookup"><span data-stu-id="c79b1-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="c79b1-114">Funkce `FunctionTailcall2` je zpětné volání; musíte jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="c79b1-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="c79b1-115">Implementace musí používat `__declspec``naked`atribut ( ) třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="c79b1-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c79b1-116">Spuštění motoru neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="c79b1-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c79b1-117">Při vstupu je nutné uložit všechny registry, které používáte, včetně registrů v jednotce s plovoucí desetinnou tálicí (FPU).</span><span class="sxs-lookup"><span data-stu-id="c79b1-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c79b1-118">Při ukončení je nutné obnovit zásobník odprýskávání mačkání všechny parametry, které byly posunuty jeho volajícího.</span><span class="sxs-lookup"><span data-stu-id="c79b1-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c79b1-119">Implementace `FunctionTailcall2` by nemělblokovat, protože zpozdí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c79b1-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c79b1-120">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu vhodném pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c79b1-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c79b1-121">Pokud dojde k pokusu o uvolnění paměti, zaběhu se zablokuje, dokud `FunctionTailcall2` se vrátí.</span><span class="sxs-lookup"><span data-stu-id="c79b1-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="c79b1-122">`FunctionTailcall2` Funkce také nesmí volat do spravovaného kódu nebo žádným způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="c79b1-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c79b1-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c79b1-123">Requirements</span></span>  
 <span data-ttu-id="c79b1-124">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c79b1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c79b1-125">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c79b1-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c79b1-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c79b1-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c79b1-127">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c79b1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79b1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c79b1-128">See also</span></span>

- [<span data-ttu-id="c79b1-129">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c79b1-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="c79b1-130">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c79b1-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="c79b1-131">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c79b1-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c79b1-132">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="c79b1-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
