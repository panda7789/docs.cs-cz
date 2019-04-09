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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173339"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="a8782-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="a8782-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="a8782-103">Posune kurzor čítače výčtu ze své aktuální pozici pro přeskočení zadaný počet prvků.</span><span class="sxs-lookup"><span data-stu-id="a8782-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8782-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8782-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8782-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8782-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a8782-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="a8782-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8782-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8782-107">Return Value</span></span>  
 <span data-ttu-id="a8782-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="a8782-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a8782-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8782-109">HRESULT</span></span>|<span data-ttu-id="a8782-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a8782-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8782-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8782-111">S_OK</span></span>|`celt` <span data-ttu-id="a8782-112">elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="a8782-112">elements were skipped.</span></span>|  
|<span data-ttu-id="a8782-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a8782-113">S_FALSE</span></span>|<span data-ttu-id="a8782-114">Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="a8782-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8782-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8782-115">Remarks</span></span>  
 <span data-ttu-id="a8782-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="a8782-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8782-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8782-117">Requirements</span></span>  
 <span data-ttu-id="a8782-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8782-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8782-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8782-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8782-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8782-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a8782-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a8782-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8782-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8782-122">See also</span></span>

- [<span data-ttu-id="a8782-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8782-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a8782-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a8782-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
