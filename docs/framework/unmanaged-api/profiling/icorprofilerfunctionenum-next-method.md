---
title: "ICorProfilerFunctionEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6cf37beced15305de60c3f57edb701adc7379a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="e5b29-102">ICorProfilerFunctionEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b29-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="e5b29-103">Získá zadaný počet souvislý funkce z sekvenční kolekce funkcí, začínající na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="e5b29-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5b29-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5b29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5b29-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e5b29-106">[v] Počet funkcí pro načtení.</span><span class="sxs-lookup"><span data-stu-id="e5b29-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="e5b29-107">[out] Pole `COR_PRF_FUNCTION` hodnoty, z nichž každý představuje načtené funkce.</span><span class="sxs-lookup"><span data-stu-id="e5b29-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e5b29-108">[out] Ukazatel na počet funkcí, které jsou aktuálně vrácenou `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="e5b29-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5b29-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5b29-109">Return Value</span></span>  
 <span data-ttu-id="e5b29-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="e5b29-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e5b29-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5b29-111">HRESULT</span></span>|<span data-ttu-id="e5b29-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e5b29-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5b29-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5b29-113">S_OK</span></span>|<span data-ttu-id="e5b29-114">`celt`elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="e5b29-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="e5b29-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e5b29-115">S_FALSE</span></span>|<span data-ttu-id="e5b29-116">Méně než `celt` byly vráceny elementy, které označuje, že výčtu je kompletní.</span><span class="sxs-lookup"><span data-stu-id="e5b29-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5b29-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5b29-117">Requirements</span></span>  
 <span data-ttu-id="e5b29-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b29-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b29-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5b29-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5b29-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5b29-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5b29-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b29-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b29-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5b29-122">See Also</span></span>  
 [<span data-ttu-id="e5b29-123">Icorprofilerfunctionenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5b29-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="e5b29-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e5b29-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
