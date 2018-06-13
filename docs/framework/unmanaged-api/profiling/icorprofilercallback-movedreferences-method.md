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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28fa18535cce50a62f6aca7ae6f013628698c6dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455531"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="8c3ce-102">ICorProfilerCallback::MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="8c3ce-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="8c3ce-103">Volá se pro sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c3ce-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c3ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c3ce-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="8c3ce-106">[v] Počet bloků souvislý objektů, které přesunout v důsledku komprimaci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="8c3ce-107">To znamená, hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="8c3ce-108">Následující tři argumenty `MovedReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="8c3ce-109">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny jeden blok souvislý objektů, které se týkají.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="8c3ce-110">[v] Pole `ObjectID` hodnoty, z nichž každý je starý (předběžné uvolňování paměti) počáteční adresa blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="8c3ce-111">[v] Pole `ObjectID` hodnoty, z nichž každý je nové počáteční adresa (po uvolnění paměti) blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="8c3ce-112">[v] Pole celých čísel, z nichž každý je velikost bloku souvislý objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="8c3ce-113">Velikost je zadán pro každý blok, který se odkazuje v `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c3ce-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c3ce-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c3ce-115">Tato metoda sestavy velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="8c3ce-116">Velikost objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="8c3ce-117">Komprimaci uvolňování paměti získá paměť obsazená neaktivní objekty a zkomprimuje uvolní místo.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="8c3ce-118">V důsledku toho může přesunout živé objekty v rámci haldy, a `ObjectID` mohou změnit hodnoty distribuovat předchozí oznámení.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="8c3ce-119">Předpokládáme, že existující `ObjectID` hodnotu (`oldObjectID`) v rozmezí následující:</span><span class="sxs-lookup"><span data-stu-id="8c3ce-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="8c3ce-120">Posun od začátku rozsahu na začátek objekt v tomto případě je následující:</span><span class="sxs-lookup"><span data-stu-id="8c3ce-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="8c3ce-121">Pro všechny hodnotu `i` , je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="8c3ce-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="8c3ce-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="8c3ce-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="8c3ce-123">můžete vypočítat nové `ObjectID` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8c3ce-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="8c3ce-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="8c3ce-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="8c3ce-125">Žádná z `ObjectID` hodnotu předanou `MovedReferences` jsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů z původního umístění do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="8c3ce-126">Proto profilery neměli zkontrolovat objekty během `MovedReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="8c3ce-127">A [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání označuje, že všechny objekty byly přesunuty do nového umístění a provádět kontroly.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c3ce-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c3ce-128">Requirements</span></span>  
 <span data-ttu-id="8c3ce-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3ce-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3ce-130">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c3ce-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c3ce-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c3ce-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c3ce-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3ce-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3ce-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c3ce-133">See Also</span></span>  
 [<span data-ttu-id="8c3ce-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c3ce-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8c3ce-135">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="8c3ce-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [<span data-ttu-id="8c3ce-136">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8c3ce-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8c3ce-137">Profilace</span><span class="sxs-lookup"><span data-stu-id="8c3ce-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
