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
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177043"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="ed1c9-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="ed1c9-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="ed1c9-103">[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ed1c9-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="ed1c9-104">Upozorní profiler při každém spuštění kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1c9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed1c9-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed1c9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed1c9-106">Parameters</span></span>  
<span data-ttu-id="ed1c9-107">[v]`functionId`</span><span class="sxs-lookup"><span data-stu-id="ed1c9-107">[in] `functionId`</span></span>  
<span data-ttu-id="ed1c9-108">Identifikátor funkce v paměti, pro kterou je spuštěna kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="ed1c9-109">[v] `fIsSafeToBlock` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného 
 `true` volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="ed1c9-110">[v] `pILHeader` Ukazatel na první bajt hlavičky IL metody.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="ed1c9-111">[v] `cbILHeader` Počet bajtů v záhlaví IL.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed1c9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed1c9-112">Remarks</span></span>  

<span data-ttu-id="ed1c9-113">Toto zpětné volání se aktivuje vždy, když je dynamická metoda kompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="ed1c9-114">To zahrnuje různé IL útržky a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="ed1c9-115">Jeho cílem je poskytnout autoři profiler s dostatek informací k identifikaci kompilované metody pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="ed1c9-116">`functionId`hodnoty nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="ed1c9-117">Ukazatel `pILHeader` je platný pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ed1c9-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed1c9-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed1c9-118">Requirements</span></span>  
 <span data-ttu-id="ed1c9-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed1c9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed1c9-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed1c9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed1c9-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed1c9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed1c9-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ed1c9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1c9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed1c9-123">See also</span></span>

- [<span data-ttu-id="ed1c9-124">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ed1c9-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="ed1c9-125">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed1c9-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
