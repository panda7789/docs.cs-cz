---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136574"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="f9a09-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a09-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="f9a09-103">[Podporováno v .NET Framework 4,7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="f9a09-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="f9a09-104">Upozorní profiler vždy, když se dokončí kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="f9a09-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a09-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9a09-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9a09-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9a09-106">Parameters</span></span>  
<span data-ttu-id="f9a09-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="f9a09-107">[in] `functionId`</span></span>  
<span data-ttu-id="f9a09-108">Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="f9a09-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="f9a09-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="f9a09-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="f9a09-110">Hodnota, která označuje, zda byla kompilace JIT úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f9a09-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="f9a09-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="f9a09-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="f9a09-112">`true` k označení toho, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f9a09-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f9a09-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9a09-113">Remarks</span></span>  

<span data-ttu-id="f9a09-114">Toto zpětné volání je aktivováno při dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="f9a09-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="f9a09-115">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="f9a09-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="f9a09-116">Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.</span><span class="sxs-lookup"><span data-stu-id="f9a09-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="f9a09-117">hodnoty `functionId` nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="f9a09-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9a09-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9a09-118">Requirements</span></span>  
 <span data-ttu-id="f9a09-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a09-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a09-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f9a09-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9a09-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f9a09-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a09-122">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a09-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a09-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9a09-123">See also</span></span>

- [<span data-ttu-id="f9a09-124">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a09-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="f9a09-125">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9a09-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
