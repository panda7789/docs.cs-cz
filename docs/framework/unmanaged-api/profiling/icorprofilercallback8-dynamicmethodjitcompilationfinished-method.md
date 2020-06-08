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
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499074"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="bab01-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="bab01-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="bab01-103">[Podporováno v .NET Framework 4,7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="bab01-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="bab01-104">Upozorní profiler vždy, když se dokončí kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="bab01-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab01-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bab01-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab01-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bab01-106">Parameters</span></span>  
<span data-ttu-id="bab01-107">pro`functionId`</span><span class="sxs-lookup"><span data-stu-id="bab01-107">[in] `functionId`</span></span>  
<span data-ttu-id="bab01-108">Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="bab01-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="bab01-109">[in] `hrStatus` Hodnota, která označuje, zda byla kompilace JIT úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bab01-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="bab01-110">[in] `fIsSafeToBlock` 
 `true` pro indikaci, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false`pro indikaci, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bab01-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="bab01-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bab01-111">Remarks</span></span>  

<span data-ttu-id="bab01-112">Toto zpětné volání je aktivováno při dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="bab01-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="bab01-113">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="bab01-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="bab01-114">Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.</span><span class="sxs-lookup"><span data-stu-id="bab01-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="bab01-115">`functionId`hodnoty nelze použít k přeložení tokenů metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="bab01-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="bab01-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bab01-116">Requirements</span></span>  
 <span data-ttu-id="bab01-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab01-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab01-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bab01-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bab01-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bab01-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bab01-120">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bab01-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab01-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bab01-121">See also</span></span>

- [<span data-ttu-id="bab01-122">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="bab01-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="bab01-123">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bab01-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
