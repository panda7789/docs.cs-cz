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
ms.openlocfilehash: 7dede4e5af702f1b86b430450db4a669c326c062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131065"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="25dfa-102">ICorDebugILCode2::GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="25dfa-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="25dfa-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="25dfa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="25dfa-104">Vrátí mapu z posunu s instrumentací prostředního jazyka (IL) na původní posunutí metody IL pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="25dfa-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25dfa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25dfa-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25dfa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="25dfa-106">Parameters</span></span>  
 <span data-ttu-id="25dfa-107">cMap</span><span class="sxs-lookup"><span data-stu-id="25dfa-107">cMap</span></span>  
 <span data-ttu-id="25dfa-108">pro Kapacita úložiště pole `map`.</span><span class="sxs-lookup"><span data-stu-id="25dfa-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="25dfa-109">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="25dfa-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="25dfa-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="25dfa-110">pcMap</span></span>  
 <span data-ttu-id="25dfa-111">mimo Počet hodnot COR_IL_MAP zapsaných do pole mapy.</span><span class="sxs-lookup"><span data-stu-id="25dfa-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="25dfa-112">map</span><span class="sxs-lookup"><span data-stu-id="25dfa-112">map</span></span>  
 <span data-ttu-id="25dfa-113">mimo Pole hodnot COR_IL_MAP, které poskytují informace o mapování z instrumentované úrovně IL na IL původní metody.</span><span class="sxs-lookup"><span data-stu-id="25dfa-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25dfa-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25dfa-114">Remarks</span></span>  
 <span data-ttu-id="25dfa-115">Pokud profiler nastaví mapování voláním metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , ladicí program může zavolat tuto metodu, aby načetla mapování a použila mapování interně při výpočtu posunu Il pro trasování a proměnnou zásobníku. životnosti.</span><span class="sxs-lookup"><span data-stu-id="25dfa-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="25dfa-116">Pokud je `cMap` 0 a `pcMap` není**null**, `pcMap` je nastaveno na počet dostupných hodnot COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="25dfa-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="25dfa-117">Pokud `cMap` není nula, představuje kapacitu úložiště `map` pole.</span><span class="sxs-lookup"><span data-stu-id="25dfa-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="25dfa-118">Když se metoda vrátí, `map` obsahuje maximum `cMap`ch položek a `pcMap` je nastavená na počet hodnot COR_IL_MAP skutečně zapsaných do pole `map`.</span><span class="sxs-lookup"><span data-stu-id="25dfa-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="25dfa-119">Pokud nedošlo k instrumentaci IL nebo mapování nebylo poskytnuto profilerem, vrátí tato metoda `S_OK` a nastaví `pcMap` na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="25dfa-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25dfa-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25dfa-120">Requirements</span></span>  
 <span data-ttu-id="25dfa-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25dfa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25dfa-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25dfa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25dfa-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25dfa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25dfa-124">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25dfa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25dfa-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25dfa-125">See also</span></span>

- [<span data-ttu-id="25dfa-126">ICorProfilerInfo:: SetILInstrumentedCodeMap –</span><span class="sxs-lookup"><span data-stu-id="25dfa-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="25dfa-127">ICorDebugILCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25dfa-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="25dfa-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="25dfa-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
