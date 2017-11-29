---
title: "ICorProfilerThreadEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3295f3dc9af50fb62a2008f59819a51a6032a48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="2af0f-102">ICorProfilerThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2af0f-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="2af0f-103">Získá zadaný počet vláken, souvislý z kolekce sekvenčních vláken, začínající na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="2af0f-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2af0f-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2af0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2af0f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2af0f-106">[v] Počet vláken pro načtení.</span><span class="sxs-lookup"><span data-stu-id="2af0f-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="2af0f-107">[out] Pole `ThreadID` hodnoty, z nichž každý představuje načtené vlákna.</span><span class="sxs-lookup"><span data-stu-id="2af0f-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2af0f-108">[out] Ukazatel na počet vláken ve skutečnosti, vrátí se v `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="2af0f-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2af0f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2af0f-109">Return Value</span></span>  
 <span data-ttu-id="2af0f-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2af0f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2af0f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2af0f-111">HRESULT</span></span>|<span data-ttu-id="2af0f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2af0f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2af0f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2af0f-113">S_OK</span></span>|<span data-ttu-id="2af0f-114">`celt`elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="2af0f-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="2af0f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2af0f-115">S_FALSE</span></span>|<span data-ttu-id="2af0f-116">Méně než `celt` byly vráceny elementy, které označuje, že výčtu je kompletní.</span><span class="sxs-lookup"><span data-stu-id="2af0f-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2af0f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2af0f-117">Requirements</span></span>  
 <span data-ttu-id="2af0f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af0f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af0f-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2af0f-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2af0f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af0f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af0f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af0f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af0f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2af0f-122">See Also</span></span>  
 [<span data-ttu-id="2af0f-123">Icorprofilerthreadenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2af0f-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="2af0f-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2af0f-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
