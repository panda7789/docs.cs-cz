---
title: ICorProfilerCallback2::SurvivingReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191299"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="82a53-102">ICorProfilerCallback2::SurvivingReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="82a53-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="82a53-103">Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním.</span><span class="sxs-lookup"><span data-stu-id="82a53-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82a53-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="82a53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82a53-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="82a53-106">[in] Počet bloků souvislých objektů, které zůstat naživu při uvolňování nekompaktním v důsledku.</span><span class="sxs-lookup"><span data-stu-id="82a53-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="82a53-107">To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` pole, které úložiště `ObjectID` a délku, pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="82a53-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="82a53-108">Následující dva argumenty `SurvivingReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="82a53-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="82a53-109">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týkají stejný blok souvislé objektů.</span><span class="sxs-lookup"><span data-stu-id="82a53-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="82a53-110">[in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="82a53-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="82a53-111">[in] Pole celých čísel, z nichž každý je velikost bloku zbývající souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="82a53-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="82a53-112">Zadat velikost pro každý blok, na který odkazuje `objectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="82a53-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82a53-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82a53-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82a53-114">Tato metoda oznamuje velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="82a53-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="82a53-115">Pro objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::survivingreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="82a53-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="82a53-116">Prvky `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován takto k určení, zda objekt zůstat naživu kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82a53-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="82a53-117">Předpokládejme, že `ObjectID` hodnotu (`ObjectID`) najdete v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="82a53-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="82a53-118">Jakoukoli hodnotu z `i` , který je v následujícím rozsahu, objekt má zůstat naživu při uvolňování paměti kolekce:</span><span class="sxs-lookup"><span data-stu-id="82a53-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="82a53-119">0 <= `i` < </span><span class="sxs-lookup"><span data-stu-id="82a53-119">0 <= `i` < </span></span>`cSurvivingObjectIDRanges`  
  
 <span data-ttu-id="82a53-120">Uvolnění nekompaktním uvolňuje paměť obsazenou neživými "" objekty, ale ne compact toto uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="82a53-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="82a53-121">V důsledku toho paměti se vrátí do haldy, ale žádné objekty "živé" přesunou.</span><span class="sxs-lookup"><span data-stu-id="82a53-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="82a53-122">Common language runtime (CLR) zavolá `SurvivingReferences` pro nekompaktním kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82a53-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="82a53-123">Pro uvolnění komprimaci [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) je použita místo ní.</span><span class="sxs-lookup"><span data-stu-id="82a53-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="82a53-124">Jeden uvolňování paměti může být komprimaci pro jeden generování a nekompaktním dalších.</span><span class="sxs-lookup"><span data-stu-id="82a53-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="82a53-125">Pro uvolnění paměti na žádné konkrétní generování, profiler obdrží, buď `SurvivingReferences` zpětného volání nebo `MovedReferences` zpětné volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="82a53-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="82a53-126">Více `SurvivingReferences` zpětná volání může přijmout během konkrétní uvolňování paměti, z důvodu omezené vnitřní vyrovnávací paměť, více vláken reporting v případě uvolnění paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="82a53-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="82a53-127">V případě více zpětných volání během uvolňování paměti je kumulativní informace – všechny odkazy, které jsou hlášeny v libovolném `SurvivingReferences` zpětného volání byly zachovány při uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82a53-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82a53-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82a53-128">Requirements</span></span>  
 <span data-ttu-id="82a53-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82a53-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82a53-130">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82a53-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82a53-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82a53-131">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="82a53-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="82a53-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82a53-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82a53-133">See also</span></span>

- [<span data-ttu-id="82a53-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82a53-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="82a53-135">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82a53-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="82a53-136">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="82a53-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
