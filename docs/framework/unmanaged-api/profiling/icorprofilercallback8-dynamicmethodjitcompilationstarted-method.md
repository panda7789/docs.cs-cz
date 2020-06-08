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
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498996"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="4d446-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="4d446-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="4d446-103">[Podporováno v .NET Framework 4,7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4d446-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="4d446-104">Upozorní profiler vždy při spuštění kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="4d446-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d446-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d446-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d446-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d446-106">Parameters</span></span>  
<span data-ttu-id="4d446-107">pro`functionId`</span><span class="sxs-lookup"><span data-stu-id="4d446-107">[in] `functionId`</span></span>  
<span data-ttu-id="4d446-108">Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="4d446-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="4d446-109">[in] `fIsSafeToBlock` 
 `true` pro indikaci, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false`pro indikaci, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4d446-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="4d446-110">[in] `pILHeader` Ukazatel na první bajt hlavičky IL metody.</span><span class="sxs-lookup"><span data-stu-id="4d446-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="4d446-111">[in] `cbILHeader` Počet bajtů v hlavičce IL.</span><span class="sxs-lookup"><span data-stu-id="4d446-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d446-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d446-112">Remarks</span></span>  

<span data-ttu-id="4d446-113">Toto zpětné volání se aktivuje pokaždé, když je dynamická metoda kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="4d446-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="4d446-114">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="4d446-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="4d446-115">Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.</span><span class="sxs-lookup"><span data-stu-id="4d446-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="4d446-116">`functionId`hodnoty nelze použít k přeložení tokenů metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="4d446-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="4d446-117">`pILHeader`Ukazatel je platný pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="4d446-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d446-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d446-118">Requirements</span></span>  
 <span data-ttu-id="4d446-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d446-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d446-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d446-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d446-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d446-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d446-122">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4d446-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d446-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d446-123">See also</span></span>

- [<span data-ttu-id="4d446-124">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="4d446-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="4d446-125">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d446-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
