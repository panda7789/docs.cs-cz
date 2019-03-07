---
title: ICorProfilerInfo4::GetReJITIDs – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0361a4cd048f0b3be6bce47e52dd44ba3cea3475
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482753"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="ae81d-102">ICorProfilerInfo4::GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="ae81d-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="ae81d-103">Vrátí pole ID, které identifikují všechny překompilován JIT verze zadané funkce, které jsou pořád ještě přidělená.</span><span class="sxs-lookup"><span data-stu-id="ae81d-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="ae81d-104">To zahrnuje překompilován JIT verze funkcí, které se později vrátit, ale ještě není uvolněn (například když doménu aplikace, která obsahuje vrácené funkce se stále používá).</span><span class="sxs-lookup"><span data-stu-id="ae81d-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae81d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae81d-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae81d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae81d-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ae81d-107">[in] `FunctionID` Instance funkce pro kterou chcete získat výčet verzí.</span><span class="sxs-lookup"><span data-stu-id="ae81d-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="ae81d-108">[in] Počet přidělených v ID překompilován JIT `reJitIds` pole.</span><span class="sxs-lookup"><span data-stu-id="ae81d-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="ae81d-109">[out] Skutečný počet ID překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="ae81d-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="ae81d-110">[out] Pole přidělené volajícímu, který bude obsahovat ID překompilován JIT pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="ae81d-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae81d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae81d-111">Remarks</span></span>  
 <span data-ttu-id="ae81d-112">`GetReJITIDs` Vytvoří výčet aktivní ID překompilován JIT pro instanci dané funkce.</span><span class="sxs-lookup"><span data-stu-id="ae81d-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="ae81d-113">Ji používá stejný vzor používání jako ostatní `ICorProfilerInfo` funkce, které přijímají volající – přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ae81d-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae81d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae81d-114">Requirements</span></span>  
 <span data-ttu-id="ae81d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae81d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae81d-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae81d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae81d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae81d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae81d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae81d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae81d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae81d-119">See also</span></span>
- [<span data-ttu-id="ae81d-120">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae81d-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ae81d-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ae81d-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ae81d-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="ae81d-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
