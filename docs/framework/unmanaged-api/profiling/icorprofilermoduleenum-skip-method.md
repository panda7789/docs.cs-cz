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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9472013dcbbeef51753980348652b74c34172ce5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499209"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="8b7e2-102">ICorProfilerModuleEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="8b7e2-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="8b7e2-103">Posune kurzor enumerátor z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b7e2-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b7e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b7e2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8b7e2-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b7e2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b7e2-107">Return Value</span></span>  
 <span data-ttu-id="8b7e2-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8b7e2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b7e2-109">HRESULT</span></span>|<span data-ttu-id="8b7e2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8b7e2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b7e2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b7e2-111">S_OK</span></span>|<span data-ttu-id="8b7e2-112">`celt` elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="8b7e2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8b7e2-113">S_FALSE</span></span>|<span data-ttu-id="8b7e2-114">Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b7e2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b7e2-115">Remarks</span></span>  
 <span data-ttu-id="8b7e2-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="8b7e2-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7e2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b7e2-117">Requirements</span></span>  
 <span data-ttu-id="8b7e2-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b7e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7e2-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b7e2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b7e2-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b7e2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b7e2-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7e2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b7e2-122">See also</span></span>
- [<span data-ttu-id="8b7e2-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b7e2-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="8b7e2-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8b7e2-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
