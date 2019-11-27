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
# <a name="cor_prf_high_monitor-enumeration"></a>Výčet COR_PRF_HIGH_MONITOR

[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
Poskytuje příznaky kromě těch, které se nacházejí v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu, které může Profiler zadat do metody [ICorProfilerInfo5:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) při načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Members  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nejsou nastavené žádné příznaky.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Řídí zpětné volání [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) pro přidání odkazů na sestavení během procházení zavření odkazu sestavení CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Řídí zpětné volání [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) pro aktualizace datového proudu symbolů přidruženého k modulu v paměti.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Řídí zpětné volání [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pro indikaci, kdy byla dynamická metoda uvolněna z paměti a uvolněna. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|Pouze .NET Core 3,0 a novější verze: zakáže [vrstvenou kompilaci](../../../core/whats-new/dotnet-core-3-0.md) pro profilery.|
|`COR_PRF_HIGH_BASIC_GC`|Pouze .NET Core 3,0 a novější verze: poskytuje v porovnání s [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)zjednodušenou možnost profilace GC. Řídí pouze zpětná volání [GarbageCollectionStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)a [GetGenerationBounds –](icorprofilerinfo2-getgenerationbounds-method.md) . Na rozdíl od příznaku `COR_PRF_MONITOR_GC` `COR_PRF_HIGH_BASIC_GC` nezakáže souběžné uvolňování paměti.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Pouze .NET Core 3,0 a novější verze: povolí zpětná volání [MovedReferences –](icorprofilercallback-movedreferences-method.md) a [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) pouze pro komprimaci GC.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Pouze .NET Core 3,0 a novější verze: podobně jako [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale poskytuje informace o přidělení objektů pro haldu velkých objektů (LOH).|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které vyžadují image s rozšířeným profilem. Odpovídá příznaku `COR_PRF_REQUIRE_PROFILE_IMAGE` ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které lze nastavit po připojení profileru ke spuštěné aplikaci.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Představuje všechny příznaky `COR_PRF_HIGH_MONITOR`, které lze nastavit pouze během inicializace. Když se pokusíte změnit některý z těchto příznaků jinde, výsledkem je `HRESULT` hodnota, která označuje selhání.|  
  
## <a name="remarks"></a>Poznámky

Příznaky `COR_PRF_HIGH_MONITOR` se používají s parametrem `pdwEventsHigh` metod [ICorProfilerInfo5:: GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) a [ICorProfilerInfo5:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .  
  
Počínaje .NET Framework 4.6.1 se hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnila z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Počínaje .NET Framework 4.7.2 se jeho hodnota změnila z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být Bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace. Když se pokusíte změnit některý z těchto příznaků jinde, dojde k selhání `HRESULT`.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
**Hlavička:** CorProf. idl, CorProf. h  
  
**Knihovna:** CorGuids. lib  
  
**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
