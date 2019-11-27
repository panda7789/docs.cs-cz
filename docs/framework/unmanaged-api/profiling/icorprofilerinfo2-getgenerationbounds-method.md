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
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433124"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="6be87-102">ICorProfilerInfo2::GetGenerationBounds – metoda</span><span class="sxs-lookup"><span data-stu-id="6be87-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="6be87-103">Získá oblasti paměti, které jsou segmenty haldy, které tvoří různé generace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be87-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6be87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6be87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6be87-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="6be87-106">pro Počet prvků přidělených volajícím pro pole `ranges`.</span><span class="sxs-lookup"><span data-stu-id="6be87-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="6be87-107">mimo Ukazatel na celé číslo, které určuje celkový počet rozsahů, některé nebo všechny, které budou vráceny v poli `ranges`.</span><span class="sxs-lookup"><span data-stu-id="6be87-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="6be87-108">mimo Pole struktur [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) , z nichž každý popisuje rozsah (tj. blok) paměti v rámci generace, která je podchází uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be87-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6be87-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6be87-109">Remarks</span></span>  
 <span data-ttu-id="6be87-110">Metodu `GetGenerationBounds` lze volat z jakéhokoli zpětného volání profileru za předpokladu, že uvolňování paměti neprobíhá.</span><span class="sxs-lookup"><span data-stu-id="6be87-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="6be87-111">Při uvolňování paměti dojde k většině posunutí generací.</span><span class="sxs-lookup"><span data-stu-id="6be87-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="6be87-112">Generace se můžou zvětšovat mezi kolekcemi, ale obecně se nepřesouvá.</span><span class="sxs-lookup"><span data-stu-id="6be87-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="6be87-113">Nejzajímavější místa pro volání `GetGenerationBounds` jsou proto v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="6be87-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="6be87-114">Během spouštění programu jsou některé objekty přiděleny samotným modulem CLR (Common Language Runtime), obecně v generacích 3 a 0.</span><span class="sxs-lookup"><span data-stu-id="6be87-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="6be87-115">Proto se v době spuštění spravovaného kódu bude tato generace již obsahovat.</span><span class="sxs-lookup"><span data-stu-id="6be87-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="6be87-116">Generace 1 a 2 budou normálně prázdné, s výjimkou fiktivních objektů, které jsou generovány systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be87-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="6be87-117">(Velikost fiktivních objektů je 12 bajtů v 32 bitových implementacích CLR; velikost je větší v 64 implementacích.) Můžete se také podívat na rozsahy generace 2, které jsou uvnitř modulů generovaných generátorem nativních imagí (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="6be87-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="6be87-118">V tomto případě jsou objekty v generaci 2 *zmrazeny objekty*, které jsou přiděleny při spuštění nástroje Ngen. exe, nikoli systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be87-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="6be87-119">Tato funkce používá vyrovnávací paměti přidělené volajícím.</span><span class="sxs-lookup"><span data-stu-id="6be87-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be87-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6be87-120">Requirements</span></span>  
 <span data-ttu-id="6be87-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6be87-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be87-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6be87-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6be87-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6be87-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6be87-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be87-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be87-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6be87-125">See also</span></span>

- [<span data-ttu-id="6be87-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be87-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="6be87-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be87-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="6be87-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6be87-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6be87-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="6be87-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
