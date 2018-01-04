---
title: "ICorProfilerThreadEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1840722a250dd627a5214700dca95c48aa2e8d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="20c46-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="20c46-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="20c46-103">Posune kurzor enumerátor z aktuálního umístění tak, aby přeskočil zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="20c46-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20c46-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20c46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20c46-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="20c46-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="20c46-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20c46-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="20c46-107">Return Value</span></span>  
 <span data-ttu-id="20c46-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="20c46-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="20c46-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20c46-109">HRESULT</span></span>|<span data-ttu-id="20c46-110">Popis</span><span class="sxs-lookup"><span data-stu-id="20c46-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20c46-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20c46-111">S_OK</span></span>|<span data-ttu-id="20c46-112">`celt`elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="20c46-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="20c46-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="20c46-113">S_FALSE</span></span>|<span data-ttu-id="20c46-114">Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="20c46-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20c46-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20c46-115">Remarks</span></span>  
 <span data-ttu-id="20c46-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="20c46-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c46-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20c46-117">Requirements</span></span>  
 <span data-ttu-id="20c46-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20c46-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c46-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20c46-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20c46-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20c46-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20c46-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c46-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c46-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="20c46-122">See Also</span></span>  
 [<span data-ttu-id="20c46-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20c46-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="20c46-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="20c46-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
