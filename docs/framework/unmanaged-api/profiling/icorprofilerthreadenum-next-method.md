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
ms.openlocfilehash: 37d1acfa70a1a2b2c18fb34fb5d6024f3b61e2ab
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494342"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="976fd-102">ICorProfilerThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="976fd-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="976fd-103">Získá zadaný počet souvislých vláken ze sekvenční kolekce vláken počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="976fd-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="976fd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="976fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="976fd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="976fd-106">pro Počet vláken, která se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="976fd-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="976fd-107">mimo Pole `ThreadID` hodnot, z nichž každý představuje načtené vlákno.</span><span class="sxs-lookup"><span data-stu-id="976fd-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="976fd-108">mimo Ukazatel na počet vláken skutečně vrácených v `ids` poli.</span><span class="sxs-lookup"><span data-stu-id="976fd-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="976fd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="976fd-109">Return Value</span></span>  
 <span data-ttu-id="976fd-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="976fd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="976fd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="976fd-111">HRESULT</span></span>|<span data-ttu-id="976fd-112">Description</span><span class="sxs-lookup"><span data-stu-id="976fd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="976fd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="976fd-113">S_OK</span></span>|<span data-ttu-id="976fd-114">`celt`prvky byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="976fd-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="976fd-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="976fd-115">S_FALSE</span></span>|<span data-ttu-id="976fd-116">`celt`Bylo vráceno méně než prvků, což indikuje, že byl výčet dokončen.</span><span class="sxs-lookup"><span data-stu-id="976fd-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="976fd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="976fd-117">Requirements</span></span>  
 <span data-ttu-id="976fd-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="976fd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="976fd-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="976fd-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="976fd-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="976fd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="976fd-121">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="976fd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976fd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="976fd-122">See also</span></span>

- [<span data-ttu-id="976fd-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="976fd-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="976fd-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="976fd-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
