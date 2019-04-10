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
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206587"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="1da3e-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="1da3e-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="1da3e-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1da3e-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="1da3e-104">Profiler upozorní pokaždé, když se dokončí kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="1da3e-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da3e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da3e-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1da3e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1da3e-106">Parameters</span></span>  
<span data-ttu-id="1da3e-107">[in]</span><span class="sxs-lookup"><span data-stu-id="1da3e-107">[in]</span></span> `functionId`  
<span data-ttu-id="1da3e-108">Identifikátor funkce v paměti, pro které JIT kompilace spuštění.</span><span class="sxs-lookup"><span data-stu-id="1da3e-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="1da3e-109">[in]</span><span class="sxs-lookup"><span data-stu-id="1da3e-109">[in]</span></span> `hrStatus`   
<span data-ttu-id="1da3e-110">Hodnota, která určuje, zda byla úspěšná kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="1da3e-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="1da3e-111">[in]</span><span class="sxs-lookup"><span data-stu-id="1da3e-111">[in]</span></span> `fIsSafeToBlock`   
`true` <span data-ttu-id="1da3e-112">k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1da3e-112">to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="1da3e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1da3e-113">Remarks</span></span>  

<span data-ttu-id="1da3e-114">Toto zpětné volání se aktivuje vždy, když dokončil kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="1da3e-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="1da3e-115">To zahrnuje různé zástupné procedury IL a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="1da3e-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="1da3e-116">Jeho cílem je poskytnout dostatek informací k identifikaci metody kompilované pro uživatele autoři profileru.</span><span class="sxs-lookup"><span data-stu-id="1da3e-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> `functionId` <span data-ttu-id="1da3e-117">hodnoty nelze přeložit na jejich tokeny metadat použít, protože dynamické metody mají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="1da3e-117">values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="1da3e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1da3e-118">Requirements</span></span>  
 <span data-ttu-id="1da3e-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da3e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da3e-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1da3e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1da3e-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1da3e-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1da3e-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1da3e-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1da3e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1da3e-123">See also</span></span>

- [<span data-ttu-id="1da3e-124">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="1da3e-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="1da3e-125">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1da3e-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
