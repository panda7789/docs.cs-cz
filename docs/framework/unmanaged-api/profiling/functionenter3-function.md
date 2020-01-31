---
title: FunctionEnter3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 3ba014cbae4a71713f29968f0137ac053033c661
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866954"
---
# <a name="functionenter3-function"></a><span data-ttu-id="6843f-102">FunctionEnter3 – funkce</span><span class="sxs-lookup"><span data-stu-id="6843f-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="6843f-103">Upozorňuje profileru, že řízení je předáno funkci.</span><span class="sxs-lookup"><span data-stu-id="6843f-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6843f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6843f-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6843f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6843f-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="6843f-106">\[in] je identifikátor funkce, do které byl ovládací prvek předán.</span><span class="sxs-lookup"><span data-stu-id="6843f-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6843f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6843f-107">Remarks</span></span>  
 <span data-ttu-id="6843f-108">Funkce zpětného volání `FunctionEnter3` upozorní profileru na volání funkcí, ale nepodporuje kontrolu argumentů.</span><span class="sxs-lookup"><span data-stu-id="6843f-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="6843f-109">K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6843f-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6843f-110">Funkce `FunctionEnter3` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="6843f-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="6843f-111">Implementace musí používat atribut třídy úložiště `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="6843f-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6843f-112">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="6843f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6843f-113">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="6843f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6843f-114">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="6843f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6843f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6843f-115">Requirements</span></span>  
 <span data-ttu-id="6843f-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6843f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6843f-117">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6843f-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6843f-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6843f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6843f-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6843f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6843f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6843f-120">See also</span></span>

- [<span data-ttu-id="6843f-121">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="6843f-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="6843f-122">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="6843f-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="6843f-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6843f-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="6843f-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6843f-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="6843f-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6843f-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6843f-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6843f-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="6843f-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6843f-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="6843f-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="6843f-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="6843f-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="6843f-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="6843f-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6843f-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
