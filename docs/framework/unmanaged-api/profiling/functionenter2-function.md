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
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866980"
---
# <a name="functionenter2-function"></a><span data-ttu-id="08996-102">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="08996-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="08996-103">Upozorňuje profileru, že řízení je předáno funkci a poskytuje informace o bloku zásobníku a argumentech funkce.</span><span class="sxs-lookup"><span data-stu-id="08996-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="08996-104">Tato funkce nahrazuje funkci [FunctionEnter –](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="08996-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08996-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08996-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08996-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="08996-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="08996-107">\[in] je identifikátor funkce, do které byl ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="08996-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="08996-108">\[in] identifikátor přemapované funkce, který Profiler předtím zadal pomocí funkce [FunctionIDMapper –](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="08996-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="08996-109">\[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="08996-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="08996-110">Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="08996-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="08996-111">\[in] ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , která určuje umístění v paměti argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="08996-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="08996-112">Aby bylo možné získat přístup k informacím o argumentech, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_ARGS`.</span><span class="sxs-lookup"><span data-stu-id="08996-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="08996-113">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.</span><span class="sxs-lookup"><span data-stu-id="08996-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="08996-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08996-114">Remarks</span></span>  
 <span data-ttu-id="08996-115">Hodnoty parametrů `func` a `argumentInfo` nejsou po vrácení `FunctionEnter2` funkce platné, protože hodnoty se mohou změnit nebo zničit.</span><span class="sxs-lookup"><span data-stu-id="08996-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="08996-116">Funkce `FunctionEnter2` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="08996-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="08996-117">Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="08996-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="08996-118">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="08996-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="08996-119">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="08996-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="08996-120">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="08996-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="08996-121">Implementace `FunctionEnter2` by neměla zablokovat, protože bude odloženo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="08996-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="08996-122">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="08996-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="08996-123">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionEnter2` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="08996-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="08996-124">Také funkce `FunctionEnter2` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="08996-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08996-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08996-125">Requirements</span></span>  
 <span data-ttu-id="08996-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08996-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08996-127">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="08996-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="08996-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08996-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08996-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08996-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08996-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08996-130">See also</span></span>

- [<span data-ttu-id="08996-131">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="08996-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="08996-132">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="08996-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="08996-133">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="08996-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="08996-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="08996-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
