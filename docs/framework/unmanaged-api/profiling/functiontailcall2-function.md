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
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500569"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="b1013-102">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b1013-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="b1013-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje informace o bloku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b1013-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1013-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1013-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1013-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1013-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="b1013-106">\[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="b1013-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="b1013-107">\[in] identifikátor přemapované funkce, který profil dřív zadal přes [FunctionIDMapper –](functionidmapper-function.md), aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="b1013-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="b1013-108">\[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b1013-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="b1013-109">Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b1013-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1013-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1013-110">Remarks</span></span>  
 <span data-ttu-id="b1013-111">Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="b1013-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="b1013-112">To znamená, že zpětné volání [FunctionLeave2 –](functionleave2-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="b1013-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="b1013-113">Hodnota `func` parametru není platná, pokud se `FunctionTailcall2` funkce vrátí, protože se může změnit nebo zničit hodnota.</span><span class="sxs-lookup"><span data-stu-id="b1013-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="b1013-114">`FunctionTailcall2`Funkce je zpětné volání. je nutné ji implementovat.</span><span class="sxs-lookup"><span data-stu-id="b1013-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="b1013-115">Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().</span><span class="sxs-lookup"><span data-stu-id="b1013-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b1013-116">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="b1013-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b1013-117">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="b1013-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b1013-118">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="b1013-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b1013-119">Implementace `FunctionTailcall2` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1013-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b1013-120">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1013-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b1013-121">Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall2` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="b1013-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="b1013-122">`FunctionTailcall2`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="b1013-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1013-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1013-123">Requirements</span></span>  
 <span data-ttu-id="b1013-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1013-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1013-125">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b1013-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b1013-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1013-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1013-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1013-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1013-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1013-128">See also</span></span>

- [<span data-ttu-id="b1013-129">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b1013-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="b1013-130">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b1013-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="b1013-131">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b1013-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b1013-132">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="b1013-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
