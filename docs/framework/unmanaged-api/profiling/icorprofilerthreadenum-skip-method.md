---
title: ICorProfilerThreadEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cce96e8c6d046beba9e45c7121bf68444fd51c95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173339"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="e4f60-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="e4f60-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="e4f60-103">Posune kurzor čítače výčtu ze své aktuální pozici pro přeskočení zadaný počet prvků.</span><span class="sxs-lookup"><span data-stu-id="e4f60-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f60-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4f60-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e4f60-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="e4f60-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f60-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e4f60-107">Return Value</span></span>  
 <span data-ttu-id="e4f60-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="e4f60-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e4f60-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4f60-109">HRESULT</span></span>|<span data-ttu-id="e4f60-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e4f60-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4f60-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4f60-111">S_OK</span></span>|<span data-ttu-id="e4f60-112">`celt` elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="e4f60-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="e4f60-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e4f60-113">S_FALSE</span></span>|<span data-ttu-id="e4f60-114">Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="e4f60-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f60-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4f60-115">Remarks</span></span>  
 <span data-ttu-id="e4f60-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="e4f60-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f60-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4f60-117">Requirements</span></span>  
 <span data-ttu-id="e4f60-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f60-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f60-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4f60-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4f60-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4f60-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f60-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f60-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f60-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f60-122">See also</span></span>

- [<span data-ttu-id="e4f60-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4f60-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e4f60-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e4f60-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
