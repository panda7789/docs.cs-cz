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
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499737"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="f1864-102">ICorProfilerCallback2::SurvivingReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="f1864-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="f1864-103">Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1864-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1864-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1864-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="f1864-106">pro Počet bloků souvislých objektů, které byly zachovány v důsledku nekomprimace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="f1864-107">To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost pole `objectIDRangeStart` a `cObjectIDRangeLength` , který ukládá `ObjectID` a délku, v uvedeném pořadí pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="f1864-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="f1864-108">Další dva argumenty `SurvivingReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="f1864-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="f1864-109">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týká se stejného bloku souvislých objektů.</span><span class="sxs-lookup"><span data-stu-id="f1864-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="f1864-110">pro Pole `ObjectID` hodnot, z nichž každá je počáteční adresou bloku souvislých objektů, živé objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="f1864-111">pro Pole celých čísel, z nichž každá je velikost zbývajícího bloku souvislých objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="f1864-112">Velikost je určena pro každý blok, na který je odkazováno v `objectIDRangeStart` poli.</span><span class="sxs-lookup"><span data-stu-id="f1864-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1864-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1864-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1864-114">Tato metoda oznamuje velikost `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64 bitů.</span><span class="sxs-lookup"><span data-stu-id="f1864-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="f1864-115">Pro objekty, které jsou větší než 4 GB, použijte místo toho metodu [ICorProfilerCallback4:: SurvivingReferences2 –](icorprofilercallback4-survivingreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1864-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="f1864-116">Prvky `objectIDRangeStart` `cObjectIDRangeLength` polí a by měly být interpretovány následujícím způsobem, aby bylo možné určit, zda objekt držel uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="f1864-117">Předpokládejme, že `ObjectID` hodnota ( `ObjectID` ) leží v následujícím rozsahu:</span><span class="sxs-lookup"><span data-stu-id="f1864-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="f1864-118">Pro všechny hodnoty `i` , které jsou v následujícím rozsahu, objekt předržel uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="f1864-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="f1864-119">0 <=`i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="f1864-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="f1864-120">Nekomprimace uvolňování paměti znovu uvolňuje paměť obsazenou "nemrtvými" objekty, ale nekomprimuje volné místo.</span><span class="sxs-lookup"><span data-stu-id="f1864-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="f1864-121">V důsledku toho se do haldy vrátí paměť, ale nebudou přesunuty žádné "živé" objekty.</span><span class="sxs-lookup"><span data-stu-id="f1864-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="f1864-122">Modul CLR (Common Language Runtime) volá `SurvivingReferences` pro nekomprimaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="f1864-123">Pro komprimaci uvolňování paměti je místo toho volána metoda [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1864-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="f1864-124">Jedno uvolnění paměti může být zkomprimováno pro jednu generaci a nekomprimaci pro jiné.</span><span class="sxs-lookup"><span data-stu-id="f1864-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="f1864-125">Pro uvolňování paměti v jakékoli konkrétní generaci získá Profiler buď `SurvivingReferences` zpětné volání `MovedReferences` , nebo zpětné volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="f1864-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="f1864-126">`SurvivingReferences`V průběhu konkrétního uvolňování paměti může být přijato více zpětných volání, z důvodu omezené vnitřní vyrovnávací paměti, více vláken hlásí v případě uvolňování paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="f1864-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="f1864-127">V případě více zpětných volání během uvolňování paměti jsou informace kumulativní – všechny odkazy, které jsou hlášeny v jakémkoli `SurvivingReferences` zpětném volání, se zachová do uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1864-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1864-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1864-128">Requirements</span></span>  
 <span data-ttu-id="f1864-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1864-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1864-130">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f1864-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1864-131">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f1864-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1864-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1864-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1864-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1864-133">See also</span></span>

- [<span data-ttu-id="f1864-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1864-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f1864-135">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1864-135">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="f1864-136">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f1864-136">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
