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
ms.openlocfilehash: ba15440df79dded95a8afa9438657d064e167f36
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495967"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="a7c30-102">ICorProfilerInfo4::GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="a7c30-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="a7c30-103">Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.</span><span class="sxs-lookup"><span data-stu-id="a7c30-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="a7c30-104">To zahrnuje verze rekompilovaných funkcí JIT, které byly následně obnoveny, ale nebyly dosud uvolněny (například pokud je stále používána doména aplikace obsahující vrácená funkce).</span><span class="sxs-lookup"><span data-stu-id="a7c30-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c30-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7c30-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c30-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7c30-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a7c30-107">pro `FunctionID`Instance funkce, pro kterou chcete vytvořit výčet verzí.</span><span class="sxs-lookup"><span data-stu-id="a7c30-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="a7c30-108">pro Počet ID rekompilovaných rekompilovaných JIT přidělených `reJitIds` v poli</span><span class="sxs-lookup"><span data-stu-id="a7c30-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="a7c30-109">mimo Skutečný počet rekompilovaných ID JIT.</span><span class="sxs-lookup"><span data-stu-id="a7c30-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="a7c30-110">mimo Pole přidělené volajícím, které bude obsahovat ID rekompilovaných JIT pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="a7c30-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7c30-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7c30-111">Remarks</span></span>  
 <span data-ttu-id="a7c30-112">`GetReJITIDs`Vytvoří výčet aktivních rekompilovaných ID JIT pro danou instanci funkce.</span><span class="sxs-lookup"><span data-stu-id="a7c30-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="a7c30-113">Řídí se stejným vzorem použití jako jiné `ICorProfilerInfo` funkce, které přijímají vyrovnávací paměti přidělené volajícím.</span><span class="sxs-lookup"><span data-stu-id="a7c30-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c30-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7c30-114">Requirements</span></span>  
 <span data-ttu-id="a7c30-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c30-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c30-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7c30-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7c30-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a7c30-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7c30-118">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c30-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7c30-119">See also</span></span>

- [<span data-ttu-id="a7c30-120">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7c30-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a7c30-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a7c30-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a7c30-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="a7c30-122">Profiling</span></span>](index.md)
