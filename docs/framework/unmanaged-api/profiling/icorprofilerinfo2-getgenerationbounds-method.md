---
title: ICorProfilerInfo2::GetGenerationBounds – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110375"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="40233-102">ICorProfilerInfo2::GetGenerationBounds – metoda</span><span class="sxs-lookup"><span data-stu-id="40233-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="40233-103">Získá oblastí paměti, které jsou segmenty haldy, které společně tvoří různých generací kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="40233-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40233-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40233-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40233-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40233-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="40233-106">[in] Počet prvků přidělenou volajícím pro `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="40233-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="40233-107">[out] Ukazatel na celé číslo, který určuje celkový počet rozsahů, některé nebo všechny z nich, vrátí `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="40233-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="40233-108">[out] Pole [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z nichž každý popisuje rozsah (bloku) paměti v rámci ke generaci, kterou provádí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40233-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40233-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40233-109">Remarks</span></span>  
 <span data-ttu-id="40233-110">`GetGenerationBounds` Metodu lze volat z jakékoli zpětného volání profileru, za předpokladu, že uvolňování paměti není v průběhu.</span><span class="sxs-lookup"><span data-stu-id="40233-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="40233-111">To znamená, může být volána z jakékoli zpětného volání s výjimkou těch, ke kterým dochází mezi [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="40233-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="40233-112">Většina posunutí generací probíhá během uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="40233-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="40233-113">Generace rozrůstat mezi kolekcí, ale obecně není pohyb.</span><span class="sxs-lookup"><span data-stu-id="40233-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="40233-114">Proto zajímá nejvíce místa, kde volání `GetGenerationBounds` v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="40233-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="40233-115">Při spuštění programu některé objekty se přidělují modulem common language runtime (CLR), obvykle v generacích 3 a 0.</span><span class="sxs-lookup"><span data-stu-id="40233-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="40233-116">Proto době spravovaný kód začne provádět tyto generace již obsahuje objekty.</span><span class="sxs-lookup"><span data-stu-id="40233-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="40233-117">Obvykle bude prázdný, s výjimkou fiktivní objekty, které jsou generovány pomocí systému uvolňování paměti generace 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="40233-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="40233-118">(Velikost fiktivní objektů je 12 bajtů v implementacích 32bitová verze modulu CLR, velikost je větší v implementacích 64bitová verze) Můžete si také prohlédnout rozsahy 2. generace, které jsou uvnitř modulů vytvářených Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="40233-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="40233-119">V takovém případě objekty v 2. generace jsou *zmrazené objekty*, které jsou přiděleny po spuštění NGen.exe, nikoli podle systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40233-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="40233-120">Tato funkce využívá volající – přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="40233-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40233-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40233-121">Requirements</span></span>  
 <span data-ttu-id="40233-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40233-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40233-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40233-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40233-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40233-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40233-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40233-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40233-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40233-126">See also</span></span>

- [<span data-ttu-id="40233-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40233-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="40233-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40233-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="40233-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="40233-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="40233-130">Profilace</span><span class="sxs-lookup"><span data-stu-id="40233-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
