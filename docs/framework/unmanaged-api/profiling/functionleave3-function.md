---
title: FunctionLeave3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 32d86f19e9c50694c7d113195e6967645b710666
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866866"
---
# <a name="functionleave3-function"></a><span data-ttu-id="4f919-102">FunctionLeave3 – funkce</span><span class="sxs-lookup"><span data-stu-id="4f919-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="4f919-103">Upozorní profiler, že se vrací řízení z funkce.</span><span class="sxs-lookup"><span data-stu-id="4f919-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f919-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f919-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f919-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f919-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="4f919-106">\[in] identifikátor funkce, ze které je vrácen ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4f919-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="4f919-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f919-107">Remarks</span></span>  
 <span data-ttu-id="4f919-108">Funkce zpětného volání `FunctionLeave3` upozorní profileru na volání funkcí, ale nepodporuje kontrolu návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="4f919-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="4f919-109">K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f919-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4f919-110">Funkce `FunctionLeave3` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="4f919-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="4f919-111">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="4f919-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="4f919-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="4f919-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="4f919-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="4f919-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="4f919-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="4f919-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4f919-115">Implementace `FunctionLeave3` by neměla blokovat, protože by se zpozdilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4f919-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="4f919-116">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4f919-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4f919-117">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave3` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="4f919-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="4f919-118">Funkce `FunctionLeave3` nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="4f919-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f919-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f919-119">Requirements</span></span>  
 <span data-ttu-id="4f919-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f919-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f919-121">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="4f919-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4f919-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f919-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f919-123">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f919-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f919-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f919-124">See also</span></span>

- [<span data-ttu-id="4f919-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4f919-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="4f919-126">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="4f919-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4f919-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f919-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4f919-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f919-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="4f919-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f919-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="4f919-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="4f919-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="4f919-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f919-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="4f919-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="4f919-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4f919-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="4f919-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="4f919-134">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4f919-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
