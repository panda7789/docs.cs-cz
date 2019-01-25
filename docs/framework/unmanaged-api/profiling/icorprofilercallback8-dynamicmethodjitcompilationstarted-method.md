---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062229245e3ae209de0eda65d4be59e286f4da7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517744"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="e2aea-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="e2aea-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="e2aea-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e2aea-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="e2aea-104">Profiler upozorní při každém spuštění kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="e2aea-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2aea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2aea-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2aea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2aea-106">Parameters</span></span>  
<span data-ttu-id="e2aea-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="e2aea-107">[in] `functionId`</span></span>  
<span data-ttu-id="e2aea-108">Identifikátor funkce v paměti, pro které JIT kompilace spuštění.</span><span class="sxs-lookup"><span data-stu-id="e2aea-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="e2aea-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="e2aea-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="e2aea-110">`true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e2aea-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="e2aea-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="e2aea-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="e2aea-112">Ukazatel na první bajt záhlaví úrovně Důvěryhodnosti metody.</span><span class="sxs-lookup"><span data-stu-id="e2aea-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="e2aea-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="e2aea-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="e2aea-114">Počet bajtů v záhlaví úrovně Důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e2aea-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="e2aea-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2aea-115">Remarks</span></span>  

<span data-ttu-id="e2aea-116">Toto zpětné volání se aktivuje vždy, když je dynamická metoda kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="e2aea-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="e2aea-117">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="e2aea-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="e2aea-118">Jeho cílem je poskytnout dostatek informací k identifikaci metody kompilované pro uživatele autoři profileru.</span><span class="sxs-lookup"><span data-stu-id="e2aea-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e2aea-119">`functionId` hodnoty nelze přeložit na jejich tokeny metadat použít, protože dynamické metody mají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="e2aea-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="e2aea-120">`pILHeader` Ukazatel je platný pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e2aea-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2aea-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2aea-121">Requirements</span></span>  
 <span data-ttu-id="e2aea-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2aea-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2aea-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2aea-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2aea-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2aea-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2aea-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2aea-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2aea-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2aea-126">See also</span></span>
- [<span data-ttu-id="e2aea-127">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e2aea-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="e2aea-128">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2aea-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
