---
title: ICorProfilerCallback4::SurvivingReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb260030914de211d227342e497daa3db287c9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758071"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="684a4-102">ICorProfilerCallback4::SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="684a4-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="684a4-103">Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním.</span><span class="sxs-lookup"><span data-stu-id="684a4-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="684a4-104">Tato metoda je volána, pokud profiler implementoval [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="684a4-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="684a4-105">Nahradí tato zpětné volání [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co lze vyjádřit v typu ULONG.</span><span class="sxs-lookup"><span data-stu-id="684a4-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684a4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="684a4-106">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="684a4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="684a4-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="684a4-108">[in] Počet bloků souvislých objektů, které zůstat naživu při uvolňování nekompaktním v důsledku.</span><span class="sxs-lookup"><span data-stu-id="684a4-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="684a4-109">To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` pole, které úložiště `ObjectID` a délku, pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="684a4-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="684a4-110">Následující dva argumenty `SurvivingReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="684a4-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="684a4-111">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týkají stejný blok souvislé objektů.</span><span class="sxs-lookup"><span data-stu-id="684a4-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="684a4-112">[in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="684a4-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="684a4-113">[in] Pole celých čísel, z nichž každý je velikost bloku zbývající souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="684a4-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="684a4-114">Zadat velikost pro každý blok, na který odkazuje `objectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="684a4-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="684a4-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="684a4-115">Remarks</span></span>  
 <span data-ttu-id="684a4-116">Prvky `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován takto k určení, zda objekt zůstat naživu kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="684a4-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="684a4-117">Předpokládejme, že `ObjectID` hodnotu (`ObjectID`) najdete v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="684a4-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="684a4-118">Jakoukoli hodnotu z `i` , který je v následujícím rozsahu, objekt má zůstat naživu při uvolňování paměti kolekce:</span><span class="sxs-lookup"><span data-stu-id="684a4-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="684a4-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="684a4-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="684a4-120">Uvolnění nekompaktním uvolňuje paměť obsazenou neživými "" objekty, ale ne compact toto uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="684a4-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="684a4-121">V důsledku toho paměti se vrátí do haldy, ale žádné objekty "živé" přesunou.</span><span class="sxs-lookup"><span data-stu-id="684a4-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="684a4-122">Common language runtime (CLR) zavolá `SurvivingReferences2` pro nekompaktním kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="684a4-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="684a4-123">Pro uvolnění komprimaci [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) je použita místo ní.</span><span class="sxs-lookup"><span data-stu-id="684a4-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="684a4-124">Jeden uvolňování paměti může být komprimaci pro jeden generování a nekompaktním dalších.</span><span class="sxs-lookup"><span data-stu-id="684a4-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="684a4-125">Pro uvolnění paměti na žádné konkrétní generování, profiler obdrží, buď `SurvivingReferences2` zpětného volání nebo [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zpětné volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="684a4-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="684a4-126">Více `SurvivingReferences2` zpětná volání může přijmout během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více zpětných volání během uvolnění paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="684a4-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="684a4-127">V případě více zpětných volání během uvolňování paměti informace jsou kumulativní; všechny odkazy, které jsou hlášeny v libovolném `SurvivingReferences2` zpětného volání byly zachovány při uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="684a4-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="684a4-128">Pokud profiler implementuje oba [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `SurvivingReferences2` metoda je volána před provedením [ICorProfilerCallback2:: Survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale pouze v případě `SurvivingReferences2` úspěšně vrátí.</span><span class="sxs-lookup"><span data-stu-id="684a4-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="684a4-129">Profilovací programy mohou vrátit HRESULT označující selhání z `SurvivingReferences2` metoda Vyhněte se volání druhá metoda.</span><span class="sxs-lookup"><span data-stu-id="684a4-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="684a4-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="684a4-130">Requirements</span></span>  
 <span data-ttu-id="684a4-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="684a4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="684a4-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="684a4-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="684a4-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="684a4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="684a4-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="684a4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684a4-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="684a4-135">See also</span></span>

- [<span data-ttu-id="684a4-136">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="684a4-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="684a4-137">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="684a4-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="684a4-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="684a4-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
