---
title: "ICorProfilerCallback4::MovedReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.MovedReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8137d944081475095509150cce84a611b7030eb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="f6a3d-102">ICorProfilerCallback4::MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f6a3d-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="f6a3d-103">Volá se pro sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="f6a3d-104">Tato metoda je volána, pokud má implementovaný profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="f6a3d-105">Nahradí tato zpětného volání [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metoda, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co může být vyjádřený v typu ULONG.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a3d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6a3d-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6a3d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6a3d-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="f6a3d-108">[v] Počet bloků souvislý objektů, které přesunout v důsledku komprimaci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="f6a3d-109">To znamená, hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="f6a3d-110">Následující tři argumenty `MovedReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="f6a3d-111">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny jeden blok souvislý objektů, které se týkají.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="f6a3d-112">[v] Pole `ObjectID` hodnoty, z nichž každý je starý (předběžné uvolňování paměti) počáteční adresa blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="f6a3d-113">[v] Pole `ObjectID` hodnoty, z nichž každý je nové počáteční adresa (po uvolnění paměti) blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="f6a3d-114">[v] Pole celých čísel, z nichž každý je velikost bloku souvislý objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="f6a3d-115">Velikost je zadán pro každý blok, který se odkazuje v `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6a3d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6a3d-116">Remarks</span></span>  
 <span data-ttu-id="f6a3d-117">Komprimaci uvolňování paměti získá paměť obsazená neaktivní objekty a zkomprimuje uvolní místo.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="f6a3d-118">V důsledku toho může přesunout živé objekty v rámci haldy, a `ObjectID` mohou změnit hodnoty distribuovat předchozí oznámení.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="f6a3d-119">Předpokládáme, že existující `ObjectID` hodnotu (`oldObjectID`) v rozmezí následující:</span><span class="sxs-lookup"><span data-stu-id="f6a3d-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="f6a3d-120">Posun od začátku rozsahu na začátek objekt v tomto případě je následující:</span><span class="sxs-lookup"><span data-stu-id="f6a3d-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="f6a3d-121">Pro všechny hodnotu `i` , je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="f6a3d-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="f6a3d-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="f6a3d-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="f6a3d-123">můžete vypočítat nové `ObjectID` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6a3d-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="f6a3d-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="f6a3d-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="f6a3d-125">Žádná z `ObjectID` hodnotu předanou `MovedReferences2` jsou platné během zpětného volání sebe, protože systém uvolňování paměti může být uprostřed přesun objektů z původního umístění do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="f6a3d-126">Proto profilery neměli zkontrolovat objekty během `MovedReferences2` volání.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="f6a3d-127">A [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání označuje, že všechny objekty byly přesunuty do nového umístění a provádět kontroly.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="f6a3d-128">Pokud profileru implementuje i [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `MovedReferences2` metoda je volána před provedením [icorprofilercallback –:: Movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metoda, ale jenom Pokud `MovedReferences2` metoda vrátí úspěšně.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="f6a3d-129">Profilery může vrátit HRESULT označující selhání z `MovedReferences2` metoda, aby se zabránilo volání druhé metody.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6a3d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6a3d-130">Requirements</span></span>  
 <span data-ttu-id="f6a3d-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a3d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a3d-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6a3d-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6a3d-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6a3d-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6a3d-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a3d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a3d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6a3d-135">See Also</span></span>  
 [<span data-ttu-id="f6a3d-136">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6a3d-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f6a3d-137">Movedreferences – metoda</span><span class="sxs-lookup"><span data-stu-id="f6a3d-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)  
 [<span data-ttu-id="f6a3d-138">Icorprofilercallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6a3d-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="f6a3d-139">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f6a3d-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f6a3d-140">Profilace</span><span class="sxs-lookup"><span data-stu-id="f6a3d-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
