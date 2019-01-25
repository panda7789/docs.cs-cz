---
title: ICorProfilerThreadEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25a6baea0cdd92d6d214ab8a697b0c00c44c42bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664574"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="4138a-102">ICorProfilerThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4138a-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="4138a-103">Získá zadaný počet souvislých vlákna z kolekce sekvenčních vláken, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4138a-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4138a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4138a-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4138a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4138a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4138a-106">[in] Počet vláken pro načtení.</span><span class="sxs-lookup"><span data-stu-id="4138a-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="4138a-107">[out] Pole `ThreadID` hodnot, z nichž každý představuje načtený vlákna.</span><span class="sxs-lookup"><span data-stu-id="4138a-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4138a-108">[out] Ukazatel na počet skutečně vrácených v vláken `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="4138a-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4138a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4138a-109">Return Value</span></span>  
 <span data-ttu-id="4138a-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="4138a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4138a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4138a-111">HRESULT</span></span>|<span data-ttu-id="4138a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4138a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4138a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4138a-113">S_OK</span></span>|<span data-ttu-id="4138a-114">`celt` elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="4138a-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="4138a-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4138a-115">S_FALSE</span></span>|<span data-ttu-id="4138a-116">Méně než `celt` prvky byly vráceny, což znamená, že dokončení výčtu.</span><span class="sxs-lookup"><span data-stu-id="4138a-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4138a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4138a-117">Requirements</span></span>  
 <span data-ttu-id="4138a-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4138a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4138a-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4138a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4138a-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4138a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4138a-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4138a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4138a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4138a-122">See also</span></span>
- [<span data-ttu-id="4138a-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4138a-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="4138a-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4138a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
