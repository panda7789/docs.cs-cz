---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: fc0251624738a06d1be7081ebd099e97f7278a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283141"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="89c7f-102">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="89c7f-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="89c7f-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="89c7f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="89c7f-104">Poskytuje příznaky kromě těch, které se nacházejí v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu, které může Profiler zadat do metody [ICorProfilerInfo5:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) při načítání.</span><span class="sxs-lookup"><span data-stu-id="89c7f-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c7f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89c7f-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="89c7f-106">Členové</span><span class="sxs-lookup"><span data-stu-id="89c7f-106">Members</span></span>  
  
|<span data-ttu-id="89c7f-107">Člen</span><span class="sxs-lookup"><span data-stu-id="89c7f-107">Member</span></span>|<span data-ttu-id="89c7f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="89c7f-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="89c7f-109">Nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="89c7f-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="89c7f-110">Řídí zpětné volání [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) pro přidání odkazů na sestavení během procházení zavření odkazu sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="89c7f-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="89c7f-111">Řídí zpětné volání [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) pro aktualizace datového proudu symbolů přidruženého k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="89c7f-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="89c7f-112">Řídí zpětné volání [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pro indikaci, kdy byla dynamická metoda uvolněna z paměti a uvolněna.</span><span class="sxs-lookup"><span data-stu-id="89c7f-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="89c7f-113">Pouze .NET Core 3,0 a novější verze: zakáže [vrstvenou kompilaci](../../../core/whats-new/dotnet-core-3-0.md) pro profilery.</span><span class="sxs-lookup"><span data-stu-id="89c7f-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="89c7f-114">Pouze .NET Core 3,0 a novější verze: poskytuje v porovnání s [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)zjednodušenou možnost profilace GC.</span><span class="sxs-lookup"><span data-stu-id="89c7f-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="89c7f-115">Řídí pouze zpětná volání [GarbageCollectionStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)a [GetGenerationBounds –](icorprofilerinfo2-getgenerationbounds-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89c7f-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="89c7f-116">Na rozdíl od příznaku `COR_PRF_MONITOR_GC` `COR_PRF_HIGH_BASIC_GC` nezakáže souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="89c7f-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="89c7f-117">Pouze .NET Core 3,0 a novější verze: povolí zpětná volání [MovedReferences –](icorprofilercallback-movedreferences-method.md) a [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) pouze pro komprimaci GC.</span><span class="sxs-lookup"><span data-stu-id="89c7f-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="89c7f-118">Pouze .NET Core 3,0 a novější verze: podobně jako [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale poskytuje informace o přidělení objektů pro haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="89c7f-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="89c7f-119">Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které vyžadují image s rozšířeným profilem.</span><span class="sxs-lookup"><span data-stu-id="89c7f-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="89c7f-120">Odpovídá příznaku `COR_PRF_REQUIRE_PROFILE_IMAGE` ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="89c7f-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="89c7f-121">Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které lze nastavit po připojení profileru ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89c7f-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="89c7f-122">Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="89c7f-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="89c7f-123">Když se pokusíte změnit některý z těchto příznaků jinde, výsledkem je `HRESULT` hodnota, která označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="89c7f-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89c7f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89c7f-124">Remarks</span></span>

<span data-ttu-id="89c7f-125">Příznaky `COR_PRF_HIGH_MONITOR` se používají s parametrem `pdwEventsHigh` metod [ICorProfilerInfo5:: GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) a [ICorProfilerInfo5:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89c7f-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="89c7f-126">Počínaje .NET Framework 4.6.1 se hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnila z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="89c7f-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="89c7f-127">Počínaje .NET Framework 4.7.2 se jeho hodnota změnila z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="89c7f-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="89c7f-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být Bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="89c7f-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="89c7f-129">Když se pokusíte změnit některý z těchto příznaků jinde, dojde k selhání `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="89c7f-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="89c7f-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89c7f-130">Requirements</span></span>

<span data-ttu-id="89c7f-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c7f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="89c7f-132">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="89c7f-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="89c7f-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89c7f-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="89c7f-134">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c7f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c7f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89c7f-135">See also</span></span>

- [<span data-ttu-id="89c7f-136">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="89c7f-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="89c7f-137">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="89c7f-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="89c7f-138">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89c7f-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
