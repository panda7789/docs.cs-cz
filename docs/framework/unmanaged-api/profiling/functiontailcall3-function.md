---
title: FunctionTailcall3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 8d7c226d26d677a8b10df29e0343b71682c46699
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427375"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="b85a4-102">FunctionTailcall3 – funkce</span><span class="sxs-lookup"><span data-stu-id="b85a4-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="b85a4-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="b85a4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b85a4-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b85a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b85a4-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="b85a4-106">pro Identifikátor aktuálně vykonávané funkce, která má být volána pro volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="b85a4-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b85a4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b85a4-107">Remarks</span></span>  
 <span data-ttu-id="b85a4-108">Funkce zpětného volání `FunctionTailcall3` upozorní profileru na volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="b85a4-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="b85a4-109">K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b85a4-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b85a4-110">Funkce `FunctionTailcall3` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="b85a4-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="b85a4-111">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="b85a4-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b85a4-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="b85a4-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b85a4-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="b85a4-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b85a4-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="b85a4-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b85a4-115">Implementace `FunctionTailcall3` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b85a4-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b85a4-116">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b85a4-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b85a4-117">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionTailcall3` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="b85a4-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="b85a4-118">Funkce `FunctionTailcall3` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="b85a4-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b85a4-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b85a4-119">Requirements</span></span>  
 <span data-ttu-id="b85a4-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b85a4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85a4-121">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b85a4-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b85a4-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b85a4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b85a4-123">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b85a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85a4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b85a4-124">See also</span></span>

- [<span data-ttu-id="b85a4-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="b85a4-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="b85a4-126">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="b85a4-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="b85a4-127">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b85a4-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b85a4-128">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b85a4-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b85a4-129">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="b85a4-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b85a4-130">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="b85a4-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="b85a4-131">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="b85a4-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="b85a4-132">SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="b85a4-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="b85a4-133">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="b85a4-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="b85a4-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b85a4-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
