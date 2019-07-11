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
ms.openlocfilehash: 2c394c2b17404351bd0813ab1eb21230a1edd9de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781092"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="0a77e-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0a77e-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="0a77e-103">Posune kurzor čítače výčtu ze své aktuální pozici pro přeskočení zadaný počet prvků.</span><span class="sxs-lookup"><span data-stu-id="0a77e-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a77e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a77e-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a77e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a77e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0a77e-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="0a77e-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a77e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a77e-107">Return Value</span></span>  
 <span data-ttu-id="0a77e-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0a77e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0a77e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a77e-109">HRESULT</span></span>|<span data-ttu-id="0a77e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0a77e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a77e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a77e-111">S_OK</span></span>|<span data-ttu-id="0a77e-112">`celt` elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="0a77e-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="0a77e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0a77e-113">S_FALSE</span></span>|<span data-ttu-id="0a77e-114">Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="0a77e-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a77e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a77e-115">Remarks</span></span>  
 <span data-ttu-id="0a77e-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="0a77e-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a77e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a77e-117">Requirements</span></span>  
 <span data-ttu-id="0a77e-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a77e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a77e-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a77e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a77e-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a77e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a77e-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a77e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a77e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a77e-122">See also</span></span>

- [<span data-ttu-id="0a77e-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a77e-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="0a77e-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0a77e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
