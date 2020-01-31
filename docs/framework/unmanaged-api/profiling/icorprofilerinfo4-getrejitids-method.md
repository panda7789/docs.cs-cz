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
ms.openlocfilehash: 9069498a4f62f4d9dbb50a7075323b14c3cc5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868444"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="4481e-102">ICorProfilerInfo4::GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="4481e-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="4481e-103">Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.</span><span class="sxs-lookup"><span data-stu-id="4481e-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="4481e-104">To zahrnuje verze rekompilovaných funkcí JIT, které byly následně obnoveny, ale nebyly dosud uvolněny (například pokud je stále používána doména aplikace obsahující vrácená funkce).</span><span class="sxs-lookup"><span data-stu-id="4481e-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4481e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4481e-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4481e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4481e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4481e-107">pro `FunctionID` instance funkce, pro kterou chcete vytvořit výčet verzí.</span><span class="sxs-lookup"><span data-stu-id="4481e-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="4481e-108">pro Počet ID rekompilovaných rekompilovaných JIT přidělených v poli `reJitIds`.</span><span class="sxs-lookup"><span data-stu-id="4481e-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="4481e-109">mimo Skutečný počet rekompilovaných ID JIT.</span><span class="sxs-lookup"><span data-stu-id="4481e-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="4481e-110">mimo Pole přidělené volajícím, které bude obsahovat ID rekompilovaných JIT pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="4481e-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4481e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4481e-111">Remarks</span></span>  
 <span data-ttu-id="4481e-112">`GetReJITIDs` vytvoří výčet aktivních rekompilovaných ID JIT pro danou instanci funkce.</span><span class="sxs-lookup"><span data-stu-id="4481e-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="4481e-113">Řídí se stejným vzorem použití jako s jinými `ICorProfilerInfo` funkcemi, které přijímají vyrovnávací paměti přidělené volajícím.</span><span class="sxs-lookup"><span data-stu-id="4481e-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4481e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4481e-114">Requirements</span></span>  
 <span data-ttu-id="4481e-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4481e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4481e-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4481e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4481e-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4481e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4481e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4481e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4481e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4481e-119">See also</span></span>

- [<span data-ttu-id="4481e-120">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4481e-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4481e-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4481e-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4481e-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="4481e-122">Profiling</span></span>](index.md)
