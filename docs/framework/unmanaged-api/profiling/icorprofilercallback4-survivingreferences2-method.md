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
ms.openlocfilehash: 208ce1d7ef8a1eab4f18a6d488f0cc480b5713d8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499334"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="91579-102">ICorProfilerCallback4::SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="91579-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="91579-103">Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="91579-104">Tato metoda je volána, pokud profiler implementoval rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="91579-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="91579-105">Toto zpětné volání nahrazuje metodu [ICorProfilerCallback2:: SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md) , protože může vykazovat větší rozsahy objektů, jejichž délka překračuje, co může být vyjádřeno v ulong.</span><span class="sxs-lookup"><span data-stu-id="91579-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91579-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91579-106">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="91579-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="91579-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="91579-108">pro Počet bloků souvislých objektů, které byly zachovány v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="91579-109">To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost pole `objectIDRangeStart` a `cObjectIDRangeLength` , který ukládá `ObjectID` a délku, v uvedeném pořadí pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="91579-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="91579-110">Další dva argumenty `SurvivingReferences2` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="91579-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="91579-111">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týká se stejného bloku souvislých objektů.</span><span class="sxs-lookup"><span data-stu-id="91579-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="91579-112">pro Pole `ObjectID` hodnot, z nichž každá je počáteční adresou bloku souvislých objektů, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="91579-113">pro Pole celých čísel, z nichž každá je velikost zbývajícího bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="91579-114">Velikost je určena pro každý blok, na který je odkazováno v `objectIDRangeStart` poli.</span><span class="sxs-lookup"><span data-stu-id="91579-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91579-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91579-115">Remarks</span></span>  
 <span data-ttu-id="91579-116">Prvky `objectIDRangeStart` `cObjectIDRangeLength` polí a by měly být interpretovány následujícím způsobem, aby bylo možné určit, zda objekt držel uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="91579-117">Předpokládejme, že `ObjectID` hodnota ( `ObjectID` ) leží v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="91579-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="91579-118">Pro všechny hodnoty `i` , které jsou v následujícím rozsahu, objekt předržel uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="91579-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="91579-119">0 <=`i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="91579-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="91579-120">Nekomprimace uvolňování paměti znovu uvolňuje paměť obsazenou "nemrtvými" objekty, ale nekomprimuje volné místo.</span><span class="sxs-lookup"><span data-stu-id="91579-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="91579-121">V důsledku toho se do haldy vrátí paměť, ale nebudou přesunuty žádné "živé" objekty.</span><span class="sxs-lookup"><span data-stu-id="91579-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="91579-122">Modul CLR (Common Language Runtime) volá `SurvivingReferences2` pro nekomprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="91579-123">Pro komprimaci uvolňování paměti je místo toho volána metoda [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91579-123">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="91579-124">Jedno uvolnění paměti může být zkomprimováno pro jednu generaci a nekomprimaci pro jiné.</span><span class="sxs-lookup"><span data-stu-id="91579-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="91579-125">Pro uvolňování paměti v jakékoli konkrétní generaci získá Profiler buď `SurvivingReferences2` zpětné volání, nebo [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) zpětné volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="91579-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="91579-126">`SurvivingReferences2`Během konkrétního uvolňování paměti může být přijato více zpětných volání, z důvodu omezené vnitřní vyrovnávací paměti, více zpětných volání během uvolňování paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="91579-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="91579-127">V případě více zpětných volání během uvolňování paměti jsou informace kumulativní; všechny odkazy, které jsou hlášeny v jakémkoli `SurvivingReferences2` zpětném volání, jsou v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91579-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="91579-128">Pokud profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `SurvivingReferences2` je metoda volána před metodou [ICorProfilerCallback2:: SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md) , ale pouze v případě, že se `SurvivingReferences2` vrátí úspěšně.</span><span class="sxs-lookup"><span data-stu-id="91579-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="91579-129">Profilery mohou vracet hodnotu HRESULT, která označuje selhání od `SurvivingReferences2` metody pro zamezení volání druhé metody.</span><span class="sxs-lookup"><span data-stu-id="91579-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91579-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91579-130">Requirements</span></span>  
 <span data-ttu-id="91579-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91579-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91579-132">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="91579-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91579-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="91579-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91579-134">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91579-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91579-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91579-135">See also</span></span>

- [<span data-ttu-id="91579-136">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91579-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="91579-137">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91579-137">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="91579-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91579-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
