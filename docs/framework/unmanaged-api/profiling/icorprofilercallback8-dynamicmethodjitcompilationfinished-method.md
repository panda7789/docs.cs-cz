---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: addaf6333914c9f0ea36d67e3eb96577fef79e1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497915"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="e2fd0-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="e2fd0-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="e2fd0-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e2fd0-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="e2fd0-104">Profiler upozorní pokaždé, když se dokončí kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2fd0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2fd0-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2fd0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2fd0-106">Parameters</span></span>  
<span data-ttu-id="e2fd0-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="e2fd0-107">[in] `functionId`</span></span>  
<span data-ttu-id="e2fd0-108">Identifikátor funkce v paměti, pro které JIT kompilace spuštění.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="e2fd0-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="e2fd0-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="e2fd0-110">Hodnota, která určuje, zda byla úspěšná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="e2fd0-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="e2fd0-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="e2fd0-112">`true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e2fd0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2fd0-113">Remarks</span></span>  

<span data-ttu-id="e2fd0-114">Toto zpětné volání se aktivuje vždy, když dokončil kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="e2fd0-115">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="e2fd0-116">Jeho cílem je poskytnout dostatek informací k identifikaci metody kompilované pro uživatele autoři profileru.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e2fd0-117">`functionId` hodnoty nelze přeložit na jejich tokeny metadat použít, protože dynamické metody mají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2fd0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2fd0-118">Requirements</span></span>  
 <span data-ttu-id="e2fd0-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2fd0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2fd0-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2fd0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2fd0-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2fd0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2fd0-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2fd0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fd0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2fd0-123">See also</span></span>
- [<span data-ttu-id="e2fd0-124">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="e2fd0-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="e2fd0-125">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2fd0-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
