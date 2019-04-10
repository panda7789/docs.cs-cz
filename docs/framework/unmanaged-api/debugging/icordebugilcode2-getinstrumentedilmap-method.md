---
title: ICorDebugILCode2::GetInstrumentedILMap – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4197b018ea85402762a8591b40f3503c02af3974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222871"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="94f98-102">ICorDebugILCode2::GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="94f98-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="94f98-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="94f98-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="94f98-104">Vrátí mapu z posunů instrumentována profiler (IL intermediate language) na původní metodu IL posunutí pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="94f98-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94f98-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94f98-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94f98-106">Parameters</span></span>  
 <span data-ttu-id="94f98-107">Cmap –</span><span class="sxs-lookup"><span data-stu-id="94f98-107">cMap</span></span>  
 <span data-ttu-id="94f98-108">[in] Kapacita úložiště `map` pole.</span><span class="sxs-lookup"><span data-stu-id="94f98-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="94f98-109">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="94f98-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="94f98-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="94f98-110">pcMap</span></span>  
 <span data-ttu-id="94f98-111">[out] Počet hodnot cor_il_map – zapsána do pole mapování.</span><span class="sxs-lookup"><span data-stu-id="94f98-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="94f98-112">map</span><span class="sxs-lookup"><span data-stu-id="94f98-112">map</span></span>  
 <span data-ttu-id="94f98-113">[out] Pole cor_il_map – hodnoty, které poskytují informace o mapování z profileru instrumentována IL IL původní metodu.</span><span class="sxs-lookup"><span data-stu-id="94f98-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94f98-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94f98-114">Remarks</span></span>  
 <span data-ttu-id="94f98-115">Pokud profiler nastaví mapování voláním [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metoda, ladicí program může volat tuto metodu načíst mapování a mapování používají interně při výpočtu IL dorovnání u zásobníku trasování a životnost proměnné.</span><span class="sxs-lookup"><span data-stu-id="94f98-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="94f98-116">Pokud `cMap` je 0 a `pcMap` jinou hodnotu než**null**, `pcMap` je nastavena na počet dostupných hodnot cor_il_map –.</span><span class="sxs-lookup"><span data-stu-id="94f98-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="94f98-117">Pokud `cMap` je nenulová, představuje kapacitu úložiště `map` pole.</span><span class="sxs-lookup"><span data-stu-id="94f98-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="94f98-118">Po návratu metody `map` obsahuje určitý počet `cMap` položky, a `pcMap` je nastavena na počet aktuálně zapsaných do hodnoty cor_il_map – `map` pole.</span><span class="sxs-lookup"><span data-stu-id="94f98-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="94f98-119">Pokud nebyl byla instrumentována IL nebo pomocí profileru nebylo zadáno mapování, vrátí tato metoda `S_OK` a nastaví `pcMap` na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="94f98-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f98-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94f98-120">Requirements</span></span>  
 <span data-ttu-id="94f98-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94f98-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94f98-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94f98-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94f98-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94f98-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="94f98-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="94f98-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94f98-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94f98-125">See also</span></span>

- [<span data-ttu-id="94f98-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="94f98-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="94f98-127">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="94f98-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="94f98-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94f98-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
