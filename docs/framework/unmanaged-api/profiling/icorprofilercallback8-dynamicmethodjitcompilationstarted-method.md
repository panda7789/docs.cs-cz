---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136467"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="20193-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="20193-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="20193-103">[Podporováno v .NET Framework 4,7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="20193-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="20193-104">Upozorní profiler vždy při spuštění kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="20193-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20193-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20193-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20193-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="20193-106">Parameters</span></span>  
<span data-ttu-id="20193-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="20193-107">[in] `functionId`</span></span>  
<span data-ttu-id="20193-108">Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="20193-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="20193-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="20193-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="20193-110">`true` k označení toho, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="20193-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="20193-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="20193-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="20193-112">Ukazatel na první bajt hlavičky IL metody.</span><span class="sxs-lookup"><span data-stu-id="20193-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="20193-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="20193-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="20193-114">Počet bajtů v hlavičce IL.</span><span class="sxs-lookup"><span data-stu-id="20193-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="20193-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20193-115">Remarks</span></span>  

<span data-ttu-id="20193-116">Toto zpětné volání se aktivuje pokaždé, když je dynamická metoda kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="20193-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="20193-117">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="20193-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="20193-118">Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.</span><span class="sxs-lookup"><span data-stu-id="20193-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="20193-119">hodnoty `functionId` nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="20193-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="20193-120">Ukazatel `pILHeader` je platný pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="20193-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="20193-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20193-121">Requirements</span></span>  
 <span data-ttu-id="20193-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20193-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20193-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="20193-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20193-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20193-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20193-125">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="20193-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20193-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20193-126">See also</span></span>

- [<span data-ttu-id="20193-127">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="20193-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="20193-128">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20193-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
