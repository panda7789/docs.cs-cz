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
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855939"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="d8322-102">ICorProfilerInfo4::GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="d8322-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="d8322-103">Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.</span><span class="sxs-lookup"><span data-stu-id="d8322-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="d8322-104">To zahrnuje verze rekompilovaných funkcí JIT, které byly následně obnoveny, ale nebyly dosud uvolněny (například pokud je stále používána doména aplikace obsahující vrácená funkce).</span><span class="sxs-lookup"><span data-stu-id="d8322-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8322-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8322-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8322-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8322-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d8322-107">pro `FunctionID` Instance funkce, pro kterou chcete vytvořit výčet verzí.</span><span class="sxs-lookup"><span data-stu-id="d8322-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="d8322-108">pro Počet ID rekompilovaných rekompilovaných JIT přidělených `reJitIds` v poli</span><span class="sxs-lookup"><span data-stu-id="d8322-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="d8322-109">mimo Skutečný počet rekompilovaných ID JIT.</span><span class="sxs-lookup"><span data-stu-id="d8322-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="d8322-110">mimo Pole přidělené volajícím, které bude obsahovat ID rekompilovaných JIT pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="d8322-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8322-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8322-111">Remarks</span></span>  
 <span data-ttu-id="d8322-112">`GetReJITIDs`Vytvoří výčet aktivních rekompilovaných ID JIT pro danou instanci funkce.</span><span class="sxs-lookup"><span data-stu-id="d8322-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="d8322-113">Řídí se stejným vzorem použití jako jiné `ICorProfilerInfo` funkce, které přijímají vyrovnávací paměti přidělené volajícím.</span><span class="sxs-lookup"><span data-stu-id="d8322-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8322-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8322-114">Requirements</span></span>  
 <span data-ttu-id="d8322-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8322-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8322-116">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8322-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8322-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8322-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8322-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8322-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8322-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8322-119">See also</span></span>

- [<span data-ttu-id="d8322-120">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8322-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d8322-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d8322-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d8322-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="d8322-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
