---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175210"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="980b6-102">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="980b6-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="980b6-103">[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="980b6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="980b6-104">Poskytuje příznaky kromě těch, které se nacházejí ve výčtu [COR_PRF_MONITOR,](cor-prf-monitor-enumeration.md) který profiler může zadat metodu [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) při načítání.</span><span class="sxs-lookup"><span data-stu-id="980b6-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="980b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="980b6-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="980b6-106">Členové</span><span class="sxs-lookup"><span data-stu-id="980b6-106">Members</span></span>  
  
|<span data-ttu-id="980b6-107">Člen</span><span class="sxs-lookup"><span data-stu-id="980b6-107">Member</span></span>|<span data-ttu-id="980b6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="980b6-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="980b6-109">Nejsou nastaveny žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="980b6-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="980b6-110">Řídí zpětné volání [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) pro přidání odkazů na sestavení během chůze uzavření odkazu sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="980b6-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="980b6-111">Řídí [ICorProfilerCallback7::ModuleInMemorySymbolsAktualizováno](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace datového proudu symbolů přidruženého k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="980b6-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="980b6-112">Řídí [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro označení, kdy dynamická metoda byla uvolněna a uvolněna.</span><span class="sxs-lookup"><span data-stu-id="980b6-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="980b6-113">Pouze verze .NET Core 3.0 a novější verze: Zakáže [vrstvenou kompilaci](../../../core/whats-new/dotnet-core-3-0.md) pro profilovací programy.</span><span class="sxs-lookup"><span data-stu-id="980b6-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="980b6-114">Pouze verze .NET Core 3.0 a novější verze: Poskytuje [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)možnost profilování zjednodušeného globálního katalogu ve srovnání s .</span><span class="sxs-lookup"><span data-stu-id="980b6-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="980b6-115">Řídí pouze [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)a [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="980b6-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="980b6-116">Na `COR_PRF_MONITOR_GC` rozdíl `COR_PRF_HIGH_BASIC_GC` od příznaku nezakáže souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="980b6-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="980b6-117">Pouze verze .NET Core 3.0 a novější verze: Povolí zpětná volání [MovedReferences](icorprofilercallback-movedreferences-method.md) a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pouze pro komprimaci gů.</span><span class="sxs-lookup"><span data-stu-id="980b6-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="980b6-118">Pouze verze .NET Core 3.0 a [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)novější verze: Podobné aplikace , ale poskytuje informace pouze o přidělení objektů pro haldu velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="980b6-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="980b6-119">Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které vyžadují obrázky s rozšířeným profilem.</span><span class="sxs-lookup"><span data-stu-id="980b6-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="980b6-120">Odpovídá příznaku `COR_PRF_REQUIRE_PROFILE_IMAGE` ve [výčtu COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="980b6-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="980b6-121">Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které lze nastavit po profiler je připojen ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="980b6-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="980b6-122">Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="980b6-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="980b6-123">Pokuso o změnu některého `HRESULT` z těchto příznaků jinde má za následek hodnotu, která označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="980b6-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="980b6-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="980b6-124">Remarks</span></span>

<span data-ttu-id="980b6-125">Příznaky `COR_PRF_HIGH_MONITOR` se používají `pdwEventsHigh` s parametrem metod [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) a [ICorProfilerInfo5::SetEventMask2.](icorprofilerinfo5-seteventmask2-method.md)</span><span class="sxs-lookup"><span data-stu-id="980b6-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="980b6-126">Počínaje rozhraním .NET Framework 4.6.1, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` hodnota změněna z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x0000002).</span><span class="sxs-lookup"><span data-stu-id="980b6-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="980b6-127">Počínaje rozhraním .NET Framework 4.7.2 `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` se `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`jeho hodnota změnila z na .</span><span class="sxs-lookup"><span data-stu-id="980b6-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="980b6-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`je určena jako bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="980b6-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="980b6-129">Pokus o změnu některého z `HRESULT`těchto příznaků jinde má za následek selhání .</span><span class="sxs-lookup"><span data-stu-id="980b6-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="980b6-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="980b6-130">Requirements</span></span>

<span data-ttu-id="980b6-131">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="980b6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="980b6-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="980b6-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="980b6-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="980b6-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="980b6-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="980b6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980b6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="980b6-135">See also</span></span>

- [<span data-ttu-id="980b6-136">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="980b6-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="980b6-137">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="980b6-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="980b6-138">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="980b6-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
