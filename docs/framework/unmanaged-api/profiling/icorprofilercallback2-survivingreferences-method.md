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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0ed1dc09e8dcee8a4c67e01279c6e13661e252d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459824"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="a0e6e-102">ICorProfilerCallback2::SurvivingReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="a0e6e-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="a0e6e-103">Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e6e-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0e6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0e6e-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="a0e6e-106">[v] Počet bloků souvislý objektů, které zůstal naživu v důsledku uvolnění paměti kompresi.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="a0e6e-107">To znamená, hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` maticových, které úložiště `ObjectID` a délky, v uvedeném pořadí, pro každý blok objektů.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="a0e6e-108">Následující dva argumenty `SurvivingReferences` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="a0e6e-109">Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` na stejný blok souvislý objektů, které se týkají.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="a0e6e-110">[v] Pole `ObjectID` hodnoty, z nichž každý je adresa počáteční blok souvislý, live objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="a0e6e-111">[v] Pole celých čísel, z nichž každý je velikost bloku hostujícího souvislý objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="a0e6e-112">Velikost je zadán pro každý blok, který se odkazuje v `objectIDRangeStart` pole.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0e6e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0e6e-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0e6e-114">Tato metoda sestavy velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="a0e6e-115">Pro objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::survivingreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="a0e6e-116">Elementy `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován následujícím způsobem určit, zda objekt zůstal naživu uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="a0e6e-117">Předpokládáme, že `ObjectID` hodnotu (`ObjectID`) v rozmezí následující:</span><span class="sxs-lookup"><span data-stu-id="a0e6e-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="a0e6e-118">Pro všechny hodnotu `i` , je v následujícím rozsahu, objekt má zůstal naživu uvolnění paměti:</span><span class="sxs-lookup"><span data-stu-id="a0e6e-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="a0e6e-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="a0e6e-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="a0e6e-120">Uvolnění paměti kompresi získá paměť obsazená "neaktivní" objekty, ale není compact toto uvolněné místo.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="a0e6e-121">V důsledku toho se vrátí halda paměti, ale žádné "živé" objekty přesunou.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="a0e6e-122">Modul CLR (CLR) volá `SurvivingReferences` pro kompresi jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="a0e6e-123">Pro komprimaci kolekce [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) nazývá místo.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="a0e6e-124">Uvolňování paměti jednom může být komprimaci pro jedna generace a bez kompresi pro jinou.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="a0e6e-125">Pro kolekci paměti na žádné konkrétní generování profileru obdrží, buď `SurvivingReferences` zpětného volání nebo `MovedReferences` zpětného volání, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="a0e6e-126">Více `SurvivingReferences` zpětná volání může být přijata během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více vláken, vytváření sestav v případě uvolňování paměti serveru a z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="a0e6e-127">V případě více zpětných volání během uvolňování paměti, je kumulativní informace – všechny odkazy, které jsou hlášeny v žádném `SurvivingReferences` zpětného volání, zůstanou platné i po uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0e6e-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e6e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0e6e-128">Requirements</span></span>  
 <span data-ttu-id="a0e6e-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e6e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e6e-130">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0e6e-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0e6e-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e6e-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e6e-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e6e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e6e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0e6e-133">See Also</span></span>  
 [<span data-ttu-id="a0e6e-134">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0e6e-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a0e6e-135">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0e6e-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="a0e6e-136">SurvivingReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a0e6e-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
