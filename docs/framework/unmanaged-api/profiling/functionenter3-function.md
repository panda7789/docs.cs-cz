---
title: "FunctionEnter3 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter3
helpviewer_keywords: FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bbdfa608f1ea60462dc432a7c2b98cafe66d7be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="68e83-102">FunctionEnter3 – funkce</span><span class="sxs-lookup"><span data-stu-id="68e83-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="68e83-103">Upozorní profileru, že se ovládací prvek předán do funkce.</span><span class="sxs-lookup"><span data-stu-id="68e83-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68e83-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68e83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68e83-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="68e83-106">[v] Identifikátor funkce, ke kterému je předán ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="68e83-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e83-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68e83-107">Remarks</span></span>  
 <span data-ttu-id="68e83-108">`FunctionEnter3` Funkce zpětného volání upozorní profileru, protože funkce je volána, ale nemá podpora argument kontroly.</span><span class="sxs-lookup"><span data-stu-id="68e83-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="68e83-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaší implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="68e83-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="68e83-110">`FunctionEnter3` Je funkce zpětného volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="68e83-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="68e83-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="68e83-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="68e83-112">Spouštěcí modul neukládá žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="68e83-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="68e83-113">Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="68e83-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="68e83-114">Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.</span><span class="sxs-lookup"><span data-stu-id="68e83-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e83-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68e83-115">Requirements</span></span>  
 <span data-ttu-id="68e83-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e83-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e83-117">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="68e83-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="68e83-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68e83-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e83-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e83-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e83-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="68e83-120">See Also</span></span>  
 [<span data-ttu-id="68e83-121">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="68e83-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="68e83-122">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="68e83-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="68e83-123">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="68e83-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="68e83-124">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="68e83-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="68e83-125">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="68e83-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="68e83-126">Setenterleavefunctionhooks3 –</span><span class="sxs-lookup"><span data-stu-id="68e83-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="68e83-127">Setenterleavefunctionhooks3withinfo –</span><span class="sxs-lookup"><span data-stu-id="68e83-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="68e83-128">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="68e83-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="68e83-129">Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="68e83-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="68e83-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="68e83-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
