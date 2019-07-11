---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbc66ef1eb5048d2c708a615a99ea363d29540f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752171"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="6bcfe-102">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="6bcfe-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="6bcfe-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="6bcfe-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6bcfe-104">Poskytuje příznaky kromě v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který lze vybrat profiler [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bcfe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bcfe-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6bcfe-106">Členové</span><span class="sxs-lookup"><span data-stu-id="6bcfe-106">Members</span></span>  
  
|<span data-ttu-id="6bcfe-107">Člen</span><span class="sxs-lookup"><span data-stu-id="6bcfe-107">Member</span></span>|<span data-ttu-id="6bcfe-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6bcfe-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="6bcfe-109">Jsou nastaveny žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="6bcfe-110">Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="6bcfe-111">Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětného volání pro aktualizace do datového proudu symbol přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="6bcfe-112">Ovládací prvky [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro určující, kdy byl dynamickou metodu uvolňování paměti shromažďují a byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="6bcfe-113">.NET core 3.0 a novějších verzích pouze: Zakáže [vrstvené kompilace](../../../core/whats-new/dotnet-core-3-0.md) pro profilovací programy.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="6bcfe-114">.NET core 3.0 a novějších verzích pouze: Poskytuje zjednodušenou GC profilace možnost ve srovnání s [ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6bcfe-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="6bcfe-115">Řídí pouze [garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), a [getgenerationbounds –](icorprofilerinfo2-getgenerationbounds-method.md) zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="6bcfe-116">Na rozdíl od `COR_PRF_MONITOR_GC` příznak `COR_PRF_HIGH_BASIC_GC` není zakázat souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="6bcfe-117">.NET core 3.0 a novějších verzích pouze: Umožňuje [movedreferences –](icorprofilercallback-movedreferences-method.md) a [movedreferences2 –](icorprofilercallback4-movedreferences2-method.md) zpětná volání pro pouze komprimaci GC.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="6bcfe-118">.NET core 3.0 a novějších verzích pouze: Podobně jako [ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md), ale poskytuje informace o přidělení objektů pro velký objekt haldy (loh) modulem GC pouze.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the Large Object Heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="6bcfe-119">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují profil vylepšené bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="6bcfe-120">Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="6bcfe-121">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které je možné nastavit poté, co je profiler připojen ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="6bcfe-122">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="6bcfe-123">Změnit některý z těchto příznaky jinde vede `HRESULT` hodnotu, která indikuje selhání.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bcfe-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bcfe-124">Remarks</span></span>  
 <span data-ttu-id="6bcfe-125">`COR_PRF_HIGH_MONITOR` Příznaky se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="6bcfe-126">Od verze rozhraní .NET Framework 4.6.1, hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změněn od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="6bcfe-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="6bcfe-127">Počínaje rozhraním .NET Framework 4.7.2, její hodnota změněna z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` k `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="6bcfe-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="6bcfe-129">Změnit některý z těchto příznaky jinde výsledkem nezdařené `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bcfe-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bcfe-130">Requirements</span></span>  
 <span data-ttu-id="6bcfe-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bcfe-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcfe-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6bcfe-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6bcfe-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bcfe-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bcfe-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcfe-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcfe-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bcfe-135">See also</span></span>

- [<span data-ttu-id="6bcfe-136">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6bcfe-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="6bcfe-137">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="6bcfe-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="6bcfe-138">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bcfe-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
