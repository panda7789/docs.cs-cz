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
ms.openlocfilehash: c037f2509aaa0a5e4c3f7a844614742b6f21bec3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769134"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="996a3-102">ICorProfilerCallback::MovedReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="996a3-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="996a3-103">Volá se, aby sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="996a3-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="996a3-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="996a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996a3-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="996a3-106">[in] Počet bloků souvislých objektů, které přesunout v důsledku komprimaci kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="996a3-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="996a3-107">To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.</span><span class="sxs-lookup"><span data-stu-id="996a3-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="996a3-108">Následující tři argumenty `MovedReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="996a3-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="996a3-109">Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny týkají jeden blok souvislé objektů.</span><span class="sxs-lookup"><span data-stu-id="996a3-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="996a3-110">[in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé původní (předběžné uvolňování), živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="996a3-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="996a3-111">[in] Pole `ObjectID` hodnot, z nichž každý je novou počáteční adresu (po uvolňování) blok souvislé, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="996a3-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="996a3-112">[in] Pole celých čísel, z nichž každý je velikost bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="996a3-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="996a3-113">Zadat velikost pro každý blok, na který odkazuje `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="996a3-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996a3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="996a3-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="996a3-115">Tato metoda oznamuje velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="996a3-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="996a3-116">Chcete-li získat velikost objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="996a3-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="996a3-117">Komprimace systému uvolňování paměti získá paměť obsazené nepoužívanými objekty a zkomprimuje uvolní místo.</span><span class="sxs-lookup"><span data-stu-id="996a3-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="996a3-118">V důsledku toho mohou být přesunuty živé objekty v rámci haldy, a `ObjectID` může změnit hodnoty distribuuje společnost předchozí oznámení.</span><span class="sxs-lookup"><span data-stu-id="996a3-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="996a3-119">Předpokládejme, že existující `ObjectID` hodnotu (`oldObjectID`) najdete v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="996a3-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="996a3-120">Posun od začátku rozsahu na začátek objekt v tomto případě je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="996a3-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="996a3-121">Jakoukoli hodnotu z `i` , který je v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="996a3-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="996a3-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="996a3-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="996a3-123">můžete vypočítat nové `ObjectID` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="996a3-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="996a3-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="996a3-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="996a3-125">Žádná z `ObjectID` hodnotu předanou `MovedReferences` jsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré umístění do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="996a3-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="996a3-126">Proto by se neměly pokoušet profilery pro kontrolu objektů během `MovedReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="996a3-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="996a3-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání znamená, že se přesunuly všechny objekty do jejich nových umístění a provést kontrolu.</span><span class="sxs-lookup"><span data-stu-id="996a3-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996a3-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="996a3-128">Requirements</span></span>  
 <span data-ttu-id="996a3-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996a3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996a3-130">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="996a3-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="996a3-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996a3-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996a3-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996a3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996a3-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="996a3-133">See also</span></span>

- [<span data-ttu-id="996a3-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="996a3-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="996a3-135">MovedReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="996a3-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="996a3-136">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="996a3-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="996a3-137">Profilace</span><span class="sxs-lookup"><span data-stu-id="996a3-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
