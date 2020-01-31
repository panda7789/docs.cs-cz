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
ms.openlocfilehash: 2f305852ae218417aa1f4d4fe9d2076c0163fd60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865269"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="ae2fb-102">ICorProfilerCallback4::MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ae2fb-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="ae2fb-103">Volá se, aby se nahlásilo nové rozložení objektů v haldě v důsledku komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="ae2fb-104">Tato metoda je volána, pokud profiler implementoval rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ae2fb-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="ae2fb-105">Toto zpětné volání nahrazuje metodu [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) , protože může vykazovat větší rozsahy objektů, jejichž délka překračuje, co může být vyjádřeno v ulong.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-105">This callback replaces the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2fb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae2fb-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae2fb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae2fb-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="ae2fb-108">pro Počet bloků souvislých objektů, které byly přesunuty jako výsledek komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="ae2fb-109">To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost polí `oldObjectIDRangeStart`, `newObjectIDRangeStart`a `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="ae2fb-110">Další tři argumenty `MovedReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="ae2fb-111">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`a `cObjectIDRangeLength[i]` všechny se týkají jednoho bloku souvislých objektů.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="ae2fb-112">pro Pole hodnot `ObjectID`, z nichž každá je stará (před uvolněním paměti) počáteční adresou bloku souvislých, živých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="ae2fb-113">pro Pole hodnot `ObjectID`, z nichž každá je novou (po uvolnění paměti), která začíná adresou bloku souvislých objektů, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="ae2fb-114">pro Pole celých čísel, z nichž každá je velikost bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="ae2fb-115">Pro každý blok, na který je odkazováno v polích `oldObjectIDRangeStart` a `newObjectIDRangeStart`, je zadána velikost.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae2fb-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae2fb-116">Remarks</span></span>  
 <span data-ttu-id="ae2fb-117">Komprimace systému uvolňování paměti uvolní paměť, která je obsazená mrtvými objekty, a zkomprimuje uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="ae2fb-118">V důsledku toho mohou být živé objekty přesunuty v rámci haldy a `ObjectID` hodnoty distribuované předchozími oznámeními se mohou změnit.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="ae2fb-119">Předpokládejme, že existující hodnota `ObjectID` (`oldObjectID`) leží v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="ae2fb-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="ae2fb-120">V tomto případě je posunutí od začátku rozsahu na začátek objektu následující:</span><span class="sxs-lookup"><span data-stu-id="ae2fb-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="ae2fb-121">Pro libovolnou hodnotu `i`, která je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="ae2fb-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="ae2fb-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="ae2fb-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="ae2fb-123">novou `ObjectID` můžete vypočítat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ae2fb-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="ae2fb-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="ae2fb-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="ae2fb-125">Žádná z hodnot `ObjectID` předaných `MovedReferences2` nejsou během samotného zpětného volání platná, protože systém uvolňování paměti může být uprostřed přesunutí objektů ze starých umístění do nových umístění.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="ae2fb-126">Proto by se profilery neměly pokoušet prozkoumat objekty během volání `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="ae2fb-127">Zpětné volání [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) označuje, že všechny objekty byly přesunuty do jejich nových umístění a lze provést kontrolu.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="ae2fb-128">Pokud profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , je metoda `MovedReferences2` volána před metodou [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) , ale pouze v případě, že se metoda `MovedReferences2` úspěšně vrátí.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="ae2fb-129">Profilery mohou vracet hodnotu HRESULT, která označuje selhání z metody `MovedReferences2`, aby se předešlo volání druhé metody.</span><span class="sxs-lookup"><span data-stu-id="ae2fb-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae2fb-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae2fb-130">Requirements</span></span>  
 <span data-ttu-id="ae2fb-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae2fb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae2fb-132">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ae2fb-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae2fb-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ae2fb-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae2fb-134">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae2fb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2fb-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae2fb-135">See also</span></span>

- [<span data-ttu-id="ae2fb-136">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae2fb-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ae2fb-137">MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="ae2fb-137">MovedReferences Method</span></span>](icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="ae2fb-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae2fb-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="ae2fb-139">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ae2fb-139">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ae2fb-140">Profilace</span><span class="sxs-lookup"><span data-stu-id="ae2fb-140">Profiling</span></span>](index.md)
