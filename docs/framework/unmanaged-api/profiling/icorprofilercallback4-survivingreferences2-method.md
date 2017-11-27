---
title: "ICorProfilerCallback4::SurvivingReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ced8542d2e84b6c317e20d7ff440e6c159383bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="efc37-102">ICorProfilerCallback4::SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="efc37-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="efc37-103">Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi.</span><span class="sxs-lookup"><span data-stu-id="efc37-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="efc37-104">Tato metoda je volána, pokud má implementovaný profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efc37-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="efc37-105">Nahradí tato zpětného volání [icorprofilercallback2::survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metoda, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co může být vyjádřený v typu ULONG.</span><span class="sxs-lookup"><span data-stu-id="efc37-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc37-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efc37-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efc37-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc37-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="efc37-108">[v] Počet bloků souvislý objektů, které zůstal naživu v důsledku uvolnění paměti kompresi.</span><span class="sxs-lookup"><span data-stu-id="efc37-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="efc37-109">To znamená, hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` maticových, které úložiště `ObjectID` a délky, v uvedeném pořadí, pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="efc37-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="efc37-110">Následující dva argumenty `SurvivingReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="efc37-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="efc37-111">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` na stejný blok souvislý objektů, které se týkají.</span><span class="sxs-lookup"><span data-stu-id="efc37-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="efc37-112">[v] Pole `ObjectID` hodnoty, z nichž každý je adresa počáteční blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="efc37-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="efc37-113">[v] Pole celých čísel, z nichž každý je velikost bloku hostujícího souvislý objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="efc37-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="efc37-114">Velikost je zadán pro každý blok, který se odkazuje v `objectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="efc37-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efc37-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efc37-115">Remarks</span></span>  
 <span data-ttu-id="efc37-116">Elementy `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován následujícím způsobem určit, zda objekt zůstal naživu uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="efc37-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="efc37-117">Předpokládáme, že `ObjectID` hodnotu (`ObjectID`) v rozmezí následující:</span><span class="sxs-lookup"><span data-stu-id="efc37-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="efc37-118">Pro všechny hodnotu `i` , je v následujícím rozsahu, objekt má zůstal naživu uvolnění paměti:</span><span class="sxs-lookup"><span data-stu-id="efc37-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="efc37-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="efc37-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="efc37-120">Uvolnění paměti kompresi získá paměť obsazená "neaktivní" objekty, ale není compact toto uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="efc37-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="efc37-121">V důsledku toho se vrátí halda paměti, ale žádné "živé" objekty přesunou.</span><span class="sxs-lookup"><span data-stu-id="efc37-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="efc37-122">Modul CLR (CLR) volá `SurvivingReferences2` pro kompresi jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="efc37-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="efc37-123">Pro komprimaci kolekce [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) nazývá místo.</span><span class="sxs-lookup"><span data-stu-id="efc37-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="efc37-124">Uvolňování paměti jednom může být komprimaci pro jedna generace a bez kompresi pro jinou.</span><span class="sxs-lookup"><span data-stu-id="efc37-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="efc37-125">Pro kolekci paměti na žádné konkrétní generování profileru obdrží, buď `SurvivingReferences2` zpětného volání nebo [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zpětného volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="efc37-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="efc37-126">Více `SurvivingReferences2` zpětná volání může být přijata během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více zpětná volání během uvolňování paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="efc37-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="efc37-127">V případě více zpětných volání během uvolňování paměti je informace kumulativní; všechny odkazy, které jsou hlášeny v žádném `SurvivingReferences2` zpětného volání, zůstanou platné i po uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="efc37-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="efc37-128">Pokud profileru implementuje i [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `SurvivingReferences2` metoda je volána před provedením [icorprofilercallback2 –:: Survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metoda, ale jenom v případě `SurvivingReferences2` vrátí úspěšně.</span><span class="sxs-lookup"><span data-stu-id="efc37-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="efc37-129">Profilery může vrátit HRESULT označující selhání z `SurvivingReferences2` metoda zrušení volání druhé metody.</span><span class="sxs-lookup"><span data-stu-id="efc37-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc37-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efc37-130">Requirements</span></span>  
 <span data-ttu-id="efc37-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc37-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc37-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efc37-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efc37-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efc37-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc37-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc37-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc37-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="efc37-135">See Also</span></span>  
 [<span data-ttu-id="efc37-136">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efc37-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="efc37-137">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efc37-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="efc37-138">Icorprofilercallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efc37-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
