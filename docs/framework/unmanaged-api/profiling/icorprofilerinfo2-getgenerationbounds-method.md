---
title: "ICorProfilerInfo2::GetGenerationBounds – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetGenerationBounds
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c84be5d7e78c348c0368e9639a470a8fc60e2ca7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="055b5-102">ICorProfilerInfo2::GetGenerationBounds – metoda</span><span class="sxs-lookup"><span data-stu-id="055b5-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="055b5-103">Získá oblasti paměti, které jsou segmenty haldě, které tvoří různé kolekce generace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="055b5-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="055b5-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="055b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="055b5-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="055b5-106">[v] Počet elementů přidělené pro volající funkcí `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="055b5-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="055b5-107">[out] Ukazatel na celé číslo, který určuje celkový počet rozsahů, některé nebo všechny z nich, vrátí se `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="055b5-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="055b5-108">[out] Pole [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z nichž každý popisuje rozsah (blok) paměti v generaci, kterou právě probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="055b5-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="055b5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="055b5-109">Remarks</span></span>  
 <span data-ttu-id="055b5-110">`GetGenerationBounds` Metodu lze volat z jakékoli profileru zpětné volání, za předpokladu, že není v průběhu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="055b5-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="055b5-111">To znamená, může být volána z jakékoli zpětného volání kromě těch, které se vyskytnou mezi [icorprofilercallback2::garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="055b5-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="055b5-112">Většina s posunem generací probíhá během kolekce.</span><span class="sxs-lookup"><span data-stu-id="055b5-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="055b5-113">Generace může růst mezi kolekcí, ale obecně není pohyb.</span><span class="sxs-lookup"><span data-stu-id="055b5-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="055b5-114">Proto nejvíce zajímavé místech volat `GetGenerationBounds` v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="055b5-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="055b5-115">Při spuštění programu některé objekty mají při přidělování modulem common language runtime (CLR) samostatně, obvykle v generace 3 a 0.</span><span class="sxs-lookup"><span data-stu-id="055b5-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="055b5-116">Proto podle času spravovaný kód spustí provádění, tyto generace již obsahuje objekty.</span><span class="sxs-lookup"><span data-stu-id="055b5-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="055b5-117">Generace 1 a 2 obvykle bude prázdný, s výjimkou fiktivní objekty, které jsou generovány modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="055b5-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="055b5-118">(Velikost fiktivní objektů je 12 bajtů v implementacích 32bitová verze modulu CLR, větší v implementacích 64-bit.) Můžete si také prohlédnout generace 2 rozsahy, které jsou uvnitř modulů vyprodukované generátor (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="055b5-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="055b5-119">V tomto případě jsou objekty v generace 2 *pozastaveny objekty*, které jsou přiděleny při spuštění NGen.exe spíše než modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="055b5-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="055b5-120">Tato funkce využívá volající přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055b5-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055b5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="055b5-121">Requirements</span></span>  
 <span data-ttu-id="055b5-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="055b5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="055b5-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="055b5-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="055b5-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="055b5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="055b5-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="055b5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055b5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="055b5-126">See Also</span></span>  
 [<span data-ttu-id="055b5-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="055b5-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="055b5-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="055b5-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="055b5-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="055b5-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="055b5-130">Profilace</span><span class="sxs-lookup"><span data-stu-id="055b5-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
