---
title: "ICorProfilerModuleEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7331c5221de1dc1bfdbbce77f8c40f4fbc95aea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="22f1e-102">ICorProfilerModuleEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="22f1e-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="22f1e-103">Posune kurzor enumerátor z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="22f1e-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22f1e-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22f1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22f1e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="22f1e-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="22f1e-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22f1e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22f1e-107">Return Value</span></span>  
 <span data-ttu-id="22f1e-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="22f1e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="22f1e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22f1e-109">HRESULT</span></span>|<span data-ttu-id="22f1e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="22f1e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22f1e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="22f1e-111">S_OK</span></span>|<span data-ttu-id="22f1e-112">`celt`elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="22f1e-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="22f1e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="22f1e-113">S_FALSE</span></span>|<span data-ttu-id="22f1e-114">Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="22f1e-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f1e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22f1e-115">Remarks</span></span>  
 <span data-ttu-id="22f1e-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="22f1e-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f1e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22f1e-117">Requirements</span></span>  
 <span data-ttu-id="22f1e-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f1e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f1e-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22f1e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22f1e-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22f1e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22f1e-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f1e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f1e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="22f1e-122">See Also</span></span>  
 [<span data-ttu-id="22f1e-123">Icorprofilermoduleenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22f1e-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="22f1e-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="22f1e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
