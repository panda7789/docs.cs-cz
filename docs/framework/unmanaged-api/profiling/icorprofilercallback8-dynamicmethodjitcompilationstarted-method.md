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
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142243"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="69f11-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="69f11-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="69f11-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="69f11-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="69f11-104">Profiler upozorní při každém spuštění kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="69f11-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f11-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f11-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="69f11-106">Parameters</span></span>  
<span data-ttu-id="69f11-107">[in]</span><span class="sxs-lookup"><span data-stu-id="69f11-107">[in]</span></span> `functionId`  
<span data-ttu-id="69f11-108">Identifikátor funkce v paměti, pro které JIT kompilace spuštění.</span><span class="sxs-lookup"><span data-stu-id="69f11-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="69f11-109">[in]</span><span class="sxs-lookup"><span data-stu-id="69f11-109">[in]</span></span> `fIsSafeToBlock`   
`true` <span data-ttu-id="69f11-110">k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="69f11-110">to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="69f11-111">[in]</span><span class="sxs-lookup"><span data-stu-id="69f11-111">[in]</span></span> `pILHeader`    
<span data-ttu-id="69f11-112">Ukazatel na první bajt záhlaví úrovně Důvěryhodnosti metody.</span><span class="sxs-lookup"><span data-stu-id="69f11-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="69f11-113">[in]</span><span class="sxs-lookup"><span data-stu-id="69f11-113">[in]</span></span> `cbILHeader`    
<span data-ttu-id="69f11-114">Počet bajtů v záhlaví úrovně Důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="69f11-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="69f11-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69f11-115">Remarks</span></span>  

<span data-ttu-id="69f11-116">Toto zpětné volání se aktivuje vždy, když je dynamická metoda kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="69f11-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="69f11-117">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="69f11-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="69f11-118">Jeho cílem je poskytnout dostatek informací k identifikaci metody kompilované pro uživatele autoři profileru.</span><span class="sxs-lookup"><span data-stu-id="69f11-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> `functionId` <span data-ttu-id="69f11-119">hodnoty nelze přeložit na jejich tokeny metadat použít, protože dynamické metody mají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="69f11-119">values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="69f11-120">`pILHeader` Ukazatel je platný pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="69f11-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="69f11-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69f11-121">Requirements</span></span>  
 <span data-ttu-id="69f11-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f11-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f11-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69f11-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69f11-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f11-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="69f11-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="69f11-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="69f11-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69f11-126">See also</span></span>

- [<span data-ttu-id="69f11-127">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="69f11-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="69f11-128">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69f11-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
