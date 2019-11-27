---
title: FunctionLeave2 – funkce
ms.date: 03/30/2017
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
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446012"
---
# <a name="functionleave2-function"></a><span data-ttu-id="9c7af-102">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9c7af-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="9c7af-103">Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce.</span><span class="sxs-lookup"><span data-stu-id="9c7af-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c7af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c7af-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c7af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c7af-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="9c7af-106">pro Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="9c7af-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="9c7af-107">pro Znovu namapovaný identifikátor funkce, který Profiler dříve zadal prostřednictvím funkce [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)</span><span class="sxs-lookup"><span data-stu-id="9c7af-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="9c7af-108">pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9c7af-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="9c7af-109">Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9c7af-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="9c7af-110">pro Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturu, která určuje umístění paměti návratové hodnoty funkce.</span><span class="sxs-lookup"><span data-stu-id="9c7af-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="9c7af-111">Aby bylo možné získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="9c7af-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="9c7af-112">Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.</span><span class="sxs-lookup"><span data-stu-id="9c7af-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c7af-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c7af-113">Remarks</span></span>  
 <span data-ttu-id="9c7af-114">Hodnoty parametrů `func` a `retvalRange` nejsou po vrácení `FunctionLeave2` funkce platné, protože hodnoty se mohou změnit nebo zničit.</span><span class="sxs-lookup"><span data-stu-id="9c7af-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="9c7af-115">Funkce `FunctionLeave2` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="9c7af-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="9c7af-116">Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="9c7af-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="9c7af-117">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="9c7af-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="9c7af-118">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="9c7af-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="9c7af-119">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="9c7af-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9c7af-120">Implementace `FunctionLeave2` by neměla zablokovat, protože bude odloženo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9c7af-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="9c7af-121">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9c7af-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9c7af-122">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave2` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="9c7af-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="9c7af-123">Také funkce `FunctionLeave2` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9c7af-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c7af-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c7af-124">Requirements</span></span>  
 <span data-ttu-id="9c7af-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c7af-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c7af-126">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="9c7af-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9c7af-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9c7af-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c7af-128">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c7af-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7af-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c7af-129">See also</span></span>

- [<span data-ttu-id="9c7af-130">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9c7af-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="9c7af-131">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9c7af-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="9c7af-132">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9c7af-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="9c7af-133">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9c7af-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
