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
ms.openlocfilehash: 4611b8c186e0293dae73cee4f9d845bb44c167c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904706"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="9f2af-102">ICorProfilerCallback::MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="9f2af-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="9f2af-103">Volá se, aby sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9f2af-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f2af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f2af-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f2af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f2af-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="9f2af-106">[in] Počet bloků souvislých objektů, které přesunout v důsledku komprimaci kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9f2af-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="9f2af-107">To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.</span><span class="sxs-lookup"><span data-stu-id="9f2af-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="9f2af-108">Následující tři argumenty `MovedReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="9f2af-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="9f2af-109">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny týkají jeden blok souvislé objektů.</span><span class="sxs-lookup"><span data-stu-id="9f2af-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="9f2af-110">[in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé původní (předběžné uvolňování), živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="9f2af-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="9f2af-111">[in] Pole `ObjectID` hodnot, z nichž každý je novou počáteční adresu (po uvolňování) blok souvislé, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="9f2af-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="9f2af-112">[in] Pole celých čísel, z nichž každý je velikost bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="9f2af-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="9f2af-113">Zadat velikost pro každý blok, na který odkazuje `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="9f2af-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f2af-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f2af-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f2af-115">Tato metoda oznamuje velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="9f2af-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="9f2af-116">Chcete-li získat velikost objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="9f2af-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="9f2af-117">Komprimace systému uvolňování paměti získá paměť obsazené nepoužívanými objekty a zkomprimuje uvolní místo.</span><span class="sxs-lookup"><span data-stu-id="9f2af-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="9f2af-118">V důsledku toho mohou být přesunuty živé objekty v rámci haldy, a `ObjectID` může změnit hodnoty distribuuje společnost předchozí oznámení.</span><span class="sxs-lookup"><span data-stu-id="9f2af-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="9f2af-119">Předpokládejme, že existující `ObjectID` hodnotu (`oldObjectID`) najdete v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="9f2af-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="9f2af-120">Posun od začátku rozsahu na začátek objekt v tomto případě je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f2af-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="9f2af-121">Jakoukoli hodnotu z `i` , který je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="9f2af-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="9f2af-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="9f2af-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="9f2af-123">můžete vypočítat nové `ObjectID` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f2af-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="9f2af-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="9f2af-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="9f2af-125">Žádná z `ObjectID` hodnotu předanou `MovedReferences` jsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré umístění do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="9f2af-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="9f2af-126">Proto by se neměly pokoušet profilery pro kontrolu objektů během `MovedReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="9f2af-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="9f2af-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání znamená, že se přesunuly všechny objekty do jejich nových umístění a provést kontrolu.</span><span class="sxs-lookup"><span data-stu-id="9f2af-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f2af-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f2af-128">Requirements</span></span>  
 <span data-ttu-id="9f2af-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f2af-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f2af-130">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f2af-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f2af-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f2af-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f2af-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f2af-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2af-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f2af-133">See also</span></span>

- [<span data-ttu-id="9f2af-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f2af-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9f2af-135">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9f2af-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="9f2af-136">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9f2af-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9f2af-137">Profilace</span><span class="sxs-lookup"><span data-stu-id="9f2af-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
