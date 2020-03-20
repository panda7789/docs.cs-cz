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
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175106"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="d3b0e-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="d3b0e-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="d3b0e-103">[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d3b0e-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="d3b0e-104">Upozorní profiler vždy, když je dokončena kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b0e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3b0e-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3b0e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3b0e-106">Parameters</span></span>  
<span data-ttu-id="d3b0e-107">[v]`functionId`</span><span class="sxs-lookup"><span data-stu-id="d3b0e-107">[in] `functionId`</span></span>  
<span data-ttu-id="d3b0e-108">Identifikátor funkce v paměti, pro kterou je spuštěna kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="d3b0e-109">[v] `hrStatus` Hodnota, která označuje, zda byla kompilace JIT úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="d3b0e-110">[v] `fIsSafeToBlock` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného 
 `true` volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="d3b0e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3b0e-111">Remarks</span></span>  

<span data-ttu-id="d3b0e-112">Toto zpětné volání se aktivuje vždy, když jit kompilace dynamické metody byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="d3b0e-113">To zahrnuje různé IL útržky a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="d3b0e-114">Jeho cílem je poskytnout autoři profiler s dostatek informací k identifikaci kompilované metody pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="d3b0e-115">`functionId`hodnoty nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3b0e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3b0e-116">Requirements</span></span>  
 <span data-ttu-id="d3b0e-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b0e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b0e-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3b0e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3b0e-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3b0e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3b0e-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b0e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b0e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3b0e-121">See also</span></span>

- [<span data-ttu-id="d3b0e-122">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="d3b0e-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="d3b0e-123">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3b0e-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
