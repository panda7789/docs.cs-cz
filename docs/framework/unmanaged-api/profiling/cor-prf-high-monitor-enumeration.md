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
# <a name="cor_prf_high_monitor-enumeration"></a>Výčet COR_PRF_HIGH_MONITOR

[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
Poskytuje příznaky kromě těch, které se nacházejí ve výčtu [COR_PRF_MONITOR,](cor-prf-monitor-enumeration.md) který profiler může zadat metodu [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) při načítání.  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nejsou nastaveny žádné příznaky.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Řídí zpětné volání [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) pro přidání odkazů na sestavení během chůze uzavření odkazu sestavení CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Řídí [ICorProfilerCallback7::ModuleInMemorySymbolsAktualizováno](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace datového proudu symbolů přidruženého k modulu v paměti.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Řídí [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro označení, kdy dynamická metoda byla uvolněna a uvolněna. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|Pouze verze .NET Core 3.0 a novější verze: Zakáže [vrstvenou kompilaci](../../../core/whats-new/dotnet-core-3-0.md) pro profilovací programy.|
|`COR_PRF_HIGH_BASIC_GC`|Pouze verze .NET Core 3.0 a novější verze: Poskytuje [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)možnost profilování zjednodušeného globálního katalogu ve srovnání s . Řídí pouze [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)a [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) zpětná volání. Na `COR_PRF_MONITOR_GC` rozdíl `COR_PRF_HIGH_BASIC_GC` od příznaku nezakáže souběžné uvolňování paměti.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Pouze verze .NET Core 3.0 a novější verze: Povolí zpětná volání [MovedReferences](icorprofilercallback-movedreferences-method.md) a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pouze pro komprimaci gů.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Pouze verze .NET Core 3.0 a [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)novější verze: Podobné aplikace , ale poskytuje informace pouze o přidělení objektů pro haldu velkého objektu (LOH).|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které vyžadují obrázky s rozšířeným profilem. Odpovídá příznaku `COR_PRF_REQUIRE_PROFILE_IMAGE` ve [výčtu COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které lze nastavit po profiler je připojen ke spuštěné aplikaci.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Představuje `COR_PRF_HIGH_MONITOR` všechny příznaky, které lze nastavit pouze během inicializace. Pokuso o změnu některého `HRESULT` z těchto příznaků jinde má za následek hodnotu, která označuje selhání.|  
  
## <a name="remarks"></a>Poznámky

Příznaky `COR_PRF_HIGH_MONITOR` se používají `pdwEventsHigh` s parametrem metod [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) a [ICorProfilerInfo5::SetEventMask2.](icorprofilerinfo5-seteventmask2-method.md)  
  
Počínaje rozhraním .NET Framework 4.6.1, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` hodnota změněna z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x0000002). Počínaje rozhraním .NET Framework 4.7.2 `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` se `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`jeho hodnota změnila z na .

`COR_PRF_HIGH_MONITOR_IMMUTABLE`je určena jako bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace. Pokus o změnu některého z `HRESULT`těchto příznaků jinde má za následek selhání .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
**Záhlaví:** CorProf.idl, CorProf.h  
  
**Knihovna:** CorGuids.lib  
  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro profilaci](profiling-enumerations.md)
- [COR_PRF_MONITOR – výčet](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 – rozhraní](icorprofilerinfo5-interface.md)
