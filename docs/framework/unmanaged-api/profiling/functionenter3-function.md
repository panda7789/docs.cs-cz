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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24c9077863ada4d1208f29755a70d2cf8abc1208
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782700"
---
# <a name="functionenter3-function"></a><span data-ttu-id="adf94-102">FunctionEnter3 – funkce</span><span class="sxs-lookup"><span data-stu-id="adf94-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="adf94-103">Oznámí profileru, že se ovládací prvek předán funkci.</span><span class="sxs-lookup"><span data-stu-id="adf94-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adf94-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adf94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="adf94-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="adf94-106">[in] Identifikátor funkce, do které se předá řízení.</span><span class="sxs-lookup"><span data-stu-id="adf94-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adf94-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adf94-107">Remarks</span></span>  
 <span data-ttu-id="adf94-108">`FunctionEnter3` Funkce zpětného volání oznámí profileru jako funkce je volána, ale nemá podpora argument kontroly.</span><span class="sxs-lookup"><span data-stu-id="adf94-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="adf94-109">Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaši implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="adf94-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="adf94-110">`FunctionEnter3` Funkce je zpětné volání, je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="adf94-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="adf94-111">Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.</span><span class="sxs-lookup"><span data-stu-id="adf94-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="adf94-112">Prováděcí modul nelze uložit žádné registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="adf94-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="adf94-113">Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="adf94-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="adf94-114">Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.</span><span class="sxs-lookup"><span data-stu-id="adf94-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adf94-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adf94-115">Requirements</span></span>  
 <span data-ttu-id="adf94-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adf94-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adf94-117">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="adf94-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="adf94-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adf94-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adf94-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf94-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf94-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adf94-120">See also</span></span>

- [<span data-ttu-id="adf94-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="adf94-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="adf94-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="adf94-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="adf94-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="adf94-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="adf94-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="adf94-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="adf94-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="adf94-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="adf94-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="adf94-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="adf94-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="adf94-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="adf94-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="adf94-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="adf94-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="adf94-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="adf94-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="adf94-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
