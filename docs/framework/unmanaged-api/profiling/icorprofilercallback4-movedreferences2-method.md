---
title: ICorProfilerCallback4::MovedReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d368c88503853d0620f28f02f88a6d887c1aa681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597820"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="66267-102">ICorProfilerCallback4::MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="66267-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="66267-103">Volá se, aby sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="66267-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="66267-104">Tato metoda je volána, pokud profiler implementoval [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66267-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="66267-105">Nahradí tato zpětné volání [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co lze vyjádřit v typu ULONG.</span><span class="sxs-lookup"><span data-stu-id="66267-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66267-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66267-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="66267-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="66267-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="66267-108">[in] Počet bloků souvislých objektů, které přesunout v důsledku komprimaci kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="66267-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="66267-109">To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.</span><span class="sxs-lookup"><span data-stu-id="66267-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="66267-110">Následující tři argumenty `MovedReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="66267-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="66267-111">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny týkají jeden blok souvislé objektů.</span><span class="sxs-lookup"><span data-stu-id="66267-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="66267-112">[in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé původní (předběžné uvolňování), živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="66267-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="66267-113">[in] Pole `ObjectID` hodnot, z nichž každý je novou počáteční adresu (po uvolňování) blok souvislé, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="66267-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="66267-114">[in] Pole celých čísel, z nichž každý je velikost bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="66267-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="66267-115">Zadat velikost pro každý blok, na který odkazuje `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="66267-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66267-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66267-116">Remarks</span></span>  
 <span data-ttu-id="66267-117">Komprimace systému uvolňování paměti získá paměť obsazené nepoužívanými objekty a zkomprimuje uvolní místo.</span><span class="sxs-lookup"><span data-stu-id="66267-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="66267-118">V důsledku toho mohou být přesunuty živé objekty v rámci haldy, a `ObjectID` může změnit hodnoty distribuuje společnost předchozí oznámení.</span><span class="sxs-lookup"><span data-stu-id="66267-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="66267-119">Předpokládejme, že existující `ObjectID` hodnotu (`oldObjectID`) najdete v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="66267-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="66267-120">Posun od začátku rozsahu na začátek objekt v tomto případě je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="66267-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="66267-121">Jakoukoli hodnotu z `i` , který je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="66267-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="66267-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="66267-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="66267-123">můžete vypočítat nové `ObjectID` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="66267-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="66267-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="66267-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="66267-125">Žádná z `ObjectID` hodnotu předanou `MovedReferences2` jsou platné během zpětného volání, protože systému uvolňování paměti může být uvnitř přesun objektů ze staré umístění do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="66267-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="66267-126">Proto by se neměly pokoušet profilery pro kontrolu objektů během `MovedReferences2` volání.</span><span class="sxs-lookup"><span data-stu-id="66267-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="66267-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání znamená, že se přesunuly všechny objekty do jejich nových umístění a provést kontrolu.</span><span class="sxs-lookup"><span data-stu-id="66267-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="66267-128">Pokud profiler implementuje oba [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `MovedReferences2` metoda je volána před provedením [ICorProfilerCallback:: Movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ale pouze tehdy, pokud `MovedReferences2` metoda skončí úspěšně.</span><span class="sxs-lookup"><span data-stu-id="66267-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="66267-129">Profilovací programy mohou vrátit HRESULT označující selhání z `MovedReferences2` metodu, vyhněte se volání druhá metoda.</span><span class="sxs-lookup"><span data-stu-id="66267-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66267-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66267-130">Requirements</span></span>  
 <span data-ttu-id="66267-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66267-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66267-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66267-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66267-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66267-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66267-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66267-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66267-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66267-135">See also</span></span>

- [<span data-ttu-id="66267-136">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66267-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="66267-137">MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="66267-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="66267-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66267-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="66267-139">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="66267-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="66267-140">Profilace</span><span class="sxs-lookup"><span data-stu-id="66267-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
