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
ms.openlocfilehash: af6aab2483f0e92dc20936fe2b01e12590d99ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455367"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="b4d8d-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="b4d8d-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="b4d8d-103">Posune kurzor enumerátor z aktuálního umístění tak, aby přeskočil zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4d8d-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4d8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4d8d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b4d8d-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4d8d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4d8d-107">Return Value</span></span>  
 <span data-ttu-id="b4d8d-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b4d8d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4d8d-109">HRESULT</span></span>|<span data-ttu-id="b4d8d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b4d8d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4d8d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4d8d-111">S_OK</span></span>|<span data-ttu-id="b4d8d-112">`celt` elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="b4d8d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b4d8d-113">S_FALSE</span></span>|<span data-ttu-id="b4d8d-114">Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d8d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4d8d-115">Remarks</span></span>  
 <span data-ttu-id="b4d8d-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d8d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4d8d-117">Requirements</span></span>  
 <span data-ttu-id="b4d8d-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d8d-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4d8d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4d8d-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d8d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d8d-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d8d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d8d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4d8d-122">See Also</span></span>  
 [<span data-ttu-id="b4d8d-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4d8d-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="b4d8d-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b4d8d-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
