---
title: ICorProfilerModuleEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: b48b782b7c8be35bfb815d72758f0bc316fb2114
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494719"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="93f57-102">ICorProfilerModuleEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="93f57-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="93f57-103">Posune kurzor čítače výčtu z aktuální pozice tak, aby byl zadaný počet prvků vynechán.</span><span class="sxs-lookup"><span data-stu-id="93f57-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93f57-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93f57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93f57-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="93f57-106">pro Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="93f57-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93f57-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93f57-107">Return Value</span></span>  
 <span data-ttu-id="93f57-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="93f57-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="93f57-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93f57-109">HRESULT</span></span>|<span data-ttu-id="93f57-110">Description</span><span class="sxs-lookup"><span data-stu-id="93f57-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93f57-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="93f57-111">S_OK</span></span>|<span data-ttu-id="93f57-112">`celt`prvky se přeskočily.</span><span class="sxs-lookup"><span data-stu-id="93f57-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="93f57-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="93f57-113">S_FALSE</span></span>|<span data-ttu-id="93f57-114">Méně než `celt` prvků bylo vynecháno, což znamená, že žádné další prvky nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="93f57-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93f57-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93f57-115">Remarks</span></span>  
 <span data-ttu-id="93f57-116">Nová pozice kurzoru tohoto enumerátoru je (aktuální pozice) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="93f57-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f57-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93f57-117">Requirements</span></span>  
 <span data-ttu-id="93f57-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f57-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f57-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93f57-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93f57-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93f57-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f57-121">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f57-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f57-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93f57-122">See also</span></span>

- [<span data-ttu-id="93f57-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93f57-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="93f57-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="93f57-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
