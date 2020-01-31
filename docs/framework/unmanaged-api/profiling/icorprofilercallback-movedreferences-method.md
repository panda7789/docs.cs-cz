---
title: ICorProfilerCallback::MovedReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 79fcaaba44956d90f9d074ade132dfc0bafd7d9e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866114"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="0c298-102">ICorProfilerCallback::MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="0c298-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="0c298-103">Volá se, aby se nahlásilo nové rozložení objektů v haldě v důsledku komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0c298-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c298-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c298-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c298-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c298-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="0c298-106">pro Počet bloků souvislých objektů, které byly přesunuty jako výsledek komprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0c298-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="0c298-107">To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost polí `oldObjectIDRangeStart`, `newObjectIDRangeStart`a `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="0c298-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="0c298-108">Další tři argumenty `MovedReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="0c298-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="0c298-109">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`a `cObjectIDRangeLength[i]` všechny se týkají jednoho bloku souvislých objektů.</span><span class="sxs-lookup"><span data-stu-id="0c298-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="0c298-110">pro Pole hodnot `ObjectID`, z nichž každá je stará (před uvolněním paměti) počáteční adresou bloku souvislých, živých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="0c298-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="0c298-111">pro Pole hodnot `ObjectID`, z nichž každá je novou (po uvolnění paměti), která začíná adresou bloku souvislých objektů, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="0c298-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="0c298-112">pro Pole celých čísel, z nichž každá je velikost bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="0c298-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="0c298-113">Pro každý blok, na který je odkazováno v polích `oldObjectIDRangeStart` a `newObjectIDRangeStart`, je zadána velikost.</span><span class="sxs-lookup"><span data-stu-id="0c298-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c298-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c298-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c298-115">Tato metoda oznamuje velikosti objektů `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64-bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="0c298-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="0c298-116">Chcete-li získat velikost objektů, které jsou větší než 4 GB, použijte místo toho metodu [ICorProfilerCallback4:: MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0c298-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="0c298-117">Komprimace systému uvolňování paměti uvolní paměť, která je obsazená mrtvými objekty, a zkomprimuje uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="0c298-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="0c298-118">V důsledku toho mohou být živé objekty přesunuty v rámci haldy a `ObjectID` hodnoty distribuované předchozími oznámeními se mohou změnit.</span><span class="sxs-lookup"><span data-stu-id="0c298-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="0c298-119">Předpokládejme, že existující hodnota `ObjectID` (`oldObjectID`) leží v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="0c298-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="0c298-120">V tomto případě je posunutí od začátku rozsahu na začátek objektu následující:</span><span class="sxs-lookup"><span data-stu-id="0c298-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="0c298-121">Pro libovolnou hodnotu `i`, která je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="0c298-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="0c298-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="0c298-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="0c298-123">novou `ObjectID` můžete vypočítat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0c298-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="0c298-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="0c298-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="0c298-125">Žádná z hodnot `ObjectID` předaných `MovedReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých umístění do nových umístění.</span><span class="sxs-lookup"><span data-stu-id="0c298-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="0c298-126">Proto by se profilery neměly pokoušet prozkoumat objekty během volání `MovedReferences`.</span><span class="sxs-lookup"><span data-stu-id="0c298-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="0c298-127">Zpětné volání [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) označuje, že všechny objekty byly přesunuty do jejich nových umístění a lze provést kontrolu.</span><span class="sxs-lookup"><span data-stu-id="0c298-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c298-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c298-128">Requirements</span></span>  
 <span data-ttu-id="0c298-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c298-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c298-130">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0c298-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c298-131">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c298-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c298-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c298-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c298-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c298-133">See also</span></span>

- [<span data-ttu-id="0c298-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c298-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0c298-135">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0c298-135">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="0c298-136">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0c298-136">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0c298-137">Profilace</span><span class="sxs-lookup"><span data-stu-id="0c298-137">Profiling</span></span>](index.md)
