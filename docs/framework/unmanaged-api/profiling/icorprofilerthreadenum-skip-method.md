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
ms.openlocfilehash: 4218faf1c324175424ab20305224f7f2fa51bb7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494212"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="a61ab-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="a61ab-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="a61ab-103">Posune kurzor čítače výčtu z aktuální pozice pro přeskočení zadaného počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="a61ab-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a61ab-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a61ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a61ab-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a61ab-106">pro Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="a61ab-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a61ab-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a61ab-107">Return Value</span></span>  
 <span data-ttu-id="a61ab-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="a61ab-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a61ab-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a61ab-109">HRESULT</span></span>|<span data-ttu-id="a61ab-110">Description</span><span class="sxs-lookup"><span data-stu-id="a61ab-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a61ab-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a61ab-111">S_OK</span></span>|<span data-ttu-id="a61ab-112">`celt`prvky se přeskočily.</span><span class="sxs-lookup"><span data-stu-id="a61ab-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="a61ab-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a61ab-113">S_FALSE</span></span>|<span data-ttu-id="a61ab-114">Méně než `celt` prvků bylo vynecháno, což znamená, že žádné další prvky nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a61ab-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a61ab-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a61ab-115">Remarks</span></span>  
 <span data-ttu-id="a61ab-116">Nová pozice kurzoru tohoto enumerátoru je (aktuální pozice) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="a61ab-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a61ab-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a61ab-117">Requirements</span></span>  
 <span data-ttu-id="a61ab-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a61ab-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a61ab-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a61ab-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a61ab-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a61ab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a61ab-121">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a61ab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61ab-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a61ab-122">See also</span></span>

- [<span data-ttu-id="a61ab-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a61ab-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a61ab-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a61ab-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
